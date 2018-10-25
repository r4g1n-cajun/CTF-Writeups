### Description:

The police have tracked one of the Ghostf4c3 members’ locations. They have captured some traffic, but are unsure of what to do with it next. Help stop the Ghostf4c3 crew by assisting the police however they ask.

First thing that they need is IP address of the member

### File:

[pcap file](https://github.com/r4g1n-cajun/CTF-Writeups/raw/master/NCSAM%20Hacktober%20CTF%202018/Forensics/Files/3N3pnespviuVCNqXWiLAY44Ct2Ph1xNd.zip)

### Steps Taken

This one was pretty simple and straight forward, after opening the PCAP file in wireshark almost immediately the stream in questions is identified.

Packet #7's info section stands out:
  - ```vcom-tunnel(8001)```



So, following the TCP stream for this connection shows this is ```Sl3nderman```.


At first I saw ```flag-h3lpw1thw3b``` at the bottom of the stream but the challenge asked for the IP and not a flag, so this must be for another challenge.

Using the source IP in the TCP connection completes the challenge.

### Flag
  - ```10.105.50.175```

273	57.880237840	10.105.50.175	10.100.8.1	DNS	128	Standard query 0x4202 A quora-prod-tch-vpc-1136165707.us-east-1.elb.amazonaws.com OPT
