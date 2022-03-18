# Workstation Setup and Software requiremnts #

Overview
This document walks through how to set up your developer workstation for frontend development.

*TLDR: Requirements*

Node version 14.x

npm version 6.x

facebook watchman


**Install Prerequisite Software**

**Node**

Our applications are tested using the Node version 14.x, so we recommend having this version set as the default node environment on your work computer.

**NVM**

nvm is our recommended approach for managing your local node environment. Please note that nvm is different than npm.

nvm installation instructions can be found here: https://github.com/nvm-sh/nvm#install--update-script 


Use the following command to install nvm:

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash


If you are using nvm to manage your node installation, you can run the following command to install this node version:

*nvm install 14.19.1*


You can then run the following command to make this your default environment:

*nvm alias default 14.19.1*


NPM
We recommend to check your npm version via `npm -v` if u did not see version 6.14.8, then run the global install on the following npm version, as it was the most recently tested version to to have worked correctly with our generators:

*npm install -g npm@6.14.8*


Yeoman
Please reference our article: Yeoman Generator

*npm install -g yo*

Install Developer Software:
Install Facebook watchman: https://facebook.github.io/watchman/

For Windows10 (As of 4/2021): Watchman is in beta phase, it require several extra steps detail can be found here (You may also need to request access from AskIT to add path into your environment config). Also note that to pick a watchman version that has windows bin file, latest version may not have it! For example, here is an older version has windows bin content. 

Macbook: brew install watchman




Windows 10 Additional Step(s)
After you installed nodejs successfully on a windows machine, you will want to setup windows-build-tools in npm to avoid any build errors (i.e. node-sass).

Executing the following to ensure installation success (and yes, make sure you are running AS ADMINISTRATOR and inside a Windows PowerShell Terminal, then do run BOTH IN FOLLOWING ORDER!):

npm install --global --production windows-build-tools@4.0.0
npm install -g --production windows-build-tools

AND! Not done yet!  If you still encounter node-sass issue, it could be windows-build-tool says it installed python, but it actually did NOT.

How we know that is by checking if you have `C:\Python27` listed in your hard drive. If its missing, likely that's the issue.

So you need to head to official site, redownload the official one and do a "repair" or install and once its done. (i.e. 2.7.15, or whichever version you see listed in your windows programs list)

Now! One last step! head to https://developer.microsoft.com/en-us/windows/downloads/sdk-archive/ to download either latest or  Windows SDK version 10.0.17763.0 (as of 4/2021) to ensure lib-sass lib will be installed correctly later on.

Make sure restarted your IDE so terminal is restarted with new config, then node-sass should install successfully after!


Confirm Node and NPM Installation
From a command shell type the following commands and verify you have installed the correct versions.

node --version
npm --version


You can find more info on Node here:  https://nodejs.org/en/download/


Recommended:  
IDE: Any IDE will work..however, our team preference is VS Code.
Install Visual Studio Code: https://code.visualstudio.com/
Visual Studio Code Extension to Refactor JS Glean: https://marketplace.visualstudio.com/items?itemName=wix.glean