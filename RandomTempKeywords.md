# Introduction #

For producing random keywords for temporary password

[http://songketmail.harisfazillah.info/2009/09/random-temporary-keywords-for-bash.html](http://songketmail.harisfazillah.info/2009/09/random-temporary-keywords-for-bash.html)

Problem copying? Visit downloads. random-alpanum.sh

# Details #

```

#!/bin/bash

# Macro for generating an environment variable (%1) with %2 random characters
# from gforge RPM spec gforge.spec
# http://gforge.org/gf/
# Start of the original code. Only work in RPM macro

# %define randstr() %1=`perl -e 'for ($i = 0, $bit = "!", $key = ""; $i < %2; $i++) {while ($bit !~ /^[0-9A-Za-z]$/) { $bit = chr(rand(90) + 32); } $key .= $bit; $bit = "!"; } print "$key";'`

# %randstr GFPASS 8
# echo $GFPASS

# End of the original code. Only work in RPM

# for this shell script. Amend to be suitable.


RANDSTR=`perl -e 'for ($i = 0, $bit = "!", $key = ""; $i < 8; $i++) {while ($bit !~ /^[0-9A-Za-z]$/) { $bit = chr(rand(90) + 32); } $key .= $bit; $bit = "!"; } print "$key";'`

echo "Using perl random keywords -> $RANDSTR "

# Harisfazillah Jamel
# http://linuxmalaysia.harisfazillah.info/
# License GPL v2
# 27 Sept 2009
# Im using this to create temporary random password for installer script.
# refer http://www.tldp.org/LDP/abs/html/index.html

# Using RANDOM in BASH
# one bug. NOMBOR = 0 will produce no value for $AYAT, shorten the lenght -1

ALPANUM=abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890
SIZEP=8
RANGE=62

# Start of loop
i=1

while [ "$i" -le $SIZEP ]
do

NOMBOR=$RANDOM
let "NOMBOR %= $RANGE"
  i=$(($i+1))

HURUF=`expr substr $ALPANUM $NOMBOR 1`
AYAT=`echo $AYAT$HURUF`

done

echo "Using BASH RANDOM random keywords -> $AYAT"

exit 0

```