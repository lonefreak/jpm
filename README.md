# jpm

## Jenkins Plugin Manager


JPM is a command line interface to help in the searching and packaging (RPM) of Jenkins plugins. It's useful if you want to manage your Jenkins plugins yourself instead of using Jenkins' Update Center.

## Installing


```
$ git clone git@github.com:lonefreak/jpm.git
$ cd jpm
$ chmod +x install.sh
$ ./install.sh
```

## Dependencies
To run JPM you will need:
```
fpm (>= 1.1.0)
rpm/rpmbuild (>= 4.8.0)
wget (>= 1.12)
curl (>= 7.19.7)
```
## Usage
```
$ jpm -h
USAGE: jpm [-x PROXY_HOST:PORT] ACTION PLUGIN [VERSION]
ACTION examples:
	jpm package PLUGIN_NAME [PLUGIN_VERSION]	//generates a RPM containing the specified plugin. If no version provided, uses latest
	jpm search PLUGIN_NAME						//searches for a plugin (works with partial names)
	jpm list PLUGIN_NAME						//lists all versions of the given plugin
```
### Searching for a plugin
```
$ jpm search extended
dynamic_extended_choice_parameter
extended-choice-parameter
extended-read-permission
script-realm-extended
```
### Listing versions of plugin
```
$ jpm list extended-choice-parameter
Versions for extended-choice-parameter
0.32
0.31
0.30
0.28
0.27
```
### Packaging 
```
$ jpm package extended-choice-parameter 0.30
##############################
OBTAINING PLUGIN
##############################

Retriving extended-choice-parameter plugin with version 0.30 from
https://updates.jenkins-ci.org/download/plugins/extended-choice-parameter/0.30/extended-choice-parameter.hpi

100%[=====================>] 44,260      95.5K/s   in 0.5s    

##############################
GENERATING RPM
##############################

Created package {:path=>"extended-choice-parameter-0.30-1.noarch.rpm"}

##############################
PROCESS FINISHED!!
##############################
```
## TODO
* using external configurations (.jpmrc)
* sudo usage
* plugin dependency resolution
* include dependencies in the RPM package
