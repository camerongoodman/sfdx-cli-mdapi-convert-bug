# SFDX-CLI Bug with sfdx:mdapi:convert command

This repo is to demonstrate a bug with the sfdx force:mdapi:convert command not converting CustomLabels.

Tested and recreated in the following

Windows 10/11
- sfdx-cli/7.151.1 win32-x64 node-v14.19.1

Ubuntu 20.04
- sfdx-cli/7.151.1 linux-x64 node-v14.19.2

Issue:  sfdx force:mdapi:convert does not convert CustomLabels to source format.

Steps:
1 - convert original source to mdapi format
    - sfdx force:source:convert -r force-app -d mdapi
2 - observe CustomLabels in mdapi folder and package.xml
3 - convert MDAPI back to SOURCE format
    - sfdx force:mdapi:convert -r mdapi -d src
4 - observe NOTHING was converted, src folder is empty

5 - Use legacy mdapi:convert
     - sfdx force:mdapi:legacy:convert -r mdapi -d src2
6 - Observe legacy convert works as expected.