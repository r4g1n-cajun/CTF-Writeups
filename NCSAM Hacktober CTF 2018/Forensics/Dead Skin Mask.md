### Description:

Mascoutah Police Department received an anonymous fax yesterday regarding a domestic altercation that happened in 1960. Merle H. Sweeney was slain in his sleep after a drunken altercation between he and his wife. His wife claimed she had left the house and was staying with her mother in Cahokia at the time, at that time, her mother corroborated her story.

The fax that was received claimed that the wife was actually guilty and also contained a picture of the assailant. There is something strange about the picture… maybe you can help us to figure it out.

### Picture:
![Picture](https://raw.githubusercontent.com/r4g1n-cajun/CTF-Writeups/master/NCSAM%20Hacktober%20CTF%202018/Forensics/Files/RWLdUXz4zo4s1TdchGsnU7OwjLRI6okP.jpg)


### Steps Taken

It states that there is ***something strange*** about the picture, and since this is a forensics challenge that means there is something embedded in the file itself.

Binwalk shows there is a zip archive embedded in the file.

```
[pj]@PJs-MacBook-Pro~/CTF:
>>binwalk RWLdUXz4zo4s1TdchGsnU7OwjLRI6okP.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             JPEG image data, JFIF standard 1.01
99916         0x1864C         JPEG image data, JFIF standard 1.01
195951        0x2FD6F         Zip archive data, at least v2.0 to extract, uncompressed size: 10, name: dontopendeadinside
196155        0x2FE3B         End of Zip archive
```

So the next step is to extract the archive from the file and examine it's contents.

```
[pj]@PJs-MacBook-Pro~/CTF:
>>binwalk -Me RWLdUXz4zo4s1TdchGsnU7OwjLRI6okP.jpg

Scan Time:     2018-10-24 22:00:32
Target File:   /Users/pj/CTF/RWLdUXz4zo4s1TdchGsnU7OwjLRI6okP.jpg
MD5 Checksum:  991f61f0311061762f766c653548981b
Signatures:    344

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             JPEG image data, JFIF standard 1.01
99916         0x1864C         JPEG image data, JFIF standard 1.01
195951        0x2FD6F         Zip archive data, at least v2.0 to extract, uncompressed size: 10, name: dontopendeadinside
196155        0x2FE3B         End of Zip archive


Scan Time:     2018-10-24 22:00:32
Target File:   /Users/pj/CTF/_RWLdUXz4zo4s1TdchGsnU7OwjLRI6okP.jpg.extracted/dontopendeadinside
MD5 Checksum:  c61db6c368d10ecd83c499794bbc7df1
Signatures:    344

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
```

After extracting there is a text file named ```dontopendeadinside```. Reading the file revels the flag.

```
[pj]@PJs-MacBook-Pro~/CTF/_RWLdUXz4zo4s1TdchGsnU7OwjLRI6okP.jpg.extracted:
>>cat dontopendeadinside
flag-ea5y
```

### Flag
  - ```flag-ea5y```
