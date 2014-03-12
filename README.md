Magento on OpenShift
====================

This git repository creates a Magento installation on OpenShift.

Sample data is populated and the application configured automagically.

Running on OpenShift
----------------------------

Create an account at http://www.openshift.com/

Create a php-5.3 + mysql 5.1 application based on this repo's code (you can call your application whatever you want)

    rhc app create $appname php-5.3 mysql-5.1 --from-code=https://github.com/openshift/magento-example

That's it, you can now checkout your application at:

    http://$appname-$yournamespace.rhcloud.com

Default admin credentials: username _admin_ password _OpenShiftAdmin123_.

### Post-installation details

After the installation it is important to change the admin password and other Magento configurations properly. Log in to 

    http://$appname-$yournamespace.rhcloud.com/admin

using the provided credentials and check all system settings, for example:

 * System > My Account
 * System > Configuration > General > Countries Options
 * System > Configuration > General > Locale Options
 * System > Configuration > Admin
 * System > Configuration > System
 
