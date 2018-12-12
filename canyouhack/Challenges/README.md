# Enumeration

Since the whole server is in scope:

## Host

```
PORT      STATE SERVICE     VERSION
80/tcp    open  http        nginx 1.4.6 (Ubuntu)
|_http-server-header: nginx/1.4.6 (Ubuntu)
|_http-title: Did not follow redirect to https://canyouhack.us/
443/tcp   open  ssl/http    nginx 1.4.6 (Ubuntu)
| http-robots.txt: 2 disallowed entries
|_/  /static/red-herring.png
|_http-server-header: nginx/1.4.6 (Ubuntu)
|_http-title: Security Innovation | Can You Hack Us?
| ssl-cert: Subject: commonName=canyouhack.us
| Subject Alternative Name: DNS:canyouhack.us, DNS:*.canyouhack.us
| Not valid before: 2018-09-22T00:00:00
|_Not valid after:  2019-10-22T12:00:00
|_ssl-date: TLS randomness does not represent time
1984/tcp  open  bigbrother?
| fingerprint-strings:
|   DNSStatusRequestTCP, DNSVersionBindReqTCP, GenericLines, GetRequest, HTTPOptions, Help, RPCCheck, RTSPRequest, SSLSessionReq:
|     For a moment, nothing happened. Then, after a second or so, nothing continued to happen.
|     long and thanks for all the fish.
|   NULL:
|_    For a moment, nothing happened. Then, after a second or so, nothing continued to happen.
10001/tcp open  scp-config?
| fingerprint-strings:
|   GenericLines:
|     You are lucky. Full moon tonight. You hear some noises.
|     Wait! There's something there you can't see! It's a door!
|     voice whispers: "The answer is 4163065174. Speak the question and enter."
|     hear laughter in the darkness. A trap door opens below you! You fall into a chasm.
|   GetRequest:
|     You are lucky. Full moon tonight. You hear some noises.
|     Wait! There's something there you can't see! It's a door!
|     voice whispers: "The answer is 3313812915. Speak the question and enter."
|     hear laughter in the darkness. A trap door opens below you! You fall into a chasm.
|   JavaRMI:
|     You are lucky. Full moon tonight. You hear some noises.
|     Wait! There's something there you can't see! It's a door!
|     voice whispers: "The answer is 4110717551. Speak the question and enter."
|     hear laughter in the darkness. A trap door opens below you! You fall into a chasm.
|   NULL:
|     You are lucky. Full moon tonight. You hear some noises.
|     Wait! There's something there you can't see! It's a door!
|     voice whispers: "The answer is 3313812915. Speak the question and enter."
|   ZendJavaBridge:
|     You are lucky. Full moon tonight. You hear some noises.
|     Wait! There's something there you can't see! It's a door!
|     voice whispers: "The answer is 2227033993. Speak the question and enter."
|_    hear laughter in the darkness. A trap door opens below you! You fall into a chasm.
10002/tcp open  documentum?
| fingerprint-strings:
|   X11Probe:
|_    4444
```
