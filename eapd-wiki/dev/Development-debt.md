# Technical debt

## Frontend

- We still use Sinon for mocking and stubs in some of our tests. The goal is to eventually migrate everything to using Jest's built-in mocking functionality (e.g., `jest.fn()`), to reduce the number of dependencies.
- We've been migrating to functional components using React hooks instead of class components, but we've only been doing it as we've done other work in a component. So there are still a lot of class-based components scattered around. It's just inconsistent and would be nice if they were all one or the other.
- Some content is in YAML files for internationalization, some of it is embedded in the React components. If the app is only ever intended to be available in English, it'd probably be good to remove the YAML part entirely. Maybe a little at a time? For the most part, when new content has gone in recently we've put it in the React components rather than deal with the YAML, and that trend seems reasonable.

## Backend
