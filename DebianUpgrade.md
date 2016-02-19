# Debian Upgrade Notes

- Debian Versions:
    - Debian 8 "jessie"
        - PHP 5.3.3-7
    - Debian 7 "wheezy"
        - PHP 5.4.45
    - Debian 6 "squeeze"
        - PHP 5.6.17


Upgrade from squeeze to wheezy; including PHP.

What other packages are held back besides PHP?

131.146 on wheezy (vmmic?)

Blue background is ready to go. Specify time when to start it.

> How much time is the upgrade going to take? Touch base on Friday.

> Clone nest and do the wheezy upgrade on it. How did it work?

A useful list of upgrade instructions.
https://www.howtoforge.com/how-to-upgrade-debian-squeeze-to-wheezy

## Upgrading my Vagrant Box

This is the process I went through on my own vagrant box.

**Get Squeeze up to Date**

First, we need to make sure everything in squeeze is up to date.

```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

Everything still works, as expected, after those updates. The PHP version
is the following. I've also verified that this matches on stage.

```
PHP 5.3.3-7+squeeze19 with Suhosin-Patch (cli) (built: Feb 17 2014 10:10:23) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies
```

**Verify Packages Are Not on Hold**

At this point I checked to make sure that no packages were on hold and they 
were not. As a side note, however, I do remember the PHP version and one other
component being held back to a previous version somewhere somehow. I can't 
find that as of right now.

```
dpkg --audit
dpkg --get-selections | grep hold
```

After that I ran `aptitude` and hit `q` just to make sure it says `No packages
are scheduled`. If we see that message, we can proceed with the upgrade.

**Upgrade to Wheezy**

Next, I edited the `/etc/apt/sources.list` file to contain the following lines 
(and only these lines).

```
deb http://ftp.us.debian.org/debian/ wheezy main
deb-src http://ftp.us.debian.org/debian/ wheezy main

deb http://security.debian.org/ wheezy/updates main
deb-src http://security.debian.org/ wheezy/updates main

