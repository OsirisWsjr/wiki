Apache - basics
===============

  
Here are some basic usages of Apache 2.  
  
**Configuration files**  
  
Drop your custom `.conf` files in to this folder:  
  

    ~/.apache2/conf.d/

  
Then restart Apache.  
  
**Reload Apache configurations:**  
  
This command will reload your `conf` files instead of restarting.  
  
**Important note:** This error below is normal and to be expected when reloading Apache2.  
  

    mkdir: cannot create directory ‘/var/run/apache2’: Permission denied

  
Use this command to reload Apache2:  
  

    /usr/sbin/apache2ctl -k graceful

  
**Important note:** You cannot restart or start Apache, only the system can do that. If you kill the process or it dies you will need to wait up to 5 minutes or it to restart. You can reload the configuration using the above command.  
  
**List loaded modules:**  
  
This will list currently loaded modules that are usable:  
  

    /usr/sbin/apachectl -t -D DUMP_MODULES

  
**List available modules.**  
  
This will list all available modules that you can load:  
  

    ls -1 /etc/apache2/mods-available/

  
**For example. Here is the way you would load the Auth Digest module:**  
  
To load a modules you will need to create and then edit a `~/.apache2/conf.d/some.conf` file and then restart Apache like this:  
  

    nano ~/.apache2/conf.d/digest.conf

  
Now Add this line to the top of the file to load the auth digest module.  
  

    Include /etc/apache2/mods-available/auth_digest.load

  
Save by pressing and holding `CTRL` and then pressing `x` then press `Y` to confirm.  
  
Reload the changes:  
  

    /usr/sbin/apache2ctl -k graceful

  
Test it is loaded: might be near the bottom  
  

    /usr/sbin/apachectl -t -D DUMP_MODULES

  
The error log is found here:  
  

    ~/.apache2/error.log

  
  

