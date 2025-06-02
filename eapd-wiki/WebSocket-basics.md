Inherent in the design of HTTP is the fact that it is entirely event based and events can only be initiated by clients. While anyone, anywhere in the world can make a request for information, the server has no ability to send information to a client, unless they specifically request it.  While this is fine for most web applications, it makes sharing state between two or more clients very difficult.  To solve this issue WebSockets were introduced in [RFC6455](https://datatracker.ietf.org/doc/html/rfc6455) in 2011.  In 2021 [98% of worldwide internet traffic](https://caniuse.com/websockets) world wide is done on a browser that supports WebSockets.  eAPD is using websockets to allow for synchronization of data between multiple users that are working on the same APD at the same time.  In practical terms this means that if a user edits a field in an APD anyone else that has that APD open should receive that update almost immediately without having to request an update. 

There are many libraries that hide the bare implementation of webSockets and make reasoning about the code easier.  I have chosen socket.io for the first iteration because it is extremely popular (4 million weekly downloads) and well documented.  There are certainly other valid options such as [express-ws](https://www.npmjs.com/package/express-ws) that I will explore if time allows.  One key fact about socket.io to keep in mind is that not every transfer is sent over an actual webSocket.  Socket.io utilizes a variety of techniques, including web sockets, to to achieve the best results given the current circumstances.  When thinking about how socket.io works however, it can be treated as a pure webSocket, even if the implementation is not.

To begin the server must be configured to accept webSocket connections.  The first step is to install socket.io with `npm i socket.io`.  With socket.io installed all that is required is an httpServer instance.  The most basic implementation using express is available in the [socket.io documentation](https://socket.io/docs/v4/server-initialization/#With-Express).  Because webSockets are fundamentally built on the HTTP protocol, you must provide valid cors headers, fortunately socket.io can accept the exact same headers as the cors package used by express.  Once the server is capable of accepting socket requests, it must know how to handle them.  The beginning of any webSocket session is a "connection" request that comes with a socket object.  The socket object represents the actual connection to the client.  As such each separate socket is a unique object held in memory on the server.  Once a socket is connected, it must be told how to respond to various events.  Each request has an "eventname" attribute that is used for routing.  the eventName is functionally equivalent to the path portion of the URL.  Thus, an event with a name of "editAPD" would be handled different from one called "createAPD".  Some basic implementation can be found here:

```javascript

io.on("connection", socket => { 

     // use an inline function
     socket.on(event, payload => {
         // Do something with the payload 
     })

     // use a named function
     socket.on(otherEvent, someHandler)

     // use a register function to register events
     registerFooHandler(io, socket)

});
```
At this point the server is ready to accept connections and configure them to respond to various kinds of events.

To configure the client you must first install the client with npm i socket.io-client.  Once the socket client is installed initiating a socket is actually trivial 
``` javascript
socket = io(`<someURL>`);
```
is all it takes to have a socket connection.  This will trigger the "connection" process at the server and the socket will be ready to receive data.  In the eAPD react app this function needs to be called in the component that will use it, but also only create a single socket for the entire application.  To that end I have added a util file called sockets that will handle this.  Like the server, the client also must know how to respond to different types of events.  An event can be registered like this (once the socket is created)

``` javascript

  socket.on('someEvent', (data) =>{
    console.log('someEvent Happened')
    console.log(data)
    // Do real things here
  })

```
To ensure that sockets are available in a given component I believe the easiest solution is to initialize and configure the socket in the useEffect hook with an empty array of dependencies.  

Before that will make sense, there is one additional concept that is needed, Rooms.  Rooms are simply a way to identify which sockets should respond to which events.  For example, changes to the APD for Alaska are not really of interest to someone editing an APD for Florida.  To support this the server can join a socket (the actual connection to a client) to a room.  Only the server has any information about what rooms a socket is in, the web client is blissfully ignorant of any rooms, it simply receives messages for the rooms it is in.  By default each socket has a unique identifier and is a part of that room.  Once a room has been created (or before, but don't do that) messages can be sent to that room by the socket.io instance (app.io in our code) by calling `app.io.to(someRoom).emit(aMessage)`. Here is the joinHandler code from the server:

``` javascript

module.exports = (io, socket) => {
  const joinRoom = (payload) => {
    const room = payload.room
    // join this socket to the room
    socket.join(room);
    // emit a join event to the room so everyone knows
    io.to(room).emit('join', `${socket.id} has joined the ${room} room`)
  }

  // register events here
  socket.on("join", joinRoom);
}
```
In this implementation, the client will listen for join events and then request to join a specific room by emitting a "join" event and providing a payload that contains a room property.  In response the server will emit a join event indicating who has joined.

``` javascript
  
  if (!socket) {
    initiateSocket()
  }
  // configure listener
  socket.on('join', (data) =>{
    console.log('Got a join event')
    console.log(data)
  })

  // Tell the server to join the room
  socket.emit('join', {room})
```

This now represents the most basic round trip of a web socket.  The client has initiated a socket connection, the server has configured that socket, and the client has now emitted an event which has been broadcasted to the appropriate sockets.  While in this case there is a traditional request/response pattern, this is not the norm.  Events will more often be sent to the client in response to some external event, not one initiated by the client.

While webSockets can provide authorization information in the headers, I feel that is not needed in this application.  I believe that the websockets should be used to notify clients of changes and in response the client should initiate a "normal" HTTP request for the new information.  This means that someone acting maliciously could join a room that they do not belong in and receive notifications when changes were made, but the contents of those changes would remain inaccessible to them.  If at some point in the future this is unworkable, webSockets can implement security in the same manner as we currently use for "normal" http requests.
