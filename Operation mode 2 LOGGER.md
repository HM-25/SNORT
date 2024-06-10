Let's run Snort in Logger Mode

You can use Snort as a sniffer and log the sniffed packets via logger mode. You only need to use the packet logger mode parameters, and Snort does the rest to accomplish this.

Packet logger parameters are explained in the table below;
Parameter	Description
-l	

Logger mode, target log and alert output directory. Default output folder is /var/log/snort

The default action is to dump as tcpdump format in /var/log/snort
-K ASCII	Log packets in ASCII format.
-r	Reading option, read the dumped logs in Snort.
-n	Specify the number of packets that will process/read. Snort will stop after reading the specified number of packets.

**Logfile Ownership**

Before generating logs and investigating them, we must remember the Linux file ownership and permissions. No need to deep dive into user types and permissions. The fundamental file ownership rule; whoever creates a file becomes the owner of the corresponding file.

Snort needs superuser (root) rights to sniff the traffic, so once you run the snort with the "sudo" command, the "root" account will own the generated log files. Therefore you will need "root" rights to investigate the log files. There are two different approaches to investigate the generated log files;

    Elevation of privileges - You can elevate your privileges to examine the files. You can use the "sudo" command to execute your command as a superuser with the following command sudo command. You can also elevate the session privileges and switch to the superuser account to examine the generated log files with the following command: sudo su

    Changing the ownership of files/directories - You can also change the ownership of the file/folder to read it as your user: sudo chown username file or sudo chown username -R directory The "-R" parameter helps recursively process the files and directories.

**Logging with parameter "-l"**

First, start the Snort instance in packet logger mode; sudo snort -dev -l .
Once the traffic is generated, Snort will start showing the packets and log them in the target directory. You can configure the default output directory in snort.config file. However, you can use the "-l" parameter to set a target directory. Identifying the default log directory is useful for continuous monitoring operations, and the "-l" parameter is much more useful for testing purposes.

The -l . part of the command creates the logs in the current directory.

**Logging with parameter "-K ASCII"**

Start the Snort instance in packet logger mode; sudo snort -dev -K ASCII

*The logs created with "-K ASCII" parameter is entirely different. There are two folders with IP address names. 
*logs are in ASCII and categorised format, so it is possible to read them without using a Snort instance.

In a nutshell, ASCII mode provides multiple files in human-readable format, so it is possible to read the logs easily by using a text editor. By contrast with ASCII format, binary format is not human-readable and requires analysis using Snort or an application like tcpdump.

**Reading generated logs with parameter "-r"**

Start the Snort instance in packet reader mode; sudo snort -r

"-r" parameter also allows users to filter the binary log files. You can filter the processed log to see specific packets with the "-r" parameter and Berkeley Packet Filters (BPF). 

    sudo snort -r logname.log -X
    sudo snort -r logname.log icmp
    sudo snort -r logname.log tcp
    sudo snort -r logname.log 'udp and port 53'
