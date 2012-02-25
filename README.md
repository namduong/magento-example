Magento on OpenShift Express
==============================

This git repository helps you get up and running quickly w/ a Magento installation
on OpenShift Express.  It will be a clean installation where you will need to accept
the license agreement as well as configure your database connectivity and configure 
the admin user account.


Running on OpenShift
----------------------------

Create an account at http://openshift.redhat.com/

Create a php-5.3 application (you can call your application whatever you want)

    rhc-create-app -a magento -t php-5.3

Add MySQL support to your application

    rhc-ctl-app -a magento -e add-mysql-5.1

Add this upstream Magento repo

    cd magento 
    git remote add upstream -m master git://github.com/openshift/magento-example.git
    git pull -s recursive -X theirs upstream master
    # note that the git pull above can be used later to pull updates to Magento
    
Then push the repo upstream

    git push

That's it, you can now checkout your application at:

    http://magento-$yournamespace.rhcloud.com


NOTES:

GIT_ROOT/.openshift/action_hooks/deploy:
    This script is executed with every 'git push'.  Feel free to modify this script
    to learn how to use it to your advantage.  By default, this script will create
    the database tables that this example uses.

    If you need to modify the schema, you could create a file 
    GIT_ROOT/.openshift/action_hooks/alter.sql and then use
    GIT_ROOT/.openshift/action_hooks/deploy to execute that script (make sure to
    back up your application + database w/ rhc-snapshot first :) )

The initialization steps will make changes to the files on the server side.  To pull 
those to your local repo, you can run rhc-snapshot -a magento from your client, explode
the resulting tar.gz and pull all the files from magento/repo/php back to your local
magento/php directory.  It's always a good idea to take a snapshot every now and then.
