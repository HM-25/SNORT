**Snort in IDS/IPS Mode**

Capabilities of Snort are not limited to sniffing and logging the traffic. IDS/IPS mode helps you manage the traffic according to user-defined rules.

Note that (N)IDS/IPS mode depends on the rules and configuration. TASK-10 summarises the essential paths, files and variables. Also, TASK-3 covers configuration testing. Here, we need to understand the operating logic first, and then we will be going into rules in TASK-9.


**Let's run Snort in IDS/IPS Mode**

NIDS mode parameters are explained in the table below;
Parameter	Description
-c	

Defining the configuration file.
-T	Testing the configuration file.
-N	Disable logging.
-D	Background mode.
-A	

Alert modes;
full: Full alert mode, providing all possible information about the alert. This one also is the default mode; once you use -A and don't specify any mode, snort uses this mode.

fast:  Fast mode shows the alert message, timestamp, source and destination IP, along with port numbers.

console: Provides fast style alerts on the console screen.

cmg: CMG style, basic header details with payload in hex and text format.

none: Disabling alerting.

Once you start running IDS/IPS mode, you need to use rules. As we mentioned earlier, we will use a pre-defined ICMP rule as an example. The defined rule will only generate alerts in any direction of ICMP packet activity.

alert icmp any any <> any any  (msg: "ICMP Packet Found"; sid: 100001; rev:1;)

This rule is located in "/etc/snort/rules/local.rules".

Remember, in this module, we will focus only on the operating modes. The rules are covered in TASK9&10. Snort will create an "alert" file if the traffic flow triggers an alert. One last note; once you start running IPS/IDS mode, the sniffing and logging mode will be semi-passive. However, you can activate the functions using the parameters discussed in previous tasks. (-i, -v, -d, -e, -X, -l, -K ASCII) If you don't remember the purpose of these commands, please revisit TASK4.


**IDS/IPS mode with parameter "-c and -T"**

Start the Snort instance and test the configuration file. sudo snort -c /etc/snort/snort.conf -T  This command will check your configuration file and prompt it if there is any misconfiguratioın in your current setting. You should be familiar with this command if you covered TASK3. If you don't remember the output of this command, please revisit TASK4.


**IDS/IPS mode with parameter "-N"**

Start the Snort instance and disable logging by running the following command: sudo snort -c /etc/snort/snort.conf -N

Now run the traffic-generator script as sudo and start ICMP/HTTP traffic. This command will disable logging mode. The rest of the other functions will still be available (if activated).

The command-line output will provide the information requested with the parameters. So, if you activate verbosity (-v) or full packet dump (-X) you will still have the output in the console, but there will be no logs in the log folder.


**IDS/IPS mode with parameter "-D"**

Start the Snort instance in background mode with the following command: sudo snort -c /etc/snort/snort.conf -D

**IDS/IPS mode with parameter "-A"**

Remember that there are several alert modes available in snort;

    console: Provides fast style alerts on the console screen.
    cmg: Provides basic header details with payload in hex and text format.
    full: Full alert mode, providing all possible information about the alert.
    fast: Fast mode, shows the alert message, timestamp, source and destination ıp along with port numbers.
    none: Disabling alerting.

In this section, only the "console" and "cmg" parameters provide alert information in the console. It is impossible to identify the difference between the rest of the alert modes via terminal. Differences can be identified by looking at generated logs. 

At the end of this section, we will compare the "full", "fast" and "none" modes. Remember that these parameters don't provide console output, so we will continue to identify the differences through log formats.


**IDS/IPS mode with parameter "-A console"**

Console mode provides fast style alerts on the console screen. Start the Snort instance in console alert mode (-A console ) with the following command sudo snort -c /etc/snort/snort.conf -A console
