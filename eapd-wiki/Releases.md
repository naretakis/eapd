New releases are cut and deployed at the end of each two-week sprint. During major feature development, code may be deployed before the functionality is complete, provided it:
- it does not break the existing functionality or user experience
- it does not allow users to perform actions they should not be able to perform
- it does not invalidate or corrupt existing data

General releases are based on the `main` branch, so `main` should ***always*** be in a shippable state.

For major feature development where some of the intermediary tasks can break existing functionality, corrupt data, etc., feature branches will be used and will only be merged into `main` when it's back into a shippable state. Feature branches can be limited to just the work necessary to break and repair the experience rather than an entire feature – if some pieces of the feature work can be completed with no impact to functionality or data, those pieces may be merged directly into main.

## Versioning Guidelines
We use the standard GitHub semver version schema - v1.0.0
* **Major** version releases are typically breaking changes and/or major feature releases
* **Minor** versions are the deployments at the end of each two-week sprint (or close to it)
* **Patch** are releases in between standard deployment cycles. This could also include hotfixes or security patches.