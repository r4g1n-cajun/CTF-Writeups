### Description:

The police have tracked one of the Ghostf4c3 members’ locations. They have captured some traffic, but are unsure of what to do with it next. Help stop the Ghostf4c3 crew by assisting the police however they ask.

First thing that they need is IP address of the member

### File:

[pcap file](https://github.com/r4g1n-cajun/CTF-Writeups/raw/master/NCSAM%20Hacktober%20CTF%202018/Forensics/Files/3N3pnespviuVCNqXWiLAY44Ct2Ph1xNd.zip)

### Steps Taken

This one was pretty simple and straight forward, after opening the PCAP file in wireshark almost immediately the stream in questions is identified.

Packet #7's info section stands out:
  - ```vcom-tunnel(8001)```

So, following the TCP stream for this connection shows this is ```Sl3nderman```

```
JOIN #hacking
:Sl3ndermann!~Sl3nderma@47.47.11.155 JOIN #hacking
MODE #hacking
:tolkien.freenode.net 353 Sl3ndermann = #hacking :Sl3ndermann folorn chkrr00k hitchhiker shadrak_1 sunrunner20 anon_1029 AldusOrion flipm0de tomaw Guest47263 Smarticles101 OmegaD George33 ErgoX___
:tolkien.freenode.net 366 Sl3ndermann #hacking :End of /NAMES list.
WHO #hacking
:tolkien.freenode.net 324 Sl3ndermann #hacking +cnt
:tolkien.freenode.net 329 Sl3ndermann #hacking 1264834911
:tolkien.freenode.net 352 Sl3ndermann #hacking ~Sl3nderma 47.47.11.155 tolkien.freenode.net Sl3ndermann H :0 Sl3ndermann
:tolkien.freenode.net 352 Sl3ndermann #hacking ~folorn 173.0.24.107 karatkievich.freenode.net folorn H :0 realname
:tolkien.freenode.net 352 Sl3ndermann #hacking ~chkrr00k unaffiliated/chkrr00k karatkievich.freenode.net chkrr00k H :0 cute
:tolkien.freenode.net 352 Sl3ndermann #hacking ~hitchhike 96-33-82-204.dhcp.ahvl.nc.charter.com verne.freenode.net hitchhiker H :0 hitchhiker
:tolkien.freenode.net 352 Sl3ndermann #hacking ~shadrak cpe-76-89-136-13.socal.res.rr.com orwell.freenode.net shadrak_1 H :0 shadrak
:tolkien.freenode.net 352 Sl3ndermann #hacking ~sunrunner unaffiliated/sunrunner20 weber.freenode.net sunrunner20 H :0 sunrunner20
:tolkien.freenode.net 352 Sl3ndermann #hacking uid323796 gateway/web/irccloud.com/x-tjghnzjamszjxpdb wolfe.freenode.net anon_1029 G :0 anon_1029
:tolkien.freenode.net 352 Sl3ndermann #hacking ~AldusOrio 198.37.207.70 hitchcock.freenode.net AldusOrion H :0 AldusOrion
:tolkien.freenode.net 352 Sl3ndermann #hacking ~magikm4n 209.97.143.109 roddenberry.freenode.net flipm0de H :0 stellar
:tolkien.freenode.net 352 Sl3ndermann #hacking tom freenode/staff/tomaw kornbluth.freenode.net tomaw H :0 Tom Wesley <tomaw@freenode.net>
:tolkien.freenode.net 352 Sl3ndermann #hacking ~root 2607:5300:201:3100::15ef kornbluth.freenode.net Guest47263 G :0 Unknown
:tolkien.freenode.net 352 Sl3ndermann #hacking Smarticles gateway/shell/firrre/x-bxlwxbprqxchsysf leguin.freenode.net Smarticles101 H :0 Logan
:tolkien.freenode.net 352 Sl3ndermann #hacking uid321010 gateway/web/irccloud.com/x-crvvuittoflixmim niven.freenode.net OmegaD H :0 OmegaD
:tolkien.freenode.net 352 Sl3ndermann #hacking ~GeorgeCre 66.212.143.103.nauticom.net sinisalo.freenode.net George33 H :0 GeorgeCrenshaw
:tolkien.freenode.net 352 Sl3ndermann #hacking sid219675 gateway/web/irccloud.com/x-nxgthfihlgyeahwd leguin.freenode.net ErgoX___ H :0 zoop
:tolkien.freenode.net 315 Sl3ndermann #hacking :End of /WHO list.
PRIVMSG #hacking :hello
WHO #hacking %ctnf,152
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking Sl3ndermann H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking folorn H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking chkrr00k H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking hitchhiker H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking shadrak_1 H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking sunrunner20 H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking anon_1029 G
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking AldusOrion H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking flipm0de H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking tomaw H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking Guest47263 G
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking Smarticles101 H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking OmegaD H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking George33 H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking ErgoX___ H
:tolkien.freenode.net 315 Sl3ndermann #hacking :End of /WHO list.
PING LAG1538532235010223
:tolkien.freenode.net PONG tolkien.freenode.net :LAG1538532235010223
PING LAG1538532265088489
:tolkien.freenode.net PONG tolkien.freenode.net :LAG1538532265088489
PRIVMSG #hacking :Can anyone help with joining the Gh0stf4c3 group? The server isnt responding
PRIVMSG #hacking :need to get that site ASAP
WHO #hacking %ctnf,152
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking Sl3ndermann H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking folorn H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking chkrr00k H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking hitchhiker H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking shadrak_1 H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking sunrunner20 H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking anon_1029 G
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking AldusOrion H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking flipm0de H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking tomaw H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking Guest47263 G
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking Smarticles101 H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking OmegaD H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking George33 H
:tolkien.freenode.net 354 Sl3ndermann 152 #hacking ErgoX___ H
:tolkien.freenode.net 315 Sl3ndermann #hacking :End of /WHO list.
PING LAG1538532295166226
:tolkien.freenode.net PONG tolkien.freenode.net :LAG1538532295166226
PRIVMSG #hacking :flag-h3lpw1thw3b
```

At first I saw ```flag-h3lpw1thw3b``` at the bottom of the stream but the challenge asked for the IP and not a flag, so this must be for another challenge.

Using the originating IP in the TCP connection completes the challenge.

### Flag
  - ```47.47.11.155```
  
