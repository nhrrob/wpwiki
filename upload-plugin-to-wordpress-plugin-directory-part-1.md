# You don't need Tortoise SVN. Just use CLI

## 1 Upload Plugin to WordPress Plugin Directory | Manual Deploy using SVN CLI

<br/>Date: February 15, 2024 <br/>

Ref:
- https://developer.wordpress.org/plugins/wordpress-org/how-to-use-subversion/
- https://developer.wordpress.org/plugins/wordpress-org/plugin-assets/

### Basic Info
#### Account Details
- Credentials are same as WordPress.org. [Use username. Not email]

<br>

#### SVN Folders
- Checkout means clone. Check in means push.
- Folders: 
```
- /assets/
- /tags/
- /trunk/
```

<br>

#### Assets Folder
- For screenshots, plugin headers, and plugin icons.
- Works for all versions of your plugin. 
- Images are served through a CDN and cached heavily. May take minutes to 6hrs max to update.

<br>

#### Tags Folder
- Plugin versions/releases go in /tags/ folder. 
- Examples: /tags/1.0, /tags/1.1 etc.

<br>

#### Trunk Folder
- Latest code on trunk. Later you can copy this folder into a version folder under /tags.
- Do not put your main plugin file in a subfolder of trunk, like /trunk/my-plugin/my-plugin.php

<br>

#### Default Image Sizes
Banner
- Normal: banner-772x250.(png|jpg) (4MB max)
- HD: banner-1544x500.(jpg|png)

Icons
- Normal: icon-128x128.(png|jpg) (1MB max)
- HD: icon-256x256.(png|jpg)

Screenshots
- screenshot-1.(png|jpg) (10MB max)
- screenshot-2.(png|jpg)

<br>

#### Issues
- Images are downloading when people click, It’s due to Image Content-Type application/octet-stream
- To fix globally, add below code in ~/.subversion/config
```
*.png = svn:mime-type=image/png
*.jpg = svn:mime-type=image/jpeg
```

<br>


### Steps (Starting a New Plugin | SVN Commands)

### Step 1. Create Local Directory
- First create a local directory on your machine to house a copy of the SVN repository: 
```
mkdir my-local-dir
```

<br>


#### Step 2. Clone Pre-Built Repository
- Check out the pre-built repository
```
svn co https://plugins.svn.wordpress.org/your-plugin-name my-local-dir
```

<br>

#### Step 3. Copy Plugin to Trunk
- Copy paste plugin files to trunk folder
- Now, add trunk folder in SVN 
```
cd my-local-dir
svn add trunk/*
```

<br>

#### Step 4. Push Code to SVN
- Check In (From my-local-dir folder)
```
svn ci -m 'Adding first version of my plugin'
```
- If access denied use credentials
```
svn ci -m 'Adding first version of my plugin' --username your_username --password your_password
```
<br>

#### [Future] Step Extra. Edit Existing File
- First go into your your local copy of the repository and make sure it’s up to date.
```
cd my-local-dir/
svn up
```
- After edit, check status and changes of local copy:
```
svn stat
svn diff
```
- Now push
```
svn ci -m "fancy new feature: now you can foo *and* bar at the same time"
```
- Tag and check in again
```
svn cp trunk tags/2.0
svn ci -m "tagging version 2.0"
```

<br>

### We are done!

- Congratulations! You have successfully completed "Upload Plugin to WordPress Plugin Directory | Manual Deploy using SVN CLI"

<br>


### Bonus:
- TBA

<br>


### <a href='https://github.com/nhrrob/wpwiki'>Back to WP Wiki</a>
