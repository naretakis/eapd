### Getting the code

First you'll need to get the code onto your computer. The easiest way is to
clone it with git. If you're not familiar with git, a tool like
[Github Desktop](https://desktop.github.com/) or
[SourceTree](https://www.sourcetreeapp.com/) can help make the experience
easier.

Most people will use the HTTPS link, but if you're a project contributor and
you have your SSH keys configured, you'll clone from the SSH link. You can
find the link by clicking the green "Clone or download" button above the file
listing on this page.

The HTTPS link is https://github.com/CMSgov/eAPD.git

If you're familiar with git and just want to work from the command line, you
just need to run:

```shell
git clone https://github.com/CMSgov/eAPD.git
```

If you can't use git for some reason, you can also download the most recent
code as [a ZIP file](https://github.com/CMSgov/eAPD/archive/refs/heads/main.zip).

### Required tools

This applications requires [node v16.16.0](https://nodejs.org/download/release/v16.16.0/), [npm v8.11.0](https://docs.npmjs.com/cli/v8), and [yarn v1.22.18](https://yarnpkg.com/getting-started/install). We recommend installing npm through [nvm](https://github.com/nvm-sh/nvm#install--update-script).

### Required services

**Okta (required)** The app uses Okta for authentication. If you do not have an Okta application already
set up, you can create a free development Okta account and Okta application by following
the [[Setting Up Dev Okta]] guide.

**Cypress** The app uses Cypress for end-to-end testing. You can set up a free Cypress Cloud account [here](https://www.cypress.io/pricing?v=2).

**Chromatic** The app uses Chromatic for visual regression testing. You can set up a free account [here](https://www.chromatic.com/pricing).

### Installation Guides

Set the following environment variables:

```shell
export JWT_SECRET= #any string is fine here.  It does affect your security posture, but for local development it doesn't matter.
export OKTA_API_KEY= #from admin, or API -> Tokens -> Create Token, and the Token Value
export OKTA_AUDIENCE= #from admin, or API -> Authorization Server, and the value under Audience
export OKTA_CLIENT_ID= #from admin, or Applications -> (your application) -> General
export OKTA_DOMAIN= #from admin, or Applications -> (your application) -> General
export OKTA_SERVER_ID= #from admin, or API -> Authorization Server, and the value under Name
```

We recommend using [Docker](https://www.docker.com) to run the app locally. We
provide a Docker configuration that will quickly install and build everything
you need, so don't have to. It'll also take care of getting everything running
and connected. If you don't have or can't use Docker, you can also run
everything manually.

[[Docker Install]] <br>
[[Manual Install]]

See the [[testing documentation|Development accessibility, testing, and linting#Testing]] for information about running
tests.

### Troubleshooting
[Troubleshooting](https://github.com/CMSgov/eAPD/wiki/Troubleshooting-Development-Environment)
