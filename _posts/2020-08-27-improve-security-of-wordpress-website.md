---
layout: post
title: "Improve security of Wordpress web site"
categories: development
tags: php
---

#Improve security of Wordpress web site
Improve security adding rules to .htaccess file

##Protect system files
```
<Files .htaccess>
	<IfModule mod_authz_core.c>
		Require all denied
	</IfModule>
	<IfModule !mod_authz_core.c>
		Order allow,deny
		Deny from all
	</IfModule>
</Files>
<Files readme.html>
	<IfModule mod_authz_core.c>
		Require all denied
	</IfModule>
	<IfModule !mod_authz_core.c>
		Order allow,deny
		Deny from all
	</IfModule>
</Files>
<Files readme.txt>
	<IfModule mod_authz_core.c>
		Require all denied
	</IfModule>
	<IfModule !mod_authz_core.c>
		Order allow,deny
		Deny from all
	</IfModule>
</Files>
<Files wp-config.php>
	<IfModule mod_authz_core.c>
		Require all denied
	</IfModule>
	<IfModule !mod_authz_core.c>
		Order allow,deny
		Deny from all
	</IfModule>
</Files>
<Files wp-login.php>
	Order Deny,Allow
	Deny from all
	Allow from IP_ADDRESS
</Files>
```

##Hide internal path
```
RewriteRule ^wp-admin/install\.php$ - [F]
RewriteRule ^wp-admin/includes/ - [F]
RewriteRule !^wp-includes/ - [S=3]
RewriteRule ^wp-includes/[^/]+\.php$ - [F]
RewriteRule ^wp-includes/js/tinymce/langs/.+\.php - [F]
RewriteRule ^wp-includes/theme-compat/ - [F]

RewriteCond %{REQUEST_FILENAME} -f
RewriteRule (^|.*/)\.(git|svn)/.* - [F]
```

##Disable PHP files
```
RewriteRule ^wp\-content/uploads/.*\.(?:php[1-7]?|pht|phtml?|phps)$ - [NC,F]
RewriteRule ^wp\-content/plugins/.*\.(?:php[1-7]?|pht|phtml?|phps)$ - [NC,F]
RewriteRule ^wp\-content/themes/.*\.(?:php[1-7]?|pht|phtml?|phps)$ - [NC,F]
```

##Filter Request Methods
```
RewriteCond %{REQUEST_METHOD} ^(TRACE|DELETE|TRACK) [NC]
RewriteRule ^.* - [F]
```

##Disable XML-RPC
```
<Files xmlrpc.php>
	<IfModule mod_authz_core.c>
		Require all denied
	</IfModule>
	<IfModule !mod_authz_core.c>
		Order allow,deny
		Deny from all
	</IfModule>
</Files>
```
