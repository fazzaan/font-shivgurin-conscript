


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
### To Do:
* vowels together must be treated as _only vowels_, up until there is a consonant prior. Detection logic for this may be challenging. Ideas:
  * sub [@ConsAll] [@VowelAll]' by @VowelPostCons;
  * Then use standard sub rules for sequences starting with @VowelPostCons. 
