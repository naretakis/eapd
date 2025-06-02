# 3.2.0
## Sep 7, 2021

##### Build System / Dependencies

- Move Changelog to Wiki [[#3426](https://github.com/CMSgov/eAPD/issues/3426)]
- changelog generator [[#3453](https://github.com/CMSgov/eAPD/issues/3453)] ([df63684c](https://github.com/CMSgov/eAPD/commit/df63684cf69d53642154cf90f07fadcd47c77623))

##### New Features

- Adds endpoint to support state certification letters [[#3403](https://github.com/CMSgov/eAPD/issues/3403)] ([c2e3da2c](https://github.com/CMSgov/eAPD/commit/c2e3da2c502962340e60af56424e6fe4e6be97b4))
- Update the way Activities names are display to be consistent [[#3404](https://github.com/CMSgov/eAPD/issues/3404)]

##### Testing

- Update tests in auth.js to handle our new auth flow [[#3254](https://github.com/CMSgov/eAPD/issues/3254)]
- Add e2e tests for Activities - adding activitites [[#3326](https://github.com/CMSgov/eAPD/issues/3326)]
- Add e2e tests for Activities - Activity Overview [[#3327](https://github.com/CMSgov/eAPD/issues/3327)]
- Add e2e tests for Activities - Outcomes and milestones [[#3328](https://github.com/CMSgov/eAPD/issues/3328)]
- Add e2e tests for Activities - State staff and expenses [[#3330](https://github.com/CMSgov/eAPD/issues/3330)]
- Add e2e tests for Activities - Private Contractor Costs [[#3331](https://github.com/CMSgov/eAPD/issues/3331)]
- Add e2e tests for Activities - Cost allocation and other funding [[#3332](https://github.com/CMSgov/eAPD/issues/3332)]
- Add e2e tests for Activities - Budget and FFP [[#3333](https://github.com/CMSgov/eAPD/issues/3333)]
- Add e2e tests for Assurances and Compliance [[3390](https://github.com/CMSgov/eAPD/issues/3390)]
- Create e2e tests for default values for Activity Schedule Summary - Default Value [[#3391](https://github.com/CMSgov/eAPD/issues/3391)]

##### Fixes

- JWTs still crossing environments in Staging and Production [[#3407](https://github.com/CMSgov/eAPD/issues/3407)]
- Program Type checkboxes should be radio buttons [[3363](https://github.com/CMSgov/eAPD/issues/3363)]


# 3.1.1
## Aug 23, 2021

#### 🚀 New features

- Federal admin panel ([#2812])

#### 🐛 Bugs fixed

- fixed export view of activity budgets ([#3388])

#### ⚙️ Behind the scenes

- added Mongo server to the preview builds ([#3104])
- added end-to-end tests for filling out key personnel page ([#3284])
- added arrays to endpoint permissions ([#3288])
- added end-to-end tests for previous activities page ([#3312])
- added end-to-end tests for Activities - Default values ([#3313])
- moved end-to-end tests to new location ([#3342])
- added previous activities test ([#3377])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2812]: https://github.com/CMSgov/eAPD/issues/2812
[#3104]: https://github.com/CMSgov/eAPD/issues/3104
[#3284]: https://github.com/CMSgov/eAPD/issues/3284
[#3288]: https://github.com/CMSgov/eAPD/issues/3288
[#3312]: https://github.com/CMSgov/eAPD/issues/3312
[#3313]: https://github.com/CMSgov/eAPD/issues/3313
[#3342]: https://github.com/CMSgov/eAPD/issues/3342
[#3377]: https://github.com/CMSgov/eAPD/issues/3377
[#3388]: https://github.com/CMSgov/eAPD/issues/3388

-----

# 3.1.0
## Aug 4, 2021

#### 🚀 New features

- manage affiliations and choose state page now make live calls for the list of affiliations ([#3264])
- Update the roles returned by the roles endpoint ([#3277])
- added alerts to each section if no FFY has been selected ([#3202])

#### 🐛 Bugs fixed

- Activity Summary displaying incorrectly in Executive Summary ([#3338])
- "Add Activity" button in activity page links to wrong APD ([#3334])
- resolved issue with invalid jwt throwing error ([#3283])
- Reduced the size of the JWT payload because sys admins had a 24KB payload and the max size is 4KB. ([#3246])
- fixed error for users with view-document permission not being able to load an APD([#3264])

#### ⚙️ Behind the scenes

- updated APD seed data used for testing ([#2863])
- created test tokens when database is seeded (development and test only) ([#3128])
- add tests for authentication ([#3188])
- install cypress for end-to-end testing ([#3226])
- updated APD seed data used for testing ([#2863])
- prevented some unexpected JSON parsing errors from being escalated to the error log. ([#3176])
- Reduced the size of the JWT payload because sys admins had a 24KB payload and the max size is 4KB. ([#3246])
- fixed error for users with view-document permission not being able to load an APD([#3264])
- remove sys admins being returned in affiliations ([#3295])
- added end-to-end test for APD overview section ([#3282])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#3283]: https://github.com/CMSgov/eAPD/issues/3283
[#2863]: https://github.com/CMSgov/eAPD/issues/2863
[#3128]: https://github.com/CMSgov/eAPD/issues/3128
[#3188]: https://github.com/CMSgov/eAPD/issues/3188
[#3226]: https://github.com/CMSgov/eAPD/issues/3226
[#3246]: https://github.com/CMSgov/eAPD/issues/3246
[#3202]: https://github.com/CMSgov/eAPD/issues/3202
[#3164]: https://github.com/CMSgov/eAPD/issues/3164
[#3176]: https://github.com/CMSgov/eAPD/issues/3176
[#3264]: https://github.com/CMSgov/eAPD/issues/3264
[#3295]: https://github.com/CMSgov/eAPD/issues/3295
[#3334]: https://github.com/CMSgov/eAPD/issues/3334
[#3338]: https://github.com/CMSgov/eAPD/issues/3338
[#3277]: https://github.com/CMSgov/eAPD/issues/3277
[#3282]: https://github.com/CMSgov/eAPD/issues/3282

-----

# 3.0.1
## Jul 15, 2021

#### 🚀 New features

#### 🐛 Bugs fixed

- Manage Account Page does not render ([#3270])
- Upgrade Browser alert not showing up for IE11 ([#3272])

#### ⚙️ Behind the scenes

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#3270]: https://github.com/CMSgov/eAPD/issues/3270
[#3272]: https://github.com/CMSgov/eAPD/issues/3272

-----

# 3.0.0
## Jul 12, 2021

#### 🚀 New features

- Allow switching between states/affiliations when applicable ([#2581])
- Update the delete process for FFY ([#2996])
- New design updates to Manage Account page ([#3204])
- updated Assurance and Compliance text on APD review and export screen to show more detailed information. ([#3169]))
- Login screen is disabled if api check fails ([#3223])

#### 🐛 Bugs fixed

- Images don't load unless you refresh page after logging in ([#3180])
- Removes "Federal" as an option for State Medicaid address ([#3181])
- Revoking a user's access is causing them to disappear and not show in the Inactive tab ([#3238])
- Fixed issue with not storing okta data on login ([#3242])

#### ⚙️ Behind the scenes

- Created endpoint to allow a user to switch states ([#3030])
- Added security check to state/:id endpoint so only users with access to that state can get the data ([#3129])
- endpoint for pulling a user's affiliations ([#3207])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2581]: https://github.com/CMSgov/eAPD/issues/2581
[#2996]: https://github.com/CMSgov/eAPD/issues/2996
[#3030]: https://github.com/CMSgov/eAPD/issues/3030
[#3242]: https://github.com/CMSgov/eAPD/issues/3242
[#3223]: https://github.com/CMSgov/eAPD/issues/3223
[#3181]: https://github.com/CMSgov/eAPD/issues/3181
[#3204]: https://github.com/CMSgov/eAPD/issues/3204
[#3207]: https://github.com/CMSgov/eAPD/issues/3207
[#3180]: https://github.com/CMSgov/eAPD/issues/3180
[#3181]: https://github.com/CMSgov/eAPD/issues/3181
[#3169]: https://github.com/CMSgov/eAPD/issues/3169
[#3238]: https://github.com/CMSgov/eAPD/issues/3238
[#3194]: https://github.com/CMSgov/eAPD/issues/3194

-----

# 2.30.0
## Jun 28, 2021

#### 🚀 New features

- Updated modal that displays when saving an APD fails ([#2997])

#### 🐛 Bugs fixed


#### ⚙️ Behind the scenes

- Use Local Okta User data instead of contacting Okta when populating affiliations ([#3091])
- Update Admin role ([#2964])
- Removes extraneous header for Budget and FPP in the export view ([#3147])
- Updates text on session expiring modal ([#3191])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#3091]: https://github.com/CMSgov/eAPD/issues/3091
[#2997]: https://github.com/CMSgov/eAPD/issues/2997
[#2964]: https://github.com/CMSgov/eAPD/issues/2964
[#3147]: https://github.com/CMSgov/eAPD/issues/3147
[#3191]: https://github.com/CMSgov/eAPD/issues/3191

-----

# 2.29.0
## Jun 15, 2021

#### 🚀 New features

- Additional affiliations may be requested ([#2582])
- Update APD paths to include APD id ([#2589])
- On the state affiliation selection page, give users an option to log out ([#3011])
- Create eAPD JWT ([#3029])
- Updates date validation and formatting to be more accurate ([#3086])
- Update APD Overview page to show if no information has been entered ([#3157])
- Update Key State Personnel page to show if no information has been entered ([#3158])
- Update Key Personnel and Program Management page to show if no information has been entered ([#3159])

#### 🐛 Bugs fixed

- Refreshing Page Traps the User on Validating the Session ([#2976])
- Resolves an issue where logging out did not actually log you out on the first attempt ([#3126])

#### ⚙️ Behind the scenes

- resolve vulnerability issues
- Allowed Federal Admins to get and approve pending affiliations ([#2811])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2582]: https://github.com/CMSgov/eAPD/issues/2582
[#2589]: https://github.com/CMSgov/eAPD/issues/2589
[#2811]: https://github.com/CMSgov/eAPD/issues/2811
[#2976]: https://github.com/CMSgov/eAPD/issues/2976
[#3011]: https://github.com/CMSgov/eAPD/issues/3011
[#3029]: https://github.com/CMSgov/eAPD/issues/3029
[#3086]: https://github.com/CMSgov/eAPD/issues/3086
[#3126]: https://github.com/CMSgov/eAPD/issues/3126
[#3157]: https://github.com/CMSgov/eAPD/issues/3157
[#3158]: https://github.com/CMSgov/eAPD/issues/3158
[#3159]: https://github.com/CMSgov/eAPD/issues/3159

-----

# 2.28.1
## May 27, 2021

#### 🚀 New features

#### 🐛 Bugs fixed

#### ⚙️ Behind the scenes

- vulnerability fixes
- Create table to hold State Admin certifications ([#2962])
- logging test environment ([#3096])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2962]: https://github.com/CMSgov/eAPD/issues/2962
[#3096]: https://github.com/CMSgov/eAPD/issues/3096

-----

# 2.28.0
## May 24, 2021

#### 🚀 New features

- Allow multiple states to be selected in onboarding process ([#2638])
- Updated delete dialog to use thematically consistent modal dialogs instead of basic alerts. ([#2926])
- New affiliation available for federal users ([#2929])
- Update State Admin Notification ([#3065])

#### 🐛 Bugs fixed

- Investigate why rich text editor is losing formatting after page reload ([#2961])
- Add activity label on nav isn't accurate ([#3010])

#### ⚙️ Behind the scenes

- Updated field labels and descriptions in the Private Contractor section of activities ([#2940])
- Upgraded modules ([#2947])
- Updates error codes ([#2550])
- Updates text on dashboard ([#2970])
- Update Github templates ([#3093])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2926]: https://github.com/CMSgov/eAPD/issues/2926
[#2929]: https://github.com/CMSgov/eAPD/issues/2929
[#2638]: https://github.com/CMSgov/eAPD/issues/2638
[#2940]: https://github.com/CMSgov/eAPD/issues/2940
[#2947]: https://github.com/CMSgov/eAPD/issues/2947
[#2550]: https://github.com/CMSgov/eAPD/issues/2550
[#2961]: https://github.com/CMSgov/eAPD/issues/2961
[#2970]: https://github.com/CMSgov/eAPD/issues/2970
[#3010]: https://github.com/CMSgov/eAPD/issues/3010
[#3065]: https://github.com/CMSgov/eAPD/issues/3065
[#3093]: https://github.com/CMSgov/eAPD/issues/3093

-----

# 2.27.0
## May 6, 2021

#### 🚀 New features

#### 🐛 Bugs fixed

- Shows a "password expired" alert instead of "invalid mfa code" alert when logging in with MFA and an expired password ([#2988])

#### ⚙️ Behind the scenes

- Upgraded modules ([#2947])
- Update interaction with Okta on backend ([#2960])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2947]: https://github.com/CMSgov/eAPD/issues/2947
[#2960] https://github.com/CMSgov/eAPD/issues/2960
[#2988]: https://github.com/CMSgov/eAPD/issues/2988

-----

# 2.26.1
## Apr 16, 2021

#### 🚀 New features

- Adds the rich text editor to two existing text fields ([#2394])
- Added help guides and links to new documentation on login page ([#2935])

#### 🐛 Bugs fixed


#### ⚙️ Behind the scenes

- Update description for Outcomes and Metrics ([#2950])


# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2394]: https://github.com/CMSgov/eAPD/issues/2394
[#2935]: https://github.com/CMSgov/eAPD/issues/2935
[#2950]: https://github.com/CMSgov/eAPD/issues/2950

-----

# 2.26.0
## Apr 5, 2021

#### 🚀 New features

- Combine Authenticators in MFA selection ([#2648])
- Email State Admin from State Dashboard when Affiliation is Pending ([#2838])

#### 🐛 Bugs fixed

- Selecting "Cancel" during the state affiliation selection puts the user into a blank screen ([#2706])
- Logout issues ([#2864])

#### ⚙️ Behind the scenes

- Refactor login code ([#2632])


# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2632]: https://github.com/CMSgov/eAPD/issues/2632
[#2648]: https://github.com/CMSgov/eAPD/issues/2648
[#2706]: https://github.com/CMSgov/eAPD/issues/2706
[#2838]: https://github.com/CMSgov/eAPD/issues/2838
[#2864]: https://github.com/CMSgov/eAPD/issues/2864

-----

# 2.25.1
## Mar 31, 2021

#### 🚀 New features

- Add eADPSystemAccess document to backend ([#2938])

#### 🐛 Bugs fixed

- Fixes an issue where the money fields were not formatting when re-loaded ([#2822])
- Checks for error before displaying "Saved!" in message header when app cannot save ([#2830])

#### ⚙️ Behind the scenes

- Add new seed users for different login issues ([#2989])
- Changed s3 buckets

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)
[#2989]: https://github.com/CMSgov/eAPD/issues/2989
[#2822]: https://github.com/CMSgov/eAPD/issues/2822
[#2830]: https://github.com/CMSgov/eAPD/issues/2830
[#2938]: https://github.com/CMSgov/eAPD/issues/2938

-----

# 2.25.0
## Mar 29, 2021

#### 🚀 New features

- Establish Process For Implementing Storybook w/ Examples ([#2909])

#### 🐛 Bugs fixed

- Fixes issue with section borders ([#2370])
- Removes create apd button for federal admins ([#2890])

#### ⚙️ Behind the scenes

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2370]: https://github.com/CMSgov/eAPD/issues/2370
[#2890]: https://github.com/CMSgov/eAPD/issues/2890
[#2909]: https://github.com/CMSgov/eAPD/issues/2909

-----

# 2.24.0
## Mar 11, 2021

#### 🚀 New features

- Improves error messages during the authentication process ([#2694])
- Swaps My State Dashboard title with eAPD logo ([#2776])
- Create an endpoint to serve the help doc ([#2793])
- Update Key State Personnel copy ([#2804])
- Updates "Unable to save" error to use new text and a modal instead of alert ([#2406])

#### 🐛 Bugs fixed

- Render "Last saved..." message only on "/apd" paths ([#2186])
- Fixes an issue where checkboxes and radio buttons have a clickable area that extends past the label ([#2232])
- Fixes issue where "Add another activity" button was not appearing as it should ([#2525])
- Removes help text and examples from Estimated Quarterly Expenditure section of APD export view ([#2538])
- Update Babel/Webpack settings so that application loads in IE11 browsers ([#2601])
- Restrict file uploads ([#2740])
- Fixes issue where the session ending timeout was not showing on certain pages ([#2770])
- Fixes issues where left side nav was not updating when activities were added or their names changed ([#2785])
- Updates contract term label ([#2820])
- Resolve patch failure ([#2826])
- Resolved issue with images not loading in staging ([#2845])
- Update assurances and compliance page with accurate links and details ([#2862]) 

#### ⚙️ Behind the scenes

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2186]: https://github.com/CMSgov/eAPD/issues/2186
[#2232]: https://github.com/CMSgov/eAPD/issues/2232
[#2406]: https://github.com/CMSgov/eAPD/issues/2406
[#2525]: https://github.com/CMSgov/eAPD/issues/2525
[#2538]: https://github.com/CMSgov/eAPD/issues/2538
[#2601]: https://github.com/CMSgov/eAPD/issues/2601
[#2694]: https://github.com/CMSgov/eAPD/issues/2694
[#2740]: https://github.com/CMSgov/eAPD/issues/2740
[#2770]: https://github.com/CMSgov/eAPD/issues/2770
[#2776]: https://github.com/CMSgov/eAPD/issues/2776
[#2785]: https://github.com/CMSgov/eAPD/issues/2785
[#2793]: https://github.com/CMSgov/eAPD/issues/2793
[#2538]: https://github.com/CMSgov/eAPD/issues/2538
[#2601]: https://github.com/CMSgov/eAPD/issues/2601
[#2804]: https://github.com/CMSgov/eAPD/issues/2804
[#2820]: https://github.com/CMSgov/eAPD/issues/2820
[#2826]: https://github.com/CMSgov/eAPD/issues/2826
[#2845]: https://github.com/CMSgov/eAPD/issues/2845
[#2862]: https://github.com/CMSgov/eAPD/issues/2862

-----

# 2.23.0
## Jan 21, 2021

#### 🚀 New features

- Adds confirmation dialog before unchecking FFY year([#2445])
- Adds State Admin panel ([#2583])
- Update endpoint for affiliations to filter by status ([#2682])
- Updated roles and add roles endpoint ([#2692])
- Update session management to warn users that their session is about to expire ([#2702])
- Updates logos in footer ([#2716])
- Increases outcomes and metrics field size to be multiline (4) ([#2724])
- Updates to program summary page ([#2736])
- Resolve TinyMCE XSS vulnerabilities ([#2741])
- Update form field labels for the Activity Private Contractor Costs form ([#2742])
- Updates FTE Allocation Help text ([#2743])
- Updates Previous Activities tables to use clearer headings (#2744)
- Uses "CMS eAPD" for page title and header title ([#2780])


#### 🐛 Bugs fixed

- fixed security headers
- fixed Estimated Quarterly Expenditure table is overwriting across Activities ([#2421])
- displays images within the tinymce editor ([#2348])
- updates footer email address to correct one ([#2353])
- cost allocation activities fix ([#2708])
- fixed issue with Back to APD link not displaying ([#2712])
- fixes issue where removing a FFY from program summary wouldn't remove it from the read-only view ([#2715])
- fixed session expiring warning bug ([#2720])
- activity creation does not add outcomes or milestones ([#2725])


#### ⚙️ Behind the scenes

- Added AWS backend to Terraform ([#2489])
- preview revamp owasp tag ([#2650])
- patches tinymce XSS vulnerability; enables media plugin ([GHSA-vrv8-v4w8-f95h])
- upgrades `@okta/okta-sdk-nodejs`; resolves ([GHSA-w7rc-rwvf-8q5r])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2348]: https://github.com/CMSgov/eAPD/issues/2348
[#2353]: https://github.com/CMSgov/eAPD/issues/2353
[#2421]: https://github.com/CMSgov/eAPD/issues/2421
[#2445]: https://github.com/CMSgov/eAPD/issues/2445
[#2489]: https://github.com/CMSgov/eAPD/issues/2489
[#2583]: https://github.com/CMSgov/eAPD/issues/2583
[#2650]: https://github.com/CMSgov/eAPD/issues/2650
[#2682]: https://github.com/CMSgov/eAPD/issues/2682
[#2692]: https://github.com/CMSgov/eAPD/issues/2692
[#2702]: https://github.com/CMSgov/eAPD/issues/2702
[#2708]: https://github.com/CMSgov/eAPD/issues/2708
[#2712]: https://github.com/CMSgov/eAPD/issues/2712
[#2715]: https://github.com/CMSgov/eAPD/issues/2715
[#2716]: https://github.com/CMSgov/eAPD/issues/2716
[#2720]: https://github.com/CMSgov/eAPD/issues/2720
[#2724]: https://github.com/CMSgov/eAPD/issues/2724
[#2725]: https://github.com/CMSgov/eAPD/issues/2725
[#2736]: https://github.com/CMSgov/eAPD/issues/2736
[#2741]: https://github.com/CMSgov/eAPD/issues/2741
[#2742]: https://github.com/CMSgov/eAPD/issues/2742
[#2743]: https://github.com/CMSgov/eAPD/issues/2743
[#2744]: https://github.com/CMSgov/eAPD/issues/2744
[#2780]: https://github.com/CMSgov/eAPD/issues/2780

[ghsa-vrv8-v4w8-f95h]: https://github.com/advisories/GHSA-vrv8-v4w8-f95h
[ghsa-w7rc-rwvf-8q5r]: https://github.com/advisories/GHSA-w7rc-rwvf-8q5r

-----

# 2.22.0
## Dec 7, 2020

#### 🚀 New features

- Allow users to delete the last activity cost entry ([#2152])
- Integrates Okta for authentication ([#2345])
- Updates to the login screens ([#2565])
- Add ability for user to choose an MFA type if not selected already ([#2566])
- Add ability for user to request access to a state ([#2567])
- Create user status screens ([#2568])
- Create a table to hold affiliations ([#2569])
- Update roles and access for approving access requests ([#2572])
- Create endpoints for requesting/approving access ([#2574])
- Show the Activity Total Cost in the Proposed Budget Summary and Budget and FFP page ([#2597])
- Update authorization to use new affiliations table ([#2617])

#### 🐛 Bugs fixed

#### ⚙️ Behind the scenes

- sending user role to Google Analytics
- changed the way some tables are being seeded
- Add API endpoint for user to select a state ([#2679])
- Centralize API error handling ([#2655])
- removed the user profile page

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2152]: https://github.com/cmsgov/eapd/issues/2152
[#2345]: https://github.com/cmsgov/eapd/issues/2345
[#2565]: https://github.com/cmsgov/eapd/issues/2565
[#2566]: https://github.com/cmsgov/eapd/issues/2566
[#2567]: https://github.com/cmsgov/eapd/issues/2567
[#2568]: https://github.com/cmsgov/eapd/issues/2568
[#2569]: https://github.com/cmsgov/eapd/issues/2569
[#2572]: https://github.com/cmsgov/eapd/issues/2572
[#2574]: https://github.com/cmsgov/eapd/issues/2574
[#2597]: https://github.com/cmsgov/eapd/issues/2597
[#2617]: https://github.com/cmsgov/eapd/issues/2617
[#2679]: https://github.com/CMSgov/eAPD/issues/2679
[#2655]: https://github.com/CMSgov/eAPD/issues/2655

-----

# 2.21.0
## Oct 29, 2020

#### 🚀 New features

- Update areas in the app where "total computable" should be used ([#2324])
- Add help text to Contract Term field ([#2431])
- Rename State Cost Category page and update Nav Bar to better assist users in navigation ([#2432])
- Match "total cost" in export to "Total Contract Cost" field label in builder ([#2459])
- Update Program Activities headers, labels, and help text ([#2528])
- Rename Objectives and Key Results to Outcomes and Metrics ([#2584])
- Updates to improve accessibility ([#2607])
- Enable the TinyMCE Help guide ([#2611])

#### 🐛 Bugs fixed

#### ⚙️ Behind the scenes

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2324]: https://github.com/CMSgov/eAPD/issues/2324
[#2431]: https://github.com/CMSgov/eAPD/issues/2431
[#2432]: https://github.com/CMSgov/eAPD/issues/2432
[#2459]: https://github.com/CMSgov/eAPD/issues/2459
[#2528]: https://github.com/CMSgov/eAPD/issues/2528
[#2584]: https://github.com/CMSgov/eAPD/issues/2584
[#2607]: https://github.com/CMSgov/eAPD/issues/2607
[#2611]: https://github.com/CMSgov/eAPD/issues/2611

-----

# 2.20.0
## Oct 21, 2020

#### 🚀 New features

- Metrics: Research using Google Analytics for Operational Metrics ([#2139])
- Metrics: Create APD event database table ([#2140])
- Metrics: API endpoint for Export events ([#2141])
- Metrics: Hook the export button into the API ([#2142])
- Replace the “Cost Allocation and Budget for FFY 2020” table with part of the new "Summary Budget by Activity” table ([#2306])
- Other funding amount should be represented as a subtraction on Activity Breakdown table ([#2429])
- Updates tables to increase accessibility ([#2501])
- Updates markup to use semantic `<nav>` and `<main>` where appropriate ([#2502])
- Updated inputs in the Estimated Quarterly Incentive Payments table to use aria-labelledby for better UX/a11y ([#2503])
- Give users the ability to choose FFYs before entering their Key Personnel ([#2509])
- Add bulleted lists, numbered lists, formatting dropdown to the RichText editor ([#2521])
- Where groups of checkboxes are used, use appropriate grouping markup including legend/label/fieldset ([#2545])
- Add a label to the rich text editor `<textarea>` element ([#2546])

#### 🐛 Bugs fixed

#### ⚙️ Behind the scenes

- Update @cmsgov/design-system to v2.1.1 [[releases](https://github.com/CMSgov/design-system/releases)]
- Refactor use of Dropdown component ([#2471])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2139]: https://github.com/CMSgov/eAPD/issues/2139
[#2140]: https://github.com/CMSgov/eAPD/issues/2140
[#2141]: https://github.com/CMSgov/eAPD/issues/2141
[#2142]: https://github.com/CMSgov/eAPD/issues/2142
[#2306]: https://github.com/CMSgov/eAPD/issues/2306
[#2429]: https://github.com/CMSgov/eAPD/issues/2429
[#2471]: https://github.com/CMSgov/eAPD/issues/2471
[#2501]: https://github.com/CMSgov/eAPD/issues/2501
[#2502]: https://github.com/CMSgov/eAPD/issues/2502
[#2503]: https://github.com/CMSgov/eAPD/issues/2503
[#2509]: https://github.com/CMSgov/eAPD/issues/2509
[#2521]: https://github.com/CMSgov/eAPD/issues/2521
[#2545]: https://github.com/CMSgov/eAPD/issues/2545
[#2546]: https://github.com/CMSgov/eAPD/issues/2546

-----

# 2.19.0
## Oct 13, 2020

#### 🚀 New features
- Change order of fields and field/title names on Cost Allocation and Other Funding + Budget and FFP pages. ([#2322])

#### 🐛 Bugs fixed


#### ⚙️ Behind the scenes


# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)
[#2322]: https://github.com/CMSgov/eAPD/issues/2322

-----

# 2.18.0
## Sep 22, 2020

#### 🚀 New features

- Results of previous activities fields are missing in export view ([#2420])
- Standards and conditions is in the wrong area on export view ([#2386])
- Match private contractor costs section on export view to builder ([#2393])

#### 🐛 Bugs fixed


#### ⚙️ Behind the scenes


# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2420]: https://github.com/CMSgov/eAPD/issues/2420
[#2386]: https://github.com/CMSgov/eAPD/issues/2386
[#2393]: https://github.com/CMSgov/eAPD/issues/2393

-----

# 2.17.0
## Sep 14, 2020

#### 🚀 New features

- Upgrade to @cmsgov/design-system v2.0.0, remove focus styles ([#2412])
- Update button text to match verbiage on page ([#2367])
- Update Key Personnel and Program Management page instructions and help text ([#2325])
- Change "Objectives and key results" Nav Bar title to match contents of page ([#2368])
- Activity section Previous & Continue buttons/arrow iconography ([#2213])

#### 🐛 Bugs fixed

- Content in the export view needs to match the builder ([#2387])
- Key personnel FTE not being saved for 2022 ([#2401])
- Arrows in the side nav should be consistent ([#2188])
- Nav bar does not indicate correct location with launch of different APD ([#2223])
- Clicking on the navigation places you right below the anchor point ([#2410])
- Scroll changes navigation buttons on export and submit page ([#2359])
- When navigating with Continue/Previous buttons, Nav does not expand to current page ([#2415])

#### ⚙️ Behind the scenes

- Use audit-ci for auditing node packages within our pipeline ([#2335])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2387]: https://github.com/CMSgov/eAPD/issues/2387
[#2412]: https://github.com/CMSgov/eAPD/issues/2412
[#2335]: https://github.com/CMSgov/eAPD/issues/2335
[#2367]: https://github.com/CMSgov/eAPD/issues/2367
[#2325]: https://github.com/CMSgov/eAPD/issues/2325
[#2401]: https://github.com/CMSgov/eAPD/issues/2401
[#2188]: https://github.com/CMSgov/eAPD/issues/2188
[#2223]: https://github.com/CMSgov/eAPD/issues/2223
[#2410]: https://github.com/CMSgov/eAPD/issues/2410
[#2359]: https://github.com/CMSgov/eAPD/issues/2359
[#2415]: https://github.com/CMSgov/eAPD/issues/2415
[#2368]: https://github.com/CMSgov/eAPD/issues/2368
[#2213]: https://github.com/cmsgov/eapd/issues/2213

-----

# 2.16.0
## Aug 10, 2020

#### 🚀 New features

- Upgrade to @cmsgov/design-system v2.0.0, remove focus styles ([#2412])
- Update button text to match verbiage on page ([#2367])
- Update Key Personnel and Program Management page instructions and help text ([#2325])
- Change "Objectives and key results" Nav Bar title to match contents of page ([#2368])
- Activity section Previous & Continue buttons/arrow iconography ([#2213])

#### 🐛 Bugs fixed

- Content in the export view needs to match the builder ([#2387])
- Key personnel FTE not being saved for 2022 ([#2401])
- Arrows in the side nav should be consistent ([#2188])
- Nav bar does not indicate correct location with launch of different APD ([#2223])
- Clicking on the navigation places you right below the anchor point ([#2410])
- Scroll changes navigation buttons on export and submit page ([#2359])
- When navigating with Continue/Previous buttons, Nav does not expand to current page ([#2415])

#### ⚙️ Behind the scenes

- Use audit-ci for auditing node packages within our pipeline ([#2335])

# Previous releases

See our [release history](https://github.com/CMSgov/eAPD/releases)

[#2387]: https://github.com/CMSgov/eAPD/issues/2387
[#2412]: https://github.com/CMSgov/eAPD/issues/2412
[#2335]: https://github.com/CMSgov/eAPD/issues/2335
[#2367]: https://github.com/CMSgov/eAPD/issues/2367
[#2325]: https://github.com/CMSgov/eAPD/issues/2325
[#2401]: https://github.com/CMSgov/eAPD/issues/2401
[#2188]: https://github.com/CMSgov/eAPD/issues/2188
[#2223]: https://github.com/CMSgov/eAPD/issues/2223
[#2410]: https://github.com/CMSgov/eAPD/issues/2410
[#2359]: https://github.com/CMSgov/eAPD/issues/2359
[#2415]: https://github.com/CMSgov/eAPD/issues/2415
[#2368]: https://github.com/CMSgov/eAPD/issues/2368
[#2213]: https://github.com/cmsgov/eapd/issues/2213

-----

# 2.15.1
## Jul 30, 2020

#### 🚀 New features

#### 🐛 Bugs fixed

- FFP and budget page data from Activity 1 is being shown in every Activity in the export view ([#2385])

#### ⚙️ Behind the scenes

# Previous releases

See our [release history](https://github.com/18F/cms-hitech-apd/releases)

[#2385]: https://github.com/18F/cms-hitech-apd/issues/2385

-----

# 2.15.0
## Jul 27, 2020

#### 🚀 New features

#### 🐛 Bugs fixed

- Text Boxes for TinyMCE don't update when navigating between "Activity Overview" sections between Activities ([#2316])
- The hourly resource and FFY costs are not overwriting as expected ([#2236])
- Start/End Dates in Export View should be in MM/DD/YYYY format ([#2314])

#### ⚙️ Behind the scenes

- Change Redux Action Types from symbols to string constants ([2349])
- Update postman script for recent migrations ([#2340])

# Previous releases

See our [release history](https://github.com/18F/cms-hitech-apd/releases)

[#2316]: https://github.com/18F/cms-hitech-apd/issues/2316
[#2349]: https://github.com/18F/cms-hitech-apd/issues/2349
[#2340]: https://github.com/18F/cms-hitech-apd/issues/2340
[#2236]: https://github.com/18F/cms-hitech-apd/issues/2236
[#2314]: https://github.com/18F/cms-hitech-apd/issues/2314

-----

# 2.14.0
## Jul 13, 2020

#### 🚀 New features

- The $0 placeholder in dollar fields doesn't always disappear (#2230)
- Update help text for Activities > Activity Overview > Activity Schedule (#2313)
- Add an “Add another activity” button to the last page of the last activity (#2282)
- Update Activity Schedule Summary page (#2318)
- Update help text for the FFP/Federal-state split selection (#2311)

#### 🐛 Bugs fixed

#### ⚙️ Behind the scenes

- [TechDebt] Fix calls to cmsgov <Review/> component with props.headingLevel as number, string is required

-----

# 2.13.0
## Jun 30, 2020

#### 🚀 New features

- Update Summary Budget Table (#2290)
- Update Actual Costs page to use "Actual Expenditures" (#2291)
- Build the "Summary Budget by Activity" table to see staffing across all activities and not just by activity (#2170)
- Update styling on the Program Activities page (#2288)
- Update State Cost Categories section for consistency (#2256)

#### 🐛 Bugs fixed

- Update copy for Milestones (#2246)
- Use consistent naming for Activity dates (#2251)

#### ⚙️ Behind the scenes

- Prevent negative FTE values from being entered in State Cost forms (#2229)
- [Tech Debt] Cleanup propType errors, other test errors/warnings (#2309)

-----

# 2.12.0
## Jun 15, 2020

#### 🚀 New features

- Hide Create New APD button for users who don't have create permission (#2198)

#### 🐛 Bugs fixed

- none

#### ⚙️ Behind the scenes

- Capture how much of an activity's other funding is attributable to each cost category, to be used to show the Medicaid total of each category separately (#2169)

-----

# 2.11.0
## Jun 2, 2020

#### 🚀 New features

- Update Print Preview Layout (#2182)
- Make the "Saving" message persist for 750ms (#2207)
- Move the activity schedule information to the top of the Activity Overview section (#2210)

#### 🐛 Bugs fixed

- none

#### ⚙️ Behind the scenes

- [Tech Debt] Add Section test (#2176)
- [Tech debt] Add one more test case for the links context provider (#2179)
- [Tech Debt] Refactor API user serialization methods (#2206)

-----

# 2.10.0
## Jun 1, 2020

#### 🚀 New features

- Adjust Key Personnel Calculations (#2174)
- update 'Statement of alternative considerations and supporting justification' help text (#2185)

#### 🐛 Bugs fixed

- Left side navigation should not get stuck under the header (#2187)
- NumberFields should allow numbers with decimals to be entered (#2214)

#### ⚙️ Behind the scenes

- Authenticate HTTP Clients via JWT presented in Authorization header (#2100)
- Update minimum Chrome version; add download link to Microsoft Edge (#2145)
- Set Minimum Green Browser Support for Chrome to Version 78 (#2216)

-----

# 2.9.0
## May 4, 2020

#### 🚀 New features

- Implement secondary back/next navigation buttons (#2103)
- Add Margin/Padding to scroll bar lane (#2155)

#### 🐛 Bugs fixed

- fixed Header Alignment Issue (#2122)
- added padding for admin dashboard title (#2144)

#### ⚙️ Behind the scenes

- Removed unused libraries and tools (#2137)

-----

# 2.8.0
## Apr 7, 2020

#### 🚀 New features

- Adds a new warning dialog to explain when unexpected errors are encountered
  and what the user can do about it. (#2112)
- The header displays the time ago since the APD was last saved (#2104)

#### 🐛 Bugs fixed

- Adds some explanation and help text to the estimated quarterly expenditure table (#2110)
- Fixed an issue where new APDs and activities came prepopulated with cost information (#2129) which could cause incorrect behavior in the activity cost summary table (#2130)
- Fixed an issue where adding an activity could make it impossible to save the APD (#2148)
- Fixed an issue where printing from a screen other than the export screen resulted in excessive whitespace (#2114)

#### ⚙️ Behind the scenes

- Updated 3rd-party libraries to the latest versions

-----

# 2.7.0
## Mar 23, 2020

#### 🚀 New features

- An all-new activity budget and FFP section (#2081)
- Switched to a paginated APD view (#2086)
- Attached the header and sidebar to the page so are always available (#2090, #2087)
- Added an autosave status message to the header (#2090)
- Removed the floating save button (#2091)

#### 🐛 Bugs fixed

- Removed an overly strict validation rule that could prevent APDs from saving properly (#2088)

-----

# 2.6.0
## Mar 9, 2020

#### 🚀 New features

- Updates the cost allocation section to make it clearer how the various numbers are related to each other, and updates the help text describing "other funding." (#1935, #1992)
- The executive summary for activities now includes activity costs per federal fiscal year (#1927)
- Activity state personnel now show calculated total cost instead of just rate and FTEs. (#2013)
- Moves the activity FFP section into a separate tab (#2010)
- Activities are no longer associated with the HIT program by default (#2059)
- Remove activity list in favor of editing names/funding source in modal (#2053)

#### 🐛 Bugs fixed

- Fixed a bug where APD Key Personnel weren't being counted as state personnel for the Program Administration activity for some budget calculations. - (#2037)
- Updated the text describing in-house cost categories to be more clear (#1936)
- Fixed a bug where autosave happened too often, causing performance issues, and potentially inconsistent saved data.
- Fixed a bug where the FFY subtotal for each cost category in the quarterly FFP table was based on the percent of funding requested, meaning it could be different from the actual activity total if the user requests more or less than 100%. (#2056)
- Fixed a bug that prevented creating new activities.
- Fixed a typo in the cost allocation instructions
- Updated the explanation for how the budget summary table is calculated (#2058)
- Fixed a bug where save actions from on APD could be applied to a different APD (#2084)
- Adds outline images for American Samoa, the Commonwealth of the Northern Mariana Islands, Guam, and the US Virgin Islands (#1758)

#### ⚙️ Behind the scenes

- Made the code for removing list items a bit simpler (#2014)
- Change how uploaded files get IDs (#2018)
- Cleaned up some inconsistencies in the way things were named internally (#2044, #2066)
- Got rid of some old code that no longer made sense (#2021)

-----

# 2.5.0
## Feb 3, 2020

### 🚀 New features

- Changed activity goals to activity objectives and key results (OKRs) (#2007)
- Make autosave more screen-reader friendly (#2020)
- Changed the APD name to HITECH IAPD (#1821, #1993)
- Added loading state for rich text editor (#2015)

### 🐛 Bugs fixed

- Fixed a bug where toggling the "show password" checkbox on passwords caused the text field to be changed to "Show password" (#2023)
- Fixed a bug where adding a new list item to an activity (goal, milestone, expense, etc.) caused that new item to be expanded every time the activity was opened until the page was reloaded. (#2026)
- Fixed a bug where images could upload every single time an APD loaded, forever and ever (#2017)

### ⚙️ Behind the scenes

- Split up some code components to make them more reusable (#2005)

-----

# 2.4.0
## Jan 22, 2020

#### 🚀 New features

- Remove the unsaved changes/logout warnings because we have automatic saves now! (#1995)
- Improved the layout of the exported PDF (#1961)
- Activities now open in modals for a cleaner editing experience (#1997)

#### 🐛 Bugs fixed

- Fixed a bug where everything was in italics. (#1998)

#### ⚙️ Behind the scenes

- Added browser security headers to frontend web responses (#1966)
- Updated dependencies (#1985)
- Removed some old, unused dev tools and rearranged some analytics code (#1990, #1991)

-----

# 2.3.0
## Jan 7, 2020

#### 🚀 New features

- Updated the activity section (#1942)

#### 🐛 Bugs fixed

- Fixed a bug where the login and admin screens could have a white box at the bottom in tall browser windows (#1766)
- Fixed a bug where an admin could not edit a user's account without changing that user's email address (#1973)

#### ⚙️ Behind the scenes

- Updated to the latest version of the CMS Design System ([#1981])
- Updated dependencies

-----

# 2.2.0
## Dec 18, 2019

#### 🚀 New features

- Make disabled button state more explicit (#1957)
- Upload files from the rich text editor instead of embedding them directly into the text (#1735)
- Made the rich text areas resize to fit their contents
- Automatically save APDs as changes are made
- Removed the 11 Standards and Conditions text fields in favor of two simpler fields (#1947)

#### 🐛 Bugs fixed

- Fixed an issue with the sidebar scrolling into the footer (#1967)

#### ⚙️ Behind the scenes

- Added OWASP ZAP active security scan in continuous integration and deployment (#1928)

-----

# 2.1.0
## Dec 3, 2019

#### 🚀 New features
- Added a print preview page (#1921)
- Display a loading screen while waiting for the APD to load so users can tell the app is doing something. (#1368)

#### 🐛 Bugs fixed
- Fixed a bug where contractor hourly rates were not used in budget calculations (#1925)

#### ⚙️ Behind the scenes
- Removed unused code (#1801, #1802, #1803)

-----

# 2.0.1
## Nov 18, 2019

#### 🐛 Bugs fixed

- Updated dependencies with known vulnerabilities

-----

# 2.0.0
## Nov 18, 2019

#### 🚀 New features

- Alert users on yellow support browsers that they should upgrade ([#1904])
- Don't try to load the page on unsupported browsers ([#1882])

#### 🐛 Bugs fixed

- Fixed an issue where the label for the state name dropdown in the State Profile section was not correctly associated ([#1779])
- Fixed an issue where some table header cells were empty ([#1780])

#### ⚙️ Behind the scenes

- Switched from a relational data model for APDs to a document-oriented model ([#1793], [#1794], [#1796], [#1798], [#1800], [#1826])
- Removed unused code ([#1799])

-----

# 1.1.0
## Sep 27, 2019

#### 🚀 New features

- Attempt to alert users before automatically logging them out due to inactivity. The app will try to use built-in browser notifications as well as flashing the tab title. In browsers that support it, the app treats activity in any eAPD tab as valid, so all eAPD tabs will remain valid as long as at least one of them is getting activity. (#1697)
- Scroll the collapsed activity review panel into view after collapsing an activity form. This way, when you collapse an activity, you end up essentially looking at the list of activities again instead of being pushed way down the page. (#1732)
- Automatically select numeric form field contents when the field is focused if the current value is 0 (#1736)
- Add spellcheck to rich text fields (#1769)

#### 🐛 Bugs fixed

- Add a "skip to main content" link (#1304)
- Prompt for confirmation before deleting APD key personnel (#1651, #1647)
- Fixed accessibility issues on the login page and the dashboard (#1688)
- Fixed semantic heading levels (#1695)
- Fixed a keyboard focus order problem when adding new items to a list (#1712)
- Fixed a keyboard focus order problem with the system use banner (#1715)
- Fixed the save button so it doesn't go into the footer (#1524)
- Switched remaining text inputs (except for rich text) to Design System components and removed custom components (#1686)
- For users in American Samoa, Guam, Northern Mariana Islands, or U.S. Virgin Islands, do not attempt to display a territory outline at the top of the sidebar because we don't have those outlines (#1423; see #1730 for more information)
- Fixed a bug where adding a new contractor resource didn't expand the contractor form (#1710)
- Make the navigation sidebar scrollable. (#1475)
- Fixed the width on activity overview detail and statement of alternatives textbox labels (#1640)
- Made the "manage account" and "login" text the same size in the header dropdown (#1655, #1680)
- Removed the emoji button from the rich text editor (#1649)
- Extend user sessions on API activity (#1728)
- Adds spacing around the Medicaid director and Medicaid office address form headers (#1646)
- Adds margin to the bottom of the state dashboard (#1601)
- Adds an ARIA region component to prevent screen readers from prematurely announcing quarterly budget numbers (#1731)
- Fixed alignment of the message if there are no APDs on the state dashboard (#1602)
- Adds spacing between the login form and the "forgotten password" help link (#1600)
- Adds per-year APD key personnel costs to the review view (#1747)
- Adds a more informative error message if attempting to save an APD while logged out (#1729)
- Use a dollar field for the "other funding" field in the cost allocation form (#1754)
- Fixes a screen reader bug by adding a wrapper around the CMS Design System's Choice component (#1760)
- Round off dollar input fields when they lose focus (#1739)
- Fixed a bug where multiline plain text fields (such as the activity overview) gets exported as a text field, and the content is truncated within it. (#1767)
- Fixed a bug where the session authentication cookie would expire at the end of the browser session instead of at the scheduled time. (#1756)
- Fixed the spacing in the activity overview section. (#1648)
- Disabled cacheing of the index page, so that clients always get the latest. (#1775)
- Fixed a bug where the APD Key Personnel section asked for a person's percent time using a plain number input box instead of a percent box (#1753)
- Improved ARIA metadata on the account management dropdown button for screen readers (#1681)
- Fixed a bug where the sidebar would change width during scrolling in IE. (#1434)
- Changed the APD title to include the full year range instead of just the start year (#1820)

#### ⚙️ Behind the scenes

- Removed old styles (#1770)
- Remove unused code
- Updated 3rd-party dependencies
- Refactored the activity quarterly cost allocation tables (#1574)

-----

# 1.0.4
## Aug 15, 2019

* Fixes a bug where multiline plain text fields (such as the activity overview) would not be expanded in the exported PDF, resulting in a textbox with scroll bars. Instead, in the exported PDF, the text field is replaced with just its content. (#1767)

-----

# 1.0.3
## Aug 14, 2019

- Fixes a bug where adding a federal fiscal year to the APD causes the app to crash when users attempt to edit existing activity contractor resources. (#1762)
- Fixes a bug where entering a date and then backing it out would make it impossible to save the APD. (#1765)
- Fixes a bug where adding a federal fiscal year to the APD while an activity contractor resource form was expanded would cause the app to crash.

-----

# 1.0.2
## Aug 2, 2019

- Fixes a bug where the summary budget table individual line items would show $0 if any single activity's total cost was $0. ([#1745](https://github.com/18F/cms-hitech-apd/pull/1745))

-----

# 1.0.1
## Jul 19, 2019

* Adds lightweight date validation

-----

# Pilot
## Jul 9, 2019