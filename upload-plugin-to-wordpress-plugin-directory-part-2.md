## 2 Upload Plugin to WordPress Plugin Directory| Auto Deploy using Github Actions

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
- Our github action location: your-repo/.github/workflows/{deploy-on-pushing-a-new-tag.yml}

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

<br>

#### TBA
- TBA

<br>

### We are done!

- Congratulations! You have successfully setup Upload Plugin to WordPress Plugin Directory| Auto Deploy using Github Actions 

<br>


### Bonus:
- TBA

<br>


### <a href='https://github.com/nhrrob/wpwiki'>Back to WP Wiki</a>