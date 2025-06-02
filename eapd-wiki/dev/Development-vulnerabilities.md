# Vulnerabilities

We are using `audit-ci` for dependency vulnerability scanning, which is
integrated into our CI pipeline. `audit-ci` is configured to fire on
"low or higher" (aka- all) vulnerabilities. To ignore certain vulnerabilities,
see `{api,web}/audit-ci.json`, and the
[`audit-ci` documentation](https://www.npmjs.com/package/audit-ci#example-config-file-and-different-directory-usage).

It is generally acceptable to add exceptions for development-only packages,
since these will only be used when building and testing the application, and
will not be used in the production environment.

[Dependabot](https://docs.github.com/en/github/managing-security-vulnerabilities/configuring-github-dependabot-security-updates)
is configured to issue pull requests to update vulnerable dependencies.

# Troubleshooting

1.  If you are not already working in a branch, create a new branch (your name)/vulnerabilities-(date)
2.	look at existing dependabot PRs <br/>
–	if there is one, try to copy the code directly into your branch <br/>
–	if there is too much pull those branches into your branch
3.	run `npm audit`
4.	if there are still vulnerabilities try `npm audit fix` 
5.	if there are still errors, look up the website for the errors to get the package that is the issue
6.  run `npm ls <package-name>` to see what top level dependency it is linked to.
7.  if it is a top level dependency, try to bump the version and see if it negatively affects anything in the system<br />
–	WARNING: THIS REQUIRES TESTING TO MAKE SURE IT DOESN’T BREAK ANYTHING
8.  if it is a sub-dependency, try added the fixed version to the "resolutions" section of package.json and see if that negatively affects anything in the system<br />
–	WARNING: THIS REQUIRES TESTING TO MAKE SURE IT DOESN’T BREAK ANYTHING
7.	if nothing else is possible, then add an exception to the `audit-ci.json` file, this will make the vulnerability scanner skip that error. If you need to add it to the `audit-ci.json` file, you need to also add a comment for the advisory you are allowing to the _comments section and what it affects. You only need to include dependencies or sub-dependencies that have versions that aren't patched, e.g.
```
  ...
  "_comment": {
    "1747": {
      "module": "browserslist",
      "affects": ["jest@26.6.3 - testing tool", "tap@15.0.2 - testing tool"]
    }
  },
  ...
```
8.	run `npm run audit` to make sure that everything is resolved