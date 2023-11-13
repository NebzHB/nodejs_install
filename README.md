Require to be launched by a script containing :
1. the inclusion lib
2. the wget of this file
3. the installVer as first parameter
4. an apt-get update before launch
5. pre-required packages already installed (nodejs required packages will be installed by this script)
6. this script take care of percents from 10 to 50

```
#!/bin/bash
######################### INCLUSION LIB ##########################
BASEDIR=$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )
wget https://raw.githubusercontent.com/NebzHB/dependance.lib/master/dependance.lib -O $BASEDIR/dependance.lib &>/dev/null
PLUGIN=$(basename "$(realpath $BASEDIR/..)")
. ${BASEDIR}/dependance.lib
##################################################################
wget https://raw.githubusercontent.com/NebzHB/nodejs_install/main/install_nodejs.sh -O $BASEDIR/install_nodejs.sh &>/dev/null

installVer='16' 	#NodeJS major version to be installed

pre
step 0 "Vérifications diverses"


step 5 "Mise à jour APT et installation des packages nécessaires"
try sudo apt-get update
try sudo DEBIAN_FRONTEND=noninteractive apt-get install -y exemple_package_needed_after_step_50

#install nodejs, steps 10->50
forceUpdateNPM=1 #sinon garde la version installée par nodeSource
. ${BASEDIR}/install_nodejs.sh ${installVer}

step 60 "La suite"

step 70 "suite"

step 80 "suite encore"

step 90 "nettoyage final"
post
```

# Added error handlers :

 npm `EINTEGRITY`

 npm `npm ERR! fatal: could not create leading directories of '/root/.npm/_cacache/tmp/'`

 npm `ENOTEMPTY` for homebridge-gsh, homebridge-alexa and homebridge-camera-ffmpeg
