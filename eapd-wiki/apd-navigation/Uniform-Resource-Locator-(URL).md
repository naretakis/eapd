In order to get anywhere on the web, we need to know the **location** of of the
document, or resource, we want to retrieve. This is specified by a **URL**:

```
             hostname
            ┌───┴────┐
    https://reddit.com/r/gifs
    └─┬─┘             └──┬──┘
    scheme              path
```

[Source](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier#Examples)

A URL can be broken down into the following parts:

* **scheme** - The scheme helps us to determine the **protocol** which we will
  use to make a request. In this case,
  [HTTP Secure](https://en.wikipedia.org/wiki/HTTPS). Some other schemes we
  could use here are `ftp`, `mailto`, or `news`.
* **hostname** - The name which is used to identify the
  [Host](https://en.wikipedia.org/wiki/Hostname), or **server** of the
  information we wish to retrieve. Behind the scenes, this hostname must be
  translated to an IP address.
  [DNS servers](https://en.wikipedia.org/wiki/Domain_Name_System)
  handle this process.
* **path** - This indicates to the server the **resource** we wish to retrieve.

## URL Fragments

```
                hostname                              fragment
            ┌───────┴──────┐                         ┌───┴───┐
    https://en.wikipedia.org/wiki/Fragment_identifier#Examples
    └─┬─┘                   └───────────┬───────────┘
    scheme                            path
```

Fragments allow us to jump to an `id` within a document. This is useful when
the information you want someone to view is a few pages down within a HTML
document. Try visiting the above URL in your browser.

More on **fragments**, [here](https://en.wikipedia.org/wiki/Fragment_identifier)

## URL Query String Parameters

Consider this example URL generated when performing a search via Google.

```
             hostname          query string
            ┌───┴────┐       ┌──────┴───────┐
    https://google.com/search?q=cats&tbm=isch
    └─┬─┘             └──┬──┘
    scheme              path
```

The **query string**, aka **params**, is a series of key/value pairs, which
allows the client to pass some information to the server. In many cases, this
information is usually provided by the user by submitting a form. In this
specific case, the **query string** indicates that we have performed an image
search for `cats`.

| key                  | value               |
| -------------------- | ------------------- |
| q (query)            | cats                |
| tbm (type of search) | isch (image search) |

More on **query string parameters**, [here](https://en.wikipedia.org/wiki/Query_string)
