[[Implementing LaunchDarkly]]

## Backend

eAPD uses LaunchDarkly for feature flag management. On the backend, we connect to LaunchDarkly using the [launchdarkly-node-server-sdk](https://github.com/launchdarkly/node-server-sdk), for more information refer to the [SDK](https://docs.launchdarkly.com/sdk/server-side/node-js). The interactions with LaunchDarkly on the backend are in middleware/launchDarkly.js. It creates the ldClient and provides methods for waiting for the ldClient to connect to LaunchDarkly and for retrieving a flag value. This middleware is used in the api.js server set up to ensure that the ldClient is initialized before any endpoint tries to use it.

### How to use in the backend

```javascript
// Import the LaunchDarkly middleware
const { getLaunchDarklyFlag } = require('../../middleware/launchDarkly');

// Retrieve that flag value
const validation = await getLaunchDarklyFlag(
	'validation', // the tag name of the flag
	{ key: 'anonymous', anonymous: true }, // user information or anonymous user
	false // the default value of the flag if LaunchDarkly is not responsive
);

// the validation constant now has the value of the flag and can be used like a regular constant
```

## Frontend

On the frontend, we connect to LaunchDarkly using the [launchdarkly-react-client-sdk](https://github.com/launchdarkly/react-client-sdk), for more information refer to the [SDK documentation](https://docs.launchdarkly.com/sdk/client-side/react/react-web#getting-started). The LaunchDarkly connection is initialized in the containers/Root.js file.

### How to use in a component

```javascript
import { useFlags } from 'launchdarkly-react-client-sdk';

// inside the component code
const { validation } = useFlags();

// the validation constant can now be used like any other constant
// you need to destructure the flag object, it didn't work to get a constant of all the flags
// instead it returned a promise object
```

### Redux

The react client SDK is created for use only in components. We needed to update a redux value. There are modules for adding all of the flag values to redux, but this is what we were trying to do. To work around this issue, a flag action was created with a updateFlags function that takes in the current flag values. It dispatches the values with a FLAGS_UPDATED type. If a reducer value needs to change based on a flag, add a FLAGS_UPDATED case to it and get the value from the action.

**Listen for flag change**

```javascript
// in the web/src/containers/Root.js
// update the useFlag() constant to retrieve the value for your flag

const { validation, newFlag } = useFlags();

// add that flag to the useEffect and dispatch
useEffect(() => {
	store.dispatch(updateFlags({ validation, newFlag }));
}, [validation, newFlag]);

// now the flag will be available in a reducer that is listening for FLAGS_UPDATED
```

**Using the flag in redux**

```javascript
// in your reducer add a case for FLAGS_UPDATED

const reducer = (state = initialState, action) => {
	switch (action.type) {
		...
		case FLAGS_UPDATED: { // add your FLAGS_UPDATED case to the existing reducer
			return {
				...state,
				valueToUpdate: action.flags.newFlag // set the value you want to update with the flag value
			}
		}
	}
}

// changing the flag will result in changing the value in the reducer
```

## Best Practices

- **Creating a Flag**
   - a flag only needs to do one thing
   - make flag planning part of the feature design
   - flags can be permanent or temporary
      - permanent flag for things like custom-branding or accessibility
      - temporary for use on new features until it is no longer needed
- **Naming a Flag**
   - name the flag name human-readable and descriptive
   - write useful descriptions when creating a flag, the flag name is used by the slack hook
- **Using a Flag**
   - plan for removing a flag while you are adding it
   - minimize the reach of the flag, put the flag on the smallest thing you can
   - refactor the code if necessary to use the flag in as few places as possible
   - avoid passing a flag state into a component, get the flag value inside the component to avoid react lifecycle/rendering issues
- **Cleaning Up a Flag**
   - make sure that you clean up the flag regularly when features are completed
      - maybe add a different ticket to clean up the flag once the feature is done
      - schedule regular cleanups
      - use the dashboard to see flags that aren't being used very often
   - flags have statuses: new/never requested, active, launched, inactive to help you know what's in use
      - temporary inactive flags should be archived
      - temporary launched flags might be ready to be archived
      - never requested flags might have been created on accident and can be archived
      - prefer archiving flags over deleting them

