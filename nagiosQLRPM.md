# NagiosQL 2.0.2 RPM For Centos 5 #

In the Internet
http://linuxmalaysia.harisfazillah.info/2008/07/nagiosql-202-rpm-for-centos-5.html

This RPM include nagios 2.11 configuration files that already configure for nagiosQL.

## (A) Introduction ##

This RPM will help you to install NagiosQL 2.0.2. It's tested with Centos 5.2 and should be working with Fedora and Red Hat Enterprise 5. This RPM include nagios 2.11 configuration files that already configure for nagiosQL.

NagiosQL is a web based administration tool for Nagios 2.x. It helps you to easily build a complex configuration with all options, manage and use them. NagiosQL is based on a webserver with PHP, MySQL and file access to the Nagios configuration files.

http://www.nagiosql.org/

It's base on this tutorial
http://nagioswiki.com/wiki/index.php/Nagios_and_NagiosQL_on_CentOS_4.x

## (B) Prerequisites ##

We assume Linux Centos 5.2 already installed. The iso for CD and DVS can be download here

http://www.centos.org/

This packages can installed from Centos repository

  * mysql
  * mysql-server
  * mysql-devel
  * php-mysql
  * httpd
  * php
  * php-pear


The command

```
yum install mysql mysql-server mysql-devel php-mysql httpd php php-pear
```
You need to install nagios 2.11 from rpmforge

Download RPM for nagios, nagios-devel, nagios-plugins, nagios-nrpe and nagios-plugins.

http://dag.wieers.com/rpm/packages/nagios/

http://dag.wieers.com/rpm/packages/nagios-nrpe/

http://dag.wieers.com/rpm/packages/nagios-plugins/

or by Install Rpmforge as you can set rpmforge as one of your computer Centos repository. Please read the manual here

http://dag.wieers.com/rpm/

for centos 5 i386
```
rpm -Uhv http://apt.sw.be/redhat/el5/en/i386/rpmforge/RPMS/rpmforge-release-0.3.6-1.el5.rf.i386.rpm
```
or from
```
rpm -Uvh http://dag.wieers.com/rpm/packages/rpmforge-release/rpmforge-release-0.3.6-1.el5.rf.i386.rpm
```
## (C) Installation ##

Download this rpm nagiosql-2.0.2-1.centos5.noarch.rpm

http://sourceforge.net/project/showfiles.php?group_id=213253&package_id=284427

or from

http://knowledge.oscc.org.my/practice-areas/system-administration/network/nagiosql-rpm/at_download/file

and install with this command
```
yum localinstall nagiosql-2.0.2-1.centos5.noarch.rpm
```
yum localinstall is used to install a set of local rpm files. If required the enabled repositories will be used to resolve dependencies.
```
***** Information **** 
Please change in /etc/php.ini magic_quotes_gpc = On
We don't want to auto script it. We do not know your local php setting
and service httpd restart
 ***** Information **** 
```
You need to reset the admin password for nagios by this command
```
htpasswd /etc/nagios/htpasswd.users admin
```
To access nagios 2.10 from web browser type http://localhost/nagios

To access nagiosQL 2.0.2 from web browser type http://localhost/nagiosQL

## (D) Source ##

The source RPM can be view here

http://knowledge.oscc.org.my/practice-areas/system-administration/network/nagiosql-rpms/view

## (E) Credit ##

Just Do IT Team (JDIT) from http://forum.pmo.gov.my/

Harisfazillah Jamel
http://blog.harisfazillah.info/
16 Jul 2008

Mirror page

http://knowledge.oscc.org.my/practice-areas/system-administration/network/centos-5-rpm-for-nagiosql

http://songketmail.wiki.sourceforge.net/nagiosQL-RPM


Backup For RPM and RPMS
http://code.google.com/p/songketmail/downloads/list