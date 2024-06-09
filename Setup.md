user@ubuntu$ snort -V  --> Show instance version

user@ubuntu$ sudo snort -c /etc/snort/snort.conf -T 
    Here "-T" is used for testing configuration, and "-c" is identifying the             configuration file (snort.conf). Once we use a configuration file, snort got         much more power! The configuration file is an all-in-one management file of the      snort. Rules, plugins, detection mechanisms, default actions and output settings     are identified here. It is possible to have multiple configuration files for         different purposes and cases but can only use one at runtime.
   
    
