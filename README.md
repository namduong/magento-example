Magento on OpenShift
====================

This git repository creates a Magento installation on OpenShift.

Sample data is populated and the application configured automagically.

Running on OpenShift
----------------------------

Create an account at http://openshift.redhat.com/

Create a php-5.3 + mysql 5.1 application based on this repo's code (you can call your application whatever you want)

    rhc app create $appname php-5.3 mysql-5.1 --from-code=git://github.com/fabianofranz/openshift-magento-example.git --no-git

That's it, you can now checkout your application at:

    http://$appname-$yournamespace.rhcloud.com

Default credentials: username 'admin' password 'OpenShiftAdmin'.