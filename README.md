# first
this is the first repository. **This** is a repo
# Day1

## RouterOS basic --------

### --xx LAB SETUP xx--
> Use CHR (Cloud Hosted Router) in virtualbox or physical device (hEX/hAP).
> Connect via WinBox (MAC/IP neighbor) or SSH.
    
1. change router identity 
        -> system> identity (winbox)
    **Goal : To manage the routers efficiently** 
2. change time 
        -> system> clock (winbox)
    **Goal : To know the time and manage easily**
3. update routerOS 
        -> /system package update print (current OS version)
        -> /system package update download 
    **Goal : To get the latest version of CHR**
4. backup and restore 
        -> #### GUI Method (WinBox)
- Create Backup:
        Go to Files > Click Backup button
        Enter filename (e.g., config_backup)
        Click Backup to save (creates .backup file)
5. user and passwords 
        -> add new user and login with new user, secure it
    **Goal : To be able to manage the users efficiently**
6. Reset to default configuration (optional)

7. create ether2 adapter (best practice)


## Layer2 Networking ----------(virtualbox)

### --xx LAB SETUP xx--
>>> Add 2 routers to virtualbox(RouterA, RouterB).
-----------------------------------------------------------------------------------
CHR VM		Adapter 1		        Adapter 2		        Adapter 3
-----------------------------------------------------------------------------------
RouterA		Bridged (WAN)		    Host-only: vboxnet0	    Host-only: vboxnet1
RouterB		Bridged (WAN)           Host-only: vboxnet0	    Host-only: vboxnet1
-----------------------------------------------------------------------------------
>>> --xx **Enable Promiscuous Mode** xx--
>> For each adapter in CHR settings → Advanced → set Promiscuous Mode = Allow All.
>> This allows VLANs/bonding to work.

1. VLANs between RouterA and RouterB
        -> interfaces> VLANs
    **Goal: RouterA sends VLAN 1/2 traffic, RouterB receives it.**
2. Bridge + STP on RouterA
        -> bridge> ...
    **Goal: Bridge ether2+ether3 and enable RSTP.**
3. BONDING (LINK AGGREGATION)
        -> bridge> Bond
    **Goal: Bond ether2+ether3 for failover.**


# images describing IPs and layers networking(bridging and bonding) 
>>> **WARNING** : Don't let the IPs overlap !!!!
>>> img-1.png, 
