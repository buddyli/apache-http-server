#Apache urlrewrite:
http://httpd.apache.org/docs/2.2/rewrite/

#rewrite flags:
http://httpd.apache.org/docs/2.4/rewrite/flags.html

#The important flags:
R: redirect(if the target url is relative path, the server will automaticly add the orginal host and port to new urls).
L: if current rules matches, no further rules will be processed.
usually R,L used together.

#VirtualHost:
if there are not only one web applications in the server, the RewriteRule should be configure exactlly within the virtualhost
you wanna configure, otherwise, just simply paste the rules at the end of the httpd.conf will be ok.

##=====Enable https======
#Reference:
For apache: http://httpd.apache.org/docs/2.4/ssl/

#For IHS: 
http://pic.dhe.ibm.com/infocenter/reqpro/v7r1m0/index.jsp?topic=/com.ibm.rational.reqpro.install_upgrade.doc/topics/t_create_certificate.html
http://pic.dhe.ibm.com/infocenter/reqpro/v7r1m0/index.jsp?topic=/com.ibm.rational.reqpro.install_upgrade.doc/topics/t_create_certificate.html

#Important tips:
Have to commit up below 2 lines:
Listen 0.0.0.0:80
Listen [::]:80
