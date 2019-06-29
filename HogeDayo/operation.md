# setup project
## 1. convert from an unmanaged package 

```
sfdx force:project:create -n HogeDayo --template standard
mkdir hogepkg
sfdx force:mdapi:retrieve -r hogepkg -p HogePackage2 -u n.takeda67+sf@gmail.com
# unzip downloaded file
sfdx force:mdapi:convert --rootdir ../hogepkg/HogePackage2

```