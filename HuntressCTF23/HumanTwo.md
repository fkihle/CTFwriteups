Challenge Info:

Author: @JohnHammond

During the MOVEit Transfer exploitation, there were tons of "indicators of compromise" hashes available for the human2.aspx webshell! We collected a lot of them, but they all look very similar... except for very minor differences. Can you find an oddity?

NOTE, this challenge is based off of a real malware sample. We have done our best to "defang" the code, but out of abudance of caution it is strongly encouraged you only analyze this inside of a virtual environment separate from any production devices. 


Solve Steps:

1. Extract all files using `binwalk -e <file.zip>`
2. Check two files for differences using `diff <file1> <file2>`
Output:
```
<     if (!String.Equals(pass, "0c3ad8b8-3bbf-45da-bd1b-9c9bf69cf116")) {
---
>     if (!String.Equals(pass, "7ffff7ce-b902-49c1-a450-84c428f33154")) {
```
3. Print that specific line from all files using `grep 'if (!String.Equals(pass,' *`
4. A quick scroll shows one file with a unique "pass" to the rest.
Output:
```
if (!String.Equals(pass, "666c6167-7b36-6365-3666-366131356464"+"64623065-6262-3333-3262-666166326230"+"62383564-317d-0000-0000-000000000000")) {
```
6. Concating the three strings gives us: 666c6167-7b36-6365-3666-36613135646464623065-6262-3333-3262-66616632623062383564-317d-0000-0000-000000000000
7. All values in the string are inside the hex range, so lets try converting in from hex to text. First remove all "-" and "0" from string: 666c61677b36636536663661313564646462306562623333326266616632623062383564317d
8. Using python3:
>>> bytes.fromhex('666c61677b36636536663661313564646462306562623333326266616632623062383564317d').decode('utf-8')
'flag{6ce6f6a15dddb0ebb332bfaf2b0b85d1}'
