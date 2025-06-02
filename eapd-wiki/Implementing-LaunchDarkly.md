Started implementing on September 27th. Finished initial coding by October 3rd. Because of ATO documentation, probably amounts of about 3 coding days. Once we had the correct urls to attach to we had a pretty easy time with basic implementation. It took a little bit longer to figure out how to change existing redux values using the flag not how to load all the flags into redux, which seems to be the common way it is done.

Hang ups

- didn't remember that we needed to use the federal urls to create connections
- changing existing redux values using the flags was tricky
   - achieved this by creating a flags action with an updateFlags function that dispatches FLAGS_UPDATED with the flag values
   - the Root component uses the useFlag() hook to get the value of particular hooks and then calls the updateFlags function if any of the flags have changed
- tried to get all of the flag values using useFlags(), but it returned a promise, not sure if there is a work around for that
- using LD flags in cypress
   - added a command that intercepts the LaunchDarkly urls and returns the flag in the state that the test needs
- the rest of the hang ups were around getting the LaunchDarkly environment variables in all of the places in the CI/CD process that we needed them, not a LaunchDarkly issue
- trying to figure out the best way to handle running tests without hitting LaunchDarkly flags or creating a user so we can target tests to always have the flag in a certain state
