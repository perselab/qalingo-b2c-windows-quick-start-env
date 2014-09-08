qalingo-b2c-windows-quick-start-env
===================================

Quick start env over Windows 7

Development tools:
- Eclipse is used in this document (Juno version)
- Eclipse plugins: eGit, m2e-wtp
- Server: Apache server, Tomcat servers, MySQL Server
- Tool: Maven

Setup MysQL Server:
- Make sure your root account password is root.

Setup development environment:
- Install plugins: eGit, m2e-wtp to your Juno Eclipse
- Clone git projects to your local by using eGit
- Fow ex, you have:
	Parent folder (0)
	+ qalingo-b2c-engine (1)
	+ qalingo-b2c-i18n (2)
	+ qalingo-b2c-shared (3)
	+ qalingo-b2c-web-classic-fo-bo (4)
	+ qalingo-b2c-windows-quick-start-env (5)
- Go to (5)/qalingo/workspace and copy the pom.xml file to (0)
- Now we have:
	Parent folder (0)
	+ qalingo-b2c-engine (1)
	+ qalingo-b2c-i18n (2)
	+ qalingo-b2c-shared (3)
	+ qalingo-b2c-web-classic-fo-bo (4)
	+ qalingo-b2c-windows-quick-start-env (5)
	+ pom.xml
- Open Eclipse, use Import Maven Project action, go to (0) and do import
- Open Eclipse Preference, change the maven settings to file: (5)/qalingo/tools/Maven_m2_conf/settings.xml
- Modify file: (5)/qalingo/tools/Maven_m2_conf/settings.xml
	fo.mcommerce.velocity.www.pages.path: to your qalingo-assets-mcommerce-pages default theme
	wurfl.xml.path                      : to (5)/qalingo/workspace/misc/wurfl/wurfl.zip
- Now, you are able to build the project. Choose the qalingo/pom.xml and run with goals: clean install and profile is dev-qalingo

Setup Apache server:
- Just overwrite the file apache/conf/httpd.conf by (5)/qalingo/servers/Apache_conf/httpd.conf or you can merge by yourself
- Open the file Windows/system32/drivers/host to add the below:
	127.0.0.1 fo-mcommerce.dev.qalingo.com fo-prehome.dev.qalingo.com rest-remote.dev.qalingo.com 
	127.0.0.1 bo-business.dev.qalingo.com bo-reporting.dev.qalingo.com bo-technical.dev.qalingo.com
	
Setup Tomcat mcommerce server:
- Download and unzip the Tomcat 7
- Create folder: ~tomcat7/conf/Catalina/localhost/
- Copy 2 files: (5)qalingo/servers/Tomcat/contexts/fo-mcommerce.xml, (5)qalingo/servers/Tomcat/contexts/fo-mcommerce-resources.xml to previous step

Setup BAT command:
- Modify (5)/qalingo/env.bat
	WORKSPACE_HOME: to (0)
	HOME          : to (0)
	The other tools should be pointed to correct location.
- Modify (5)/qalingo/server-tomcat-startup-frontoffice-mcommerce.bat
	CATALINA_HOME: to your tomcat7 location
	PROJECT_PATH: to your qalingo-b2c-web-classic-fo-bo project
	
Run:
- Run the apache first
- Run the tomcat by command: (5)/qalingo/server-tomcat-startup-frontoffice-mcommerce.bat
- Open file: (1)/sites_urls.html
- Open link: >> {Q}alingo - Frontoffice mCommerce (Apache)


All the documentation is here: http://docs.qalingo.org

