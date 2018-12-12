# Challenge 2
  - https://canyouhack.us/c/a518de63035f6de0f5f6a6e95b07d1b2

## Session Token Generator

Generating the tokens spits out:
```
f89c60d66862903a33465675c78f66566928364214432e43283784a05d87119966f08451252006277392f04e34831522
f15c03d03835946a93433662c54f68537954388232472e28299718a45d75199969f57441211083268357f09e01801551
f23c40d06853994a43471639c87f54564948343206480e90248788a12d44108937f75419241062297311f98e83872501
f16c31d13825914a58447654c36f78509973339211409e69235744a00d85143910f57443241070262350f20e45816542
```

There is a visible patter where characters repeat themselves every third character.

`fcd89a46cf59324e27ad19f42023fe85`

To ensure this was in-fact the case I generated the max number of tokens allowed (100) and put them into a text file and with a small and quick python script slice every 3rd character and print them in relation to the line in the file:

***cat.py***
```python
#!/usr/bin/env python
import fileinput

for line in fileinput.input():
    print line [::3],
```

```
[pj]@OSXploit~/h4ckm3/2:
>>wc -l tokens.txt && python cat.py tokens.txt > flag.txt
     100 tokens.txt

[pj]@OSXploit~/h4ckm3/2:
>>cat flag.txt | head -n 6
fcd89a46cf59324e27ad19f42023fe85
fcd89a46cf59324e27ad19f42023fe85
fcd89a46cf59324e27ad19f42023fe85
fcd89a46cf59324e27ad19f42023fe85
fcd89a46cf59324e27ad19f42023fe85
fcd89a46cf59324e27ad19f42023fe85

[pj]@OSXploit~/h4ckm3/2:
>>wc -l flag.txt && cat flag.txt | sort -u
     100 flag.txt
fcd89a46cf59324e27ad19f42023fe85
```

And that is in-fact the case as all 100 tokens convert to the same 32 character string 100 times. 
