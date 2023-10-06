Challenge info:

Author: @JohnHammond

Caesar caesar, on the wall, who is the fairest of them all?

Perhaps a clever ROT13?

NOTE: this flag does not follow the usual MD5 hash standard flag format. It is still wrapped with the code>flag{} prefix and suffix.

Solve Steps:

1. We're given a .txt file with the following:
```
     Bu obl! Jbj, guvf jnezhc punyyratr fher   bf V !erugrtbg ghc bg ahs sb gby n fnj 
    qrsvavgryl nofbyhgryl nyjnlf ybir gelvat   ftavug rivgnibaav qan jra ch xavug bg 
       gb qb jvgu gur irel onfvp, pbzzba naq   sb genc gfevs ruG !frhdvauprg SGP pvffnyp 
     lbhe synt vf synt{whyvhf_ naq gung vf n   tavuglerir gba fv gv gho gengf gnret 
 gung lbh jvyy arrq gb fbyir guvf punyyratr.    qan rqvu bg tavleg rxvy g'abq V 
  frcnengr rnpu cneg bs gur synt. Gur frpbaq   bq hbl gho _n_av fv tnys rug sb genc 
   arrq whfg n yvggyr ovg zber. Jung rknpgyl   rxnz qan leg bg reru rqhypav rj qyhbuf 
     guvf svyyre grkg ybbx zber ratntvat naq   ?fravyjra qqn rj qyhbuF ?ryvujugebj 
    Fubhyq jr nqq fcnprf naq gel naq znxr vg   uthbar fv fravy lanz jbU ?ynpvegrzzlf 
 gb znxr guvf svyyre grkg ybbx oryvrinoyr? N    n avugvj ferggry sb renhdf qvybf 
 fvzcyr, zbabfcnpr-sbag grkg svyr ybbxf tbbq   rug gn gfbzyn rj reN .rz bg uthbar 
   raq? Vg ybbxf yvxr vg! V ubcr vg vf tbbq.   }abvgprysre fv tnys ehbl sb genc qevug ruG 
naq ng guvf cbvag lbh fubhyq unir rirelguvat   ebs tnys fvug gvzohf bg qrra hbl gnug 
    cbvagf. Gur ortvaavat vf znexrq jvgu gur   ,rpneo lyehp tavarcb rug qan kvsrec tnys 
  naq vg vapyhqrf Ratyvfu jbeqf frcnengrq ol   lyehp tavfbyp n av qar bg ,frebpferqah 
  oenpr. Jbj! Abj GUNG vf n PGS! Jub xarj jr   fvug bg erucvp enfrnp rug xyvz qyhbp 
            rkgrag?? Fbzrbar trg gung Whyvhf   !ynqrz n lht enfrnP 
```
2. The text looks mirrored along the y-axis and I'm assuming that the right side is the mirrored side. I wrote a little program that imports the text from file, splits the two sides, reverses the right side and rot13 decodes the whole thing. I need to learn python so that's what i used for this.
3. Python script used:
```python
## import 're' for use of regex
import re
## import 'codecs' for use of ROT13
import codecs

## Split inputtext into a two dimensional listarray with
## [x][0] as left side and [x][1] as right side
with open("caesarmirror.txt", "r") as f:
  txtlines = [text.rstrip('\n') for text in f]
  txt = [line.strip() for line in txtlines]
  elements = [re.split(r"\s\s\s", lines) for lines in txt]

# print each side rot13 decoded with a reversing of the right side
for i in range(len(elements)):
  print(codecs.encode(elements[i][0], 'rot_13') + " " + codecs.encode(elements[i][1][::-1], 'rot_13'))

f.close()
```
4. Output:
```
Oh boy! Wow, this warmup challenge sure was a lot of fun to put together! I so
definitely absolutely always love trying to think up new and innovative things
to do with the very basic, common and classic CTF techniques! The first part of
your flag is flag{julius_ and that is a great start but it is not everything
that you will need to solve this challenge. I don't like trying to hide and
separate each part of the flag. The second part of the flag is in_a_ but you do
need just a little bit more. What exactly should we include here to try and make
this filler text look more engaging and worthwhile? Should we add newlines?
Should we add spaces and try and make it symmetrical? How many lines is enough
to make this filler text look believable? A solid square of letters within a
simple, monospace-font text file looks good enough to me. Are we almost at the
end? It looks like it! I hope it is good. The third part of your flag is reflection}
and at this point you should have everything that you need to submit this flag for
points. The beginning is marked with the flag prefix and the opening curly brace,
and it includes English words separated by underscores, to end in a closing curly
brace. Wow! Now THAT is a CTF! Who knew we could milk the caesar cipher to this
extent?? Someone get that Julius Caesar guy a medal!
```
5. flag: **flag{julius_in_a_reflection}**
6. Note: I could have outputed the result to a file and used `grep` to produce the flag with something like:
```
$ grep -oP 'flag is \K\S+' output.txt       
flag{julius_
in_a_
reflection}
```
