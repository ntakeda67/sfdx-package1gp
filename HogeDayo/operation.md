# setup project
## 1. convert from an unmanaged package 

```
sfdx force:project:create -n HogeDayo --template standard
mkdir hogepkg
sfdx force:package1:version:list -i 0330I0000006hbW -u n.takeda67+sf@gmail.com
sfdx force:mdapi:retrieve -r hogepkg -p HogePackage2  -u n.takeda67+sf@gmail.com
# unzip downloaded file
sfdx force:mdapi:convert --rootdir ../hogepkg/HogePackage2
```

## 2. create scratch org installed the package.
```
sfdx force:org:create -f ./config/project-scratch-def.json -a devHoge13
sfdx force:org:open -u devHoge13
sfdx force:source:convert -r force-app/main/default/ -d mdformat
sfdx force:mdapi:deploy -u devHoge13 -d mdformat -w 2 --verbose

sfdx force:source:push -u devHoge13

sfdx force:package1:version:create -i 0330I0000006hbW -d "HogeDayo From SFDX" -k p@ss1234 -n HogeSfdxVersion -r "http://example.com?q=relasenote" -p "http://example.com?q=postinstall" -v "1.3" - u n.takeda67+sf@gmail.com"
```