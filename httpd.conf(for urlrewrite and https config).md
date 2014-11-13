##Apache urlrewrite:
http://httpd.apache.org/docs/2.2/rewrite/

##rewrite flags:
http://httpd.apache.org/docs/2.4/rewrite/flags.html

##The important flags:
R: redirect(if the target url is relative path, the server will automaticly add the orginal host and port to new urls), default redirect status is 302(temporary move to an new location, 301 means permanent move to an new location).
L: if current rules matches, no further rules will be processed.
usually R,L used together.

RewriteCond always use with RewriteRule together, one RewriteRule can match one or many condations, append with [OR] or just append line by line.

##build-in variables:
http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html

##VirtualHost:
if there are not only one web applications in the server, the RewriteRule should be configure exactlly within the virtualhost
you wanna configure, otherwise, just simply paste the rules at the end of the httpd.conf will be ok.

##Redirect rules for global scope
When we want to add rules for all of the hosts, we do not have to add the same rules to each of the VirtualHost, just paste redirect rules at the end of the httpd.conf, and in each VirtualHost, specify to inherit the global rules is ok.

e.g:
-- global redirect rules
RewriteEngine On
RewriteRule /buy/?$     /new/buy/product/us/en-us [R,L]

-- in each VirtualHost, we have to config
<VirtualHost localhost:80>
	RewriteEngine On
	RewriteOptions Inherit 
</VirtualHost>

<VirtualHost localhost:443>
	SSLEnable
	RewriteEngine On
	RewriteOptions Inherit 
</VirtualHost>

then the redirect rule will work on both HTTP and HTTPS hosts.

#=====Enable https======
##Reference:
For apache: http://httpd.apache.org/docs/2.4/ssl/

##For IHS: 
http://pic.dhe.ibm.com/infocenter/reqpro/v7r1m0/index.jsp?topic=/com.ibm.rational.reqpro.install_upgrade.doc/topics/t_create_certificate.html
http://pic.dhe.ibm.com/infocenter/reqpro/v7r1m0/index.jsp?topic=/com.ibm.rational.reqpro.install_upgrade.doc/topics/t_create_certificate.html

##Important tips:
Have to commit up below 2 lines:
Listen 0.0.0.0:80
Listen [::]:80

