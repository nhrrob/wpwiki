## #NHRWPWiki

### List of Issues
- Issue 1: Installing plugin requires ftp access 
- Issue 2: Updating wordpress failed due to permission issue

## 

### Issue Solutions

#### Issue 1: Installing plugin requires ftp access 

Solution: 
Add below code in wp-config.php
	<code>define('FS_METHOD','direct');</code>

#### Issue 2: Updating wordpress failed due to permission issue
Error message: 
Could not create directory.
Installation failed.

Solution:
Run below commands form your project root.

```
sudo chown -R www-data:www-data wp-content/plugins/
sudo chmod 775 wp-content

sudo chown -R www-data:www-data wp-content/
```

Ref Link: https://stackoverflow.com/questions/37157264/wordpress-plugin-install-could-not-create-directory 


#### Issue 3: TBA