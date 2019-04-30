## Common .htaccess redirects

#### Redirect an entire site:
Redirect 301 / http://www.domain.com/

#### Redirect a single page:
Redirect 301 /pagename.php http://www.domain.com/pagename.html

#### Redirect an entire site to a subfolder
Redirect 301 / http://www.domain.com/subfolder/

#### Redirect a subfolder to another site
Redirect 301 /subfolder http://www.domain.com/

#### Redirect any file with the .html extension to use the same filename but use the .php extension instead.
RedirectMatch 301 (.*)\.html$ http://www.domain.com$1.php

#### Redirect from old domain to new domain with full path and query string:
```
#Options +FollowSymLinks (depends on the server configuration)
Options +FollowSymLinks
RewriteEngine On
RewriteRule ^(.*) http://www.newdomain.com%{REQUEST_URI} [R=302,NC]
```
#### Redirect bare domain to www. domain
```
#Options +FollowSymLinks (depends on the server configuration)
RewriteEngine on
RewriteCond %{HTTP_HOST} ^domain.com [NC]
RewriteRule ^(.*)$ http://www.domain.hu/$1 [L,R=301]
```
#### Redirect www. domain to bare domain
```
#Options +FollowSymLinks (depends on the server configuration)
RewriteEngine on
RewriteCond %{HTTP_HOST} .
RewriteCond %{HTTP_HOST} !^domain\.com
RewriteRule (.*) http://domain.com/$1 [R=301,L]
```
#### Redirect subdomain to a folder
```
#Options +FollowSymLinks (depends on the server configuration)
RewriteEngine On 
RewriteCond %{REQUEST_URI} !^/subdomain
RewriteCond %{HTTP_HOST} ^subdomain.domain.com
RewriteRule (.*) /directory/$1 [L] 
```
#### Redirect subdomain to any domain
```
#Options +FollowSymLinks (depends on the server configuration)
RewriteEngine On
RewriteCond %{REQUEST_URI} ^/m/(.*)$
RewriteRule ^(.*) http://www.dynamic-sport.hu/%1 [R=302,NC]
```
