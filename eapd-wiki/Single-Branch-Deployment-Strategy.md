## Single Branch
### Full Get Flow Diagram
[![Git Flow Diagram](https://github.com/CMSgov/eAPD/blob/main/documentation/git-flow-diagram.png?raw=true)](https://github.com/CMSgov/eAPD/blob/main/documentation/git-flow-diagram.png?raw=true)
* Merges into main trigger deploys to staging
* Releases are managed through the GitHub UI

### Deploy feature to default branch (main)
* Create a new branch

```git checkout -b bbrooks/newFeature main```
* Make changes to branch, push changes to GitHub

```git push --set-upstream origin bbrooks/newFeature```

```git push -u origin bbrooks/newFeature```
* Create PR in GitHub UI
* Satisfy PR Requirements
* Squash & Merge
* Delete the branch

### Create release
* When default branch (main) is ready for release
* Create release in GitHub UI
 * Create tag, target main branch
 * Publish when ready

### Hotfix/Revert to previous Release
In this scenario we have Released from the main branch version 1.0.0. Work has continued on the main branch and it is no longer reflective of what was deployed to production and we need to apply a hotfix to production. 

In overview we will be creating a release branch, which will serve as a stand-in for main, and a hotfix branch. The release branch will be created from the commit ID of the last Release and the hotfixes will be merged into it. The 1.0.1 hotfixed Release will be created from the release branch instead of the main branch, following our normal Release procedures. Before closing the hotfix branch it should also be merged into the up to date main branch as well.

* Find commit of tagged release

Where v1.0.0 equals the release you're hotfixing/reverting to

```git rev-list -n 1 v1.0.0```
* Create branch from commit ID

```git branch bbrooks/release1.0.1 $commit-id```
* Create a hotfix branch (hotfix1.0.1) from the new branch (release1.0.1)
* Create the fix on hotfix branch
* Create PR of hotfix branch into branch created from release (release1.0.1)
* Satisfy PR Requirements
* Squash & Merge
* Create release in GitHub UI
 * Create tag (v1.0.1), target release branch (release1.0.1)
 * Publish when ready
* Merge hotfix branch into up to date main branch
* Delete hotfix branch
* Delete release branch

Useful tidbit:
Checkedout code that was deployed to prod based on commit id returned from above

```git checkout $commit-id```
