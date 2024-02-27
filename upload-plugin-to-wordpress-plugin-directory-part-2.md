## 2 Upload Plugin to WordPress Plugin Directory | Auto Deploy using Github Actions

<br/>Date: February 26, 2024 <br/>

Ref:
- https://github.com/10up/action-wordpress-plugin-deploy
- https://github.com/10up/action-wordpress-plugin-asset-update

### Github Action - WordPress Plugin Deploy (by 10up)
#### Action Info
- Action Repo: https://github.com/10up/action-wordpress-plugin-deploy
- This action commits contents of your Git tag to the WordPress.org plugin repository using the same tag name.
- It exclude files using .distignore. 
- Moves plugin icons/assets from your-github-repo/.wordpress-org to svn-repo/assets folder.
- Required Github Secrets (from repo settings)
```
SVN_USERNAME
SVN_PASSWORD
```
- Optional Environment Variables
```
SLUG - If repo and plugin slug is different
```
<br>

#### Create an Action to Auto Deploy
- We will create a github action to auto deploy from github to org (using 10up's action).
- Our github action location: your-github-repo/.github/workflows/{deploy-on-pushing-a-new-tag.yml}

<br>

#### Sample .distignore 
``` 
/.wordpress-org
/.git
/.github
/node_modules

.distignore
.gitignore
```

<br>

#### Example : Deploy on Publishing Tag
- https://github.com/10up/action-wordpress-plugin-deploy/blob/develop/examples/deploy-on-pushing-a-new-tag.yml 

<br>


### Github Action - WordPress Plugin Asset Update (by 10up)

#### Action Info
- Action Repo: https://github.com/10up/action-wordpress-plugin-asset-update
- This Action commits any readme and WordPress.org-specific assets changes in your specified branch (e.x. trunk) to the WordPress.org plugin repository
- Useful for updating things like screenshots or Tested up to separately from functional changes 
- This Action also attempts to parse out the stable tag from your readme and deploy to there as well as trunk. 
- If your stable tag is trunk or a tag that does not exist in the tags subfolder, it will skip that part of the update and only update trunk and/or assets.
- Required Github Secrets (from repo settings)
```
SVN_USERNAME
SVN_PASSWORD
```
- Optional Environment Variables
```
SLUG - If repo and plugin slug is different
IGNORE_OTHER_FILES - if true, then only readme and asset folder (your-github-repo/.wordpress-org) will be deployed
```

<br>

#### Sample Code (Our Github Action / Workflow File)
- Maintain a separate branch (e.x. trunk) for readme and asset changes. Keep it up to date with the latest release.
- Our github action location: your-github-repo/.github/workflows/{deploy-readme-asset-on-pushing-on-trunk.yml}
- Sample code
```
name: Plugin asset/readme update
on:
  push:
    branches:
    - trunk
jobs:
  trunk:
    name: Push to trunk
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: WordPress.org plugin asset/readme update
      uses: 10up/action-wordpress-plugin-asset-update@stable
      env:
        SVN_PASSWORD: ${{ secrets.SVN_PASSWORD }}
        SVN_USERNAME: ${{ secrets.SVN_USERNAME }}
```

<br>

### We are done!

- Congratulations! You have successfully setup Upload Plugin to WordPress Plugin Directory | Auto Deploy using Github Actions 

<br>


### Bonus:
- TBA

<br>


### <a href='https://github.com/nhrrob/wpwiki'>Back to WP Wiki</a>