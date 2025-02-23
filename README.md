# Simulator for Test

Supported Arch: PPC64LE

Install and Start Simulator
---------------------------

* Clone this repo ``git clone git@github.com:gurevichmark/openbmc_simulator.git``

* Run ``./simulator [-c] [-d <delay type> -t <delay time(max)>] [-n <NIC> -r <IP range>]`` 

For Ubuntu OS, please run ``apt-get update`` first

Options
-------

**-c**: Cleanup IPs configuration. If not specified, will setup openbmc simulator environment and start simulator

**-d**: Delay response type, supported parameters: ``random`` and ``constant``.

**-t**: Delay response time, must be used with **-d**. If delay type is ``random``, the parameter specifies the max value. The delay time will be random between 0 and input parameter. Format is "xxmxx"

**-n**: NIC name on which to configure IPs

**-r**: IPs to configure on NIC. The format is as '10.[1|{1.10}].[1|{1..200}].[1|{1..200}]'

Example:

Setup environment and start simulator ``./simulator -n eth0 -r 10.1.1.{1..10}``

Clear environment: ``./simulator -c -n eth0 -r 10.1.1.{1..10}``

Setup environment and start simulator that will delay response ``./simulator -d random -t 10``

Node Definition in xCAT
-----------------------

If the node that simulator runs on as below:

    ip=10.0.0.1
    
You can define the node as below:

    mkdef simulator groups=all bmc=10.0.0.1 mgt=openbmc bmcusername=root bmcpassword=0penBmc

Run Command Against Simulator
-----------------------------

Take ``rpower`` command as example:

    # rpower simulator on
    simulator: on
    
