# NCSAM Hacktober CTF Writeup

This was an awesome CTF and I had a lot of fun doing it. It lasted one week and I worked on it as I had time periodically through out the day and later at night.

Some of the challenge categories I have had no experience in so it was a first for me and I had to learn as I went along.
- I decided to compete alone
- 4 person max per team
- Came in 17th out of 140 teams.
- This was my first 'real' CTF that wasn't just basic pentesting against some VMs.
- Some of the flags I was able to find without completely reversing/decompiling binaries so those won't be very detailed.

## Invite Page
This was the page posted as the CTF. You wen't given the link to the registration page, so there was a challenge before even signing up.

![Image](https://raw.githubusercontent.com/r4g1n-cajun/CTF-Writeups/master/NCSAM%20Hacktober%20CTF%202018/Files%20for%20README/Initial%20Page.png?token=AlLywJK8GpRetMwoeY-N1zgBZxsvQrFAks5b2MmCwA%3D%3D)

Scanning the QR code takes you to another page:

![Alt Text](https://raw.githubusercontent.com/r4g1n-cajun/CTF-Writeups/master/NCSAM%20Hacktober%20CTF%202018/Files%20for%20README/secret_page.gif?token=AlLywOp93fNwCUO-5qW0bL0TvTFKevGhks5b2MxKwA%3D%3D)

It's pretty obvious that the string around the QR code is base64 encoded, decoding it gives us the CTF main page:
```
[pj]@OSXploit~:
>>echo aGFja3RvYmVyLm9yZw== | base64 -D
hacktober.org
```

Now you are able to register for the CTF and start the challenges.

![Image](https://raw.githubusercontent.com/r4g1n-cajun/CTF-Writeups/master/NCSAM%20Hacktober%20CTF%202018/Files%20for%20README/CTF%20Page.png?token=AlLywBxkY3UD7LJCP91mjeCrxzJAOjXAks5b2M9UwA%3D%3D)

## About Hacktober CTF:

Hacktober CTF is a Midwest Cyber Center (MC2) sponsored event for National Cybersecurity Awareness Month. Teams of 4 will compete against one another to test and expand cybersecurity skills and awareness. Participants will experience challenges involving exploitation, databases, web penetration, DFIR, cryptography, programming, scripting, recon, steganography, and more.

The game will consist of challenges that players must solve in order to advance and gain points. The challenges will focus on the following categories:
  - Cryptography – encrypted and encoded messages
  - Exploitation – hacking vulnerable software applications
  - Programming – solving problems programmatically through Python, C, and VBA
  - SQL – databases designed to hold various information from employee info to sensitive data
  - Stegonagraphy – hiding data and messages in pictures and other types of media
  - UNIX – basic fundamentals of Linux systems

Players will be guided through the competition by following a fictional storyline that helps them gather intel, hints, and find the best possible solutions for solving challenges.

### Story (Gh0stf4c3)

***Description***

Gh0stf4c3 is a hacktivist group known for causing mischief and mayhem. They have no real objective other than to frighten people and companies, hack into their systems, and steal. They employ “trick or treat” tactics where, if you don’t meet their demands up front (treat) they will hack into your system and cause trouble (trick). They are especially active during the Halloween season, where most of their activity is conducted from 1-31 Oct. They have an affinity towards horror and Halloween, and will theme their hacks and activity as such.

#### Actors

##### V0rh33s

***Tactics:***
  - Website vandalism
  - Programming

##### Sl3ndermann

***Tactics:***
  - Steganography
  - Exploitation

##### Freddy_k1ll

***Tactics:***
  - Cryptography
  - Programming


## Top 25:

![Image](https://raw.githubusercontent.com/r4g1n-cajun/CTF-Writeups/master/NCSAM%20Hacktober%20CTF%202018/Top_25.png?token=AlLywABabdvRx4Cmi5vitUvGV8m6fTU-ks5b2MJmwA%3D%3D)