deb http://ftp.us.debian.org/debian/ wheezy-updates main
deb-src http://ftp.us.debian.org/debian/ wheezy-updates main
```

Now we need to get apt up to date with our changes to the sources above.

```
apt-get update
```

This results in some errors that say `There is no public key available`. I ran 
the following to install the appropriate keys and remove those errors.

```
sudo aptitude install debian-keyring debian-archive-keyring
```

Remove the following extra references to other squeeze packages and pinnings. 
These are the ones I mentioned previously that I could not find at the time.

```
rm /etc/apt/preferences.d/preferences
rm /etc/apt/sources.list.d/backports.list
rm /etc/apt/sources.list.d/saltstack.list
```

All of KSL still seems to work at this point and we're ready to do the actual
meat of the upgrade. Start with getting all the squeeze packages up to date 
(again) by running the following command.

```
apt-get upgrade
```

As part of the upgrade I installed the package maintainer's version of 
/etc/sudoers. This will break the admin user in Vagrant. If you are SSH'ed as 
root at the moment you can fix it manually after the upgrade by running `visudo` 
and adding the following line.

```
%admin ALL=NOPASSWD: ALL
```

And, finally, here's the larger command that will upgrade from squeeze to 
wheezy.

```
apt-get dist-upgrade
```

**Dependency Error**

At this point you may get a dependency error. If so, you'll want to remove the 
nfs-common package and then install it again after the upgrade. When this is 
removed you can't use the typical vagrant mounts. So, lets start by taking
down the vagrant box.

```
vagrant halt
```

Now open the `Vagrantfile` and comment out the following lines.

```
config.vm.share_folder "ksl_root", "/var/www/ksl", FILEBASEPATH + "/ksl", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "ksl_api", "/var/www/ksl-api", FILEBASEPATH + "/ksl-api", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "ksl_global", "/var/www/ksl-global", FILEBASEPATH + "/ksl-global", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "ksl_header", "/var/www/ksl-header", FILEBASEPATH + "/ksl-header", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "dado", "/var/www/dado", FILEBASEPATH + "/dado", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "simp", "/var/www/simp", FILEBASEPATH + "/simp", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "xtree", "/var/www/xtree", FILEBASEPATH + "/xtree", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "ddm_framework", "/var/www/framework", FILEBASEPATH + "/framework", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "its", "/var/www/its", FILEBASEPATH + "/its", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "m_ksl_cars", "/var/www/m-ksl-cars", FILEBASEPATH + "/m-ksl-cars", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "m_ksl_homes", "/var/www/m-ksl-homes", FILEBASEPATH + "/m-ksl-homes", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "m_ksl_jobs", "/var/www/m-ksl-jobs", FILEBASEPATH + "/m-ksl-jobs", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
config.vm.share_folder "nest", "/var/www/nest", FILEBASEPATH + "/nest", type: "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc' ,'actimeo=2']
```

Fire vagrant up again.

```
vagrant up
```

Remove the nfs-common package.

```
apt-get remove nfs-common
```

Do the upgrade, again.

```
apt-get dist-upgrade
```

When the upgrade is complete, install nfs-common again.

```
apt-get install nfs-common
```

After this, I confirmed the PHP version matches the one I expect for wheezy by 
running `php --version` again.

```
PHP 5.4.45-0+deb7u2 (cli) (built: Oct 17 2015 08:26:31) 
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2014 Zend Technologies
```

Put your `Vagrantfile` back in order by uncommenting the lines that you 
commented before upgrading nfs-common.

Reboot your vagrant box and you should be done.

```
vagrant reload
```

**Fix Mongo and XTree**

In order to get mongo working again I had to use pecl to uninstall and then 
reinstall the driver.

```
pecl uninstall mongo
pecl install mongo
```

Next, xtree is broken. You'll probably want to clone it so you have access
to it on the vagrant box. You'll need the `php5.4` branch. Then the basic 
procedure for compiling it is:

```
cd xtree
phpize
./configure
make -j 4
make install
service apache2 restart
```


## Nest Server

The nest server probably doesn't have a lot of changes to be made. The first 
one, however, is xtree. Do the following to get the new version of xtree 
installed on nest.

```
phpize                      # PHP utility that will generate configure script
./configure --enable-xtree  # Creates make files
make                        # Compile
sudo make install
```

For me, this results in an xtree.so file in the `/usr/lib/php5/20100525/`
directory. Next, edit the `php.ini` file.

```
vi /etc/php5/apache2/php.ini
```

Add the following line.

```
extension=xtree.so
```

Restart apache with `apachectl restart` and xtree should be loaded.


## m-ksl-cars

This seems to mostly work but I've only just browsed a couple pages.


## ksl

There are a lot of warnings on general classifieds. As such, I had to disable 
them by adding `~E_NOTICE` to the php.ini on the `error_reporting` line.

**Call-time pass-by-reference has been removed**

This error appears in the listing page for general.

```
Fatal error: Call-time pass-by-reference has been removed in 
/var/www/ksl/logic/classifieds/featured_filler.php on line 183
```


## m-ksl-jobs

Jobs needs a symlink fixed (this is not specific to the upgrade). Hoopes 
mentioned that he would fix this but you can run the following command to 
fix it in your environment if necessary. Without this symlink you'll get a 
*forbidden* error when you visit ksl.com/jobs.

```
ln -s /var/www/m-ksl-jobs/
```


## Warnings on Live

The following warnings come out on vmmic04.ksl.com when running the command 
`php --version`. These are part of the problem that we need to fix.

```
PHP Warning:  Module 'memcache' already loaded in Unknown on line 0
PHP Warning:  PHP Startup: apc.shm_size now uses M/G suffixes, please update your ini files in Unknown on line 0

Deprecated: Directive 'register_globals' is deprecated in PHP 5.3 and greater in Unknown on line 0

Deprecated: Directive 'magic_quotes_gpc' is deprecated in PHP 5.3 and greater in Unknown on line 0
```

## Nest Code Fixes

