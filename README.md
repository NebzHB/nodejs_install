Require to be launch by a script containing :
1. the inclusion lib
2. the wget of this file
3. the installVer as first parameter
4. an apt-get update before launch
5. pre-required packages already installed (nodejs required packages will be installed by this script)

```
#!/bin/bash
######################### INCLUSION LIB ##########################
BASEDIR=$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )
wget https://raw.githubusercontent.com/NebzHB/dependance.lib/master/dependance.lib -O $BASEDIR/dependance.lib &>/dev/null
PLUGIN=$(basename "$(realpath $BASEDIR/..)")
. ${BASEDIR}/dependance.lib
##################################################################
wget https://raw.githubusercontent.com/NebzHB/nodejs_install/main/install_nodejs.sh -O $BASEDIR/install_nodejs.sh &>/dev/null

installVer='12' 	#NodeJS major version to be installed

pre
step 0 "Vérifications diverses"


step 5 "Mise à jour APT et installation des packages nécessaires"
try sudo apt-get update
try sudo DEBIAN_FRONTEND=noninteractive apt-get install -y some_prerequired_packages

#install nodejs, steps 10->50
. ${BASEDIR}/install_nodejs.sh ${installVer}

step 60 "La suite"
```
