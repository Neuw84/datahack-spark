# datahack-spark

Vagrant box for the Spark [Datahack](https://www.datahack.es) module. This box uses Ansible as local provisioner.

Contains:

---

    * Apache Zeppelin 0.7.3
    * Apache Spark 2.2.1
    * Python (sci-kit, pandas, numpy, matplotlib, etc)

Please use this with at least **8GB** of Ram and **2** processors on the host machine.

The default user/password for Apache Zeppelin is ```admin/admin```.

## Requisites

* VirtualBox 5.0+
* Vagrant 2.0 +

## Usage

* Install Vagrant <https://www.vagrantup.com/>, Vagrant will install for you VirtualBox if it isn't installed.
* ```git clone``` (**Windows users before cloning:** ```git config --global core.autocrlf input```) or download the [latest](https://github.com/Neuw84/datahack-spark/releases) release
* ```vagrant up``` then wait some minutes.
* Open: <http://spark:8080>
