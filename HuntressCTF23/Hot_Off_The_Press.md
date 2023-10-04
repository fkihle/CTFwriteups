Challenge info:

Oh wow, a malware analyst shared a sample that I [read about in the news](https://www.huntress.com/blog/critical-vulnerabilities-ws_ftp-exploitation)!

But it looks like they put it in some weird kind of archive...? Anyway, the password should be infected as usual!

NOTE, this challenge is based off of a real malware sample. We have done our best to "defang" the code, 
but out of abudance of caution it is strongly encouraged you only analyze this inside of a virtual environment 
separate from any production devices. 


Solve Steps:

1. `file ` shows us that we're dealing with a uHarc archive.
2. [node-uharc](https://github.com/ghaschel/node-uharc)
