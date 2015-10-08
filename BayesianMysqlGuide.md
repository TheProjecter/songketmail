# Bayesian SpamAssassin MySQL SPEC RPM #

Internet links :

http://songketmail.wiki.sourceforge.net/bayesian-mysql

http://code.google.com/p/songketmail/wiki/BayesianMySql

This documentation need to refer to files residing in BayesianMySql at SongketMail Project Wiki. This RPM will configure Spamassassin to used Bayesian with MySql. This document refer to bayesian-mysql version 0.0.1. This version is tested using MySql 5.0.22 and spamassassin 3.1.9.

SPEC RPM can be found here
http://songketmail.wiki.sourceforge.net/bayesmysql-specrpm

http://code.google.com/p/songketmail/wiki/BayesianMySqlCode

Source to be used with SPEC RPM
http://sourceforge.net/project/showfiles.php?group_id=213253&package_id=257222

http://code.google.com/p/songketmail/downloads/list

Building RPM
http://www.rpm.org/RPM-HOWTO/build.html

## Simple steps ##

(1) Copy the tar.bz2 file to /usr/src/redhat/SOURCE
(2) Copy the above spec file to /usr/src/redhat/SPEC and name it bayesian-mysql.spec
(3) Run rpmbuild -bb /usr/src/redhat/SPEC/bayesian-mysql.spec


You need to install development packages and rpmbuild to build RPM.

This installation is using CentOS 5 as the main Linux Operating System. Your installation may be different with Red Hat and Fedora. Opensuse may vary need to get the right RPM name for the packages.

### (1) Install Packages needed as per CentOS 5. ###

spamassassin, mysql, mysql-server, perl-DBI, perl-DBD-MySQL, perl-Net-Daemon, perl-libwww-perl

or by yum

yum install spamassassin mysql mysql-server perl-DBI perl-DBD-MySQL perl-Net-Daemon perl-libwww-perl

### (2) Start the Mysql Server and create database name bayesianmysql (login as root) ###

mysqladmin create bayesianmysql

Assign the user

GRANT ALL ON bayesianmysql.**to bayesianmysql@localhost identified by 'yourpassword1234';**

Change the password yourpassword1234 to your own.

### (3) Create the tables needed by the database. ###

http://wiki.apache.org/spamassassin/BetterDocumentation/SqlReadme

http://wiki.apache.org/spamassassin/BetterDocumentation/SqlReadmeBayes

http://wiki.apache.org/spamassassin/BetterDocumentation/SqlReadmeAwl

or load the SQL file used by Bayesianmysql SPEC RPM

http://code.google.com/p/songketmail/wiki/BayesianMySqlSkeletonTables
http://songketmail.wiki.sourceforge.net/bayesianmysql-sql

mysql -p -u bayesianmysql bayesianmysql < nameofsqlfile.sql

### (4) Copy 2 spamassassin cf files to /etc/mail/spamassassin ###

Get the file name bayesian-mysql.cf

http://songketmail.wiki.sourceforge.net/bayesian-mysql.cf

http://code.google.com/p/songketmail/wiki/BayesianMySqlCf

and file name bayesian-mysql-mysql.cf

http://code.google.com/p/songketmail/wiki/BayesianMysqlSpamassassinCf

http://songketmail.wiki.sourceforge.net/bayesian-mysql-mysql.cf

Remember to change password as per your site or item 2.

### (5) You need at least to trained spamassassin one ham and spam email using sa-learn. ###

Spamassassin Public Corpus can be used if you don't have any examples.

http://spamassassin.apache.org/publiccorpus/

http://spamassassin.apache.org/publiccorpus/readme.html

The command :-

http://spamassassin.apache.org/full/3.1.x/dist/doc/sa-learn.html

sa-learn --ham hamemail.txt
sa-learn --spam spamemail.txt

### (6) Finishing the setup ###

Sync the dataset

sa-learn --sync --force-expire

Update the rules

sa-updates

Run the LINT test

spamassassin --lint -D

Watch the debug output from spamd and look for the following debug
line:

debug: bayes: Database connection established
debug: bayes: Using username: 

&lt;username&gt;



Forum and discussion

http://sourceforge.net/forum/?group_id=213253
http://groups.google.com/group/songketmail

Blog

http://songketmail.harisfazillah.info/


Harisfazillah Jamel for SongketMail
version 1.0
12 Jan 2008