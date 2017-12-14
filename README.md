# datahack-spark

Vagrant box for the Spark [Datahack](https://www.datahack.es) module. This box uses Ansible as local provisioner.

Contains:

---

    * Zeppelin 0.7.3
    * Spark 2.2.1
    * Python (sci-kit, pandas, numpy, etc.)

Please use this with at least **12GB** of Ram and **2** processors on the host machine

## Requisites

* VirtualBox 5.0+
* Vagrant 2.0 +

## Usage

* Install Vagrant <https://www.vagrantup.com/>, Vagrant will install for you VirtualBox if it isn't installed.
* ```git clone``` (**Windows users before cloning:** ```git config --global core.autocrlf input```).
* ```vagrant up``` then wait some minutes.
* Open: <http://spark:8080>