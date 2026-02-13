


### Glyph names list for font design app
ahBase baBase caBase daBase ihBase faBase gaBase iiBase zhaBase kaBase laBase maBase naBase ngaBase paBase rtaBase rraBase shaBase taBase uuBase vaBase waBase yaBase tsaBase accentBase preVowelBase  

#### Glyph mapping
ahBase - a  
baBase - b  
caBase - c  
daBase - d  
iiBase - e  
faBase - f  
gaBase - g  
ihBase - i  
zhaBase - j  
kaBase - k  
laBase - l  
maBase - m  
naBase - n  
paBase - p  
rtaBase - r  
shaBase - s  
taBase - t  
uuBase - u  
vaBase - v  
waBase - w  
yaBase - y  
tsaBase - z  

##### Digraphs
ngaBase - ng (& q?)  
rraBase - rr  

##### Diacritics
ahBase - a  
iiBase - e  
ihBase - i  
uuBase - u  
accentBase - o?  
preVowelBase - h?  


## Logic notes for OpenType Scripting  
### Example words from creator
Left word = orthography; Right word = typing scheme:  
(H model no longer necessary!)  
* seva - sehva  
* aík - aiok / aIk  
* yusim - yuhsihm  
* sevguren - sehvguhrehn  
* vam - vahm  
* veim - veihm  
* yusim - yuhsihm  
* Ramin - Rahmihn  
* fan - fahn  

* leitse - leize  
* zhishtap - jistap  
* in - in  
* maizhinashish - maijinasis  
* waimaishil-iet - waimaisiliet / waimaisilhiet (ok may need the H for this one because the creator's written form indicates that both the i and e belong to the T and not the L. Ask the creator why it's written like this and if it's stylistic or necessary orthographically. [end of third line])  
* miáchyizh - miaocyij  
* du - du  
* maispada - maispada  
* yusim - yusim  
* akyut - akyut  
* ne - ne  
* amám - amaom  
* ru - ru  


### Broken sequences  
[ ] - cons + i/u + i/u + a/e + a/e (but I think this is very rare)  
[x] - letters which aren't wide enough to hold vowels a and e by default (and thus need a vowel-bearing form):
  * for all a/e: ca da fa ga zha ka nga pa rta rra sha ta  
  * for vowel sequences ia/ie: na  
  * caWide daWide faWide gaWide zhaWide kaWide ngaWide paWide rtaWide rraWide shaWide taWide naWide  
  * Actually, most of them are fine with just a bit of widening and anchor positioning. Glyphs which definitely need a dedicated wide glyph form:
    * shaWide 
[ ] - u-mark's accent should be on top when in certain positions  


### Shape classes
#### Bar from mid-right
baBase faBase maBase naBase paBase shaBase vaBase waBase yaBase tsaBase  
#### Hook from base to mid-right
caBase daBase gaBase zhaBase kaBase laBase ngaBase rtaBase rraBase  
#### Diagonal from base to mid-right
taBase  


### To Do:
[x] - vowels together must be treated as _only vowels_, up until there is a consonant prior. Detection logic for this may be challenging. Ideas:
  * sub [@ConsAll] [@VowelAll]' by @VowelPostCons;
  * Then use standard sub rules for sequences starting with @VowelPostCons. 
[x] - Consider restructuring logic so that the pre-cons-vowel-breaker [h] is unnecessary.  
  * onset vowel = BARE VOWEL so that we don't need initial char detection rules.  
    * This vowel must be a SPACING vowel, i.e. a "Simple" glyph type that creates cursor advancement.  
  * bare vowel + vowel = sub vowel by pre-cons-vowel sub rules. No CHAR type vowels with the through-line.  
  * consonant + vowel = sub vowel by "post-consonant-vowel". This vowel glyph may be only a ladder logic glyph and might not be seen. This post-cons-vowel glyph tells the next sub logic rules to operate accordingly.  
  * post-cons-vowel + vowel = sub vowel by post-cons-vowel sub rules  
[x] - Make elongated consonants for a/e and ia/ie (only needed for sha)  
[x] - Adjust anchors for every consonant  
[ ] - Adjust vowel lsb and rsb  
[ ] - Fix vowel anchoring for i then u - u then i works though.  
[ ] - Determine how to shunt pre-cons vowels backwards. Complicated. Conditions: 1) only if the consonant is IN a word, not at the start. 2) vowels may need to attach to horizontal anchors for mark-on-mark placement. 3) vowels will need to have zero-adv-width in these cases.
