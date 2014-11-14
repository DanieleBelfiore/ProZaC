#ProZaC - Proxy Zabbix Ceilometer


##Objective
This project started as a way to integrate monitoring information collected in a Cloud environment, namely by OpenStack's Ceilometer, integrating it with an already existing monitoring solution using Zabbix.

##Features
* Integration of OpenStack's available monitoring information (e.g. using Ceilometer) with already existing Monitoring systems (e.g. Zabbix);
* Automatically gather information about the existing Cloud Infrastructure being considered (tenants, instances);
* Seamlessly handle changes in the Cloud Infrastructure (creation and deletion of tenants and/or instances);
* Periodically retrieve resources/meters details from OpenStack;
* Allow to have one common monitoring system (e.g Zabbix) for several OpenStack-based Cloud Data Centres.

##Requirements
ProZaC was written using _Python_ version 2.7.5 but can be easily ported to version 3. It uses the Pika library for support of AMQP protocol towards RabbitMQ, one of the messaging systems used by OpenStack.

For installing Pika, if you already have _Python_ and the _pip_ packet manager configured, you need only to use a terminal/console and simply run:

		sudo pip install pika

Otherwise, you might check whether pika is available in the software repositories of your distribution, i.e.
	        sudo yum install python-pika 
		sudo apt-get install python-pika

If the previous command fails, download and manually install the Pika library on the host where you intend to run the ProZaC:

* https://github.com/pika/pika
* http://pika.readthedocs.org/en/latest/

**Note:** Since the purpose of this project is to be integrated with OpenStack and Zabbix it is assumed that apart from a running installation of these two, some knowledge of OpenStack has already been acquired.

##Usage
Assuming that all the above requirements are met, ProZaC can be run  with 3 simple steps:

1. On your OpenStack installation point to your Keystone configuration file (keystone.conf) and uncomment the following line:

		notification_driver = keystone.openstack.common.notifier.rpc_notifier

2. Edit the `proxy.conf` configuration file to reflect your own system, including the IP addresses and ports of Zabbix and of the used OpenStack modules (RabbitMQ/QPID, Ceilometer Keystone and Nova). You can also tweak some ZCP internal configurations such as the polling interval, template name and proxy name (used in Zabbix).

3. Finally, run the Zabbix-Ceilometer Proxy!

		service prozac.py start

If all goes well the information retrieved from OpenStack's Ceilometer will be pushed in your Zabbix monitoring system.

##Source
If not doing so already, you can check out the latest version of Prozac through [github](https://github.com/INFN-Catania/ProZaC).

##Copyright

##Credits

ProZaC is a fork of *ZabbixCeilometer-Proxy* of OneSource Consultoria Informatica, Lda. [🔗](http://www.onesource.pt). For further information about the original project, check its [github](https://github.com/clmarques/ZabbixCeilometer-Proxy). 
See ProZaC individual source files for more details about functionalities added after the fork.

##License
Distributed under the Apache 2 license. See ``LICENSE.txt`` for more information.

##About

This work has been supported by INFN, Catania division, in the context of PRISMA project. For further details about PRISMA, check out its [PRISMA website](http://www.ponsmartcities-prisma.it/). 
For more details on ProZaC, or Zabbix consultancy, please contact main author via email **_emidio.giorgio✉️ct.infn.it__**   
