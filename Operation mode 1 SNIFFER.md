Let's run Snort in Sniffer Mode

Like tcpdump, Snort has various flags capable of viewing various data about the packet it is ingesting.

Sniffer mode parameters are explained in the table below;

**Parameter	Description**
-v	Verbose. Display the TCP/IP output in the console.
-d	Display the packet data (payload).
-e	Display the link-layer (TCP/IP/UDP/ICMP) headers. 
-X	Display the full packet details in HEX.
-i	This parameter helps to define a specific network interface to listen/sniff. Once you have multiple interfaces, you can choose a specific interface to sniff. 

**Sniffing with parameter "-i"**

Start the Snort instance in verbose mode (-v) and use the interface (-i) "eth0"; sudo snort -v -i eth0

In case you have only one interface, Snort uses it by default. The above example demonstrates to sniff on the interface named "eth0". Once you simulate the parameter -v, you will notice it will automatically use the "eth0" interface and prompt it.

**Sniffing with parameter "-v"**

Start the Snort instance in verbose mode (-v); sudo snort -v

Verbosity mode provides tcpdump like output information. Once we interrupt the sniffing with CTRL+C, it stops and summarises the sniffed packets.

**Sniffing with parameter "-d"**

Start the Snort instance in dumping packet data mode (-d); sudo snort -d

Packet data payload mode covers the verbose mode and provides more data.

Sniffing with parameter "-de"

Start the Snort instance in dump (-d) and link-layer header grabbing (-e) mode; snort -d -e

Note that you can use the parameters both in combined and separated form as follows;

    snort -v
    snort -vd
    snort -de
    snort -v -d -e
    snort -X

Now run the traffic-generator script as sudo and start ICMP/HTTP traffic. Once the traffic is generated, snort will start showing the  packets in verbosity mode as follows;

Sniffing with parameter "-X"

Start the Snort instance in full packet dump mode (-X); sudo snort -X

Now run the traffic-generator script as sudo and start ICMP/HTTP traffic. Once the traffic is generated, snort will start showing the  packets in verbosity mode as follows;
