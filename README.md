# fcrepo4-vagrant-base-box
This is a base box for the [Fedora 4 Vagrant Virtual Machine](https://github.com/fcrepo4-exts/fcrepo4-vagrant). A packaged box lives on [atlas](https://atlas.hashicorp.com/fcrepo/fcrepo4-base).

## Requirements

* [Vagrant](https://www.vagrantup.com/)
* [VirtualBox](https://www.virtualbox.org/)

## Usage

1. `git clone https://github.com/fcrepo4-exts/fcrepo4-vagrant-base-box.git`
2. `cd fcrepo4-vagrant-base-box`
3. `vagrant up`

You can shell into the machine with `vagrant ssh` or `ssh -p 2222 vagrant@localhost`

## Environment

* Ubuntu 14.04 64-bit machine with: 
  * [Tomcat 7](http://tomcat.apache.org)
    * Available at:  [http://localhost:8080](http://localhost:8080)
    * Manager username = "fedora4", password = "fedora4"
  * [Solr 4.10.3](http://lucene.apache.org/solr/)
    * Available at: [http://localhost:8080/solr](http://localhost:8080/solr), for indexing & searching your content.
    * Installed in `/var/lib/tomcat7/solr`
  * [Apache Karaf](http://karaf.apache.org/)
    * Installed in `/opt/karaf`
    * Installed as a service `apache-karaf` 
  * [Fuseki 2.3.0](http://jena.apache.org/documentation/fuseki2/)
    * Available at: [http://localhost:8080/fuseki](http://localhost:8080/fuseki), for querying and updating.
    * Installed in `/etc/fuseki`
    * Dataset Path name `/test`
    * Persistent storage `/etc/fuseki/databases/test\_data`

###Usage

* Install Vagrant and VirtualBox
* Clone this repository 
* `cd fcrepo4-vagrant-base-box`
* `vagrant up`

### How to build base box for Hashicorp

To create a base box to use with Atlas the basic steps are as follows: 

- Clone the repo 
 - `git clone https://github.com/fcrepo4-exts/fcrepo4-vagrant-base-box`
 - `fcrepo4-vagrant-base-box`
- Provision the VM
 - `vagrant up`
- Shutdown the VM
- - `vagrant ssh`
  - `sudo shutdown -P now`
- Export the VM to a box file 
 - `vagrant package`
- [Create a new version on atlas](https://atlas.hashicorp.com/fcrepo/boxes/fcrepo4-base/versions/new)
- Add a provider (virtualbox)
- Upload box

## Support

### Windows Troubleshooting

If you receive errors involving `\r` (end of line):

Edit the global `.gitconfig` file, find the line:
```
autocrlf = true
```
and change it to
```
autocrlf = false
```
Remove and clone again. This will prevent windows git clients from automatically replacing unix line endings LF with windows line endings CRLF.

## Maintainers

Current maintainers:

* [Nick Ruest](https://github.com/ruebot)
* [Jared Whiklo](https://github.com/whikloj)

## Thanks

This VM setup was heavily influenced (read: stolen) from [Islandora 2.x VM](https://github.com/Islandora-Labs/islandora/tree/7.x-2.x/install).
