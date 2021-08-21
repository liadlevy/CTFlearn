# Forensics
A walkthrough of CTFlearn forensics challenges
# Hard
## Corrupted file
step 1 - downlad corrupted gif:
https://mega.nz/#!aKwGFARR!rS60DdUh8-jHMac572TSsdsANClqEsl9PD2sGl-SyDk

step 2 - analyze the problem: 
- usually corrupted file indicates stracture error, we can check the header of the file with `file unopenable.gif` and we can see it doesn't reconize it is a gif format. Likely to be in the header. 
- Using `hexdump unopenable.gif` we can see the header and relize the 4 first bytes are deleted "GIF8"

step 3 - add the missing bytes:
`
xxd unopenable.gif | xxd -r -s 4 > new_gif.gif; 
data="GIF8"; 
echo -n $data | xxd -p | xxd -r -p - new_gif.gif
`

step 4 - gif with 3 base64 strings (base64 usually ends with ==). Decode it ZmxhZ3tnMWZfb3JfajFmfQ and you'll get the flag! 

flag: **flag{g1f_or_j1f}**
# Medium
## 07601
step 1 - downlad the picture:
https://mega.nz/file/CXYXBQAK#6eLJSXvAfGnemqWpNbLQtOHBvtkCzA7-zycVjhHPYQQ

step 2 - extract hidden files:
`binwalk -e AGT.png`

step 3 - explore the files using common forensics binaries (file, strings etc). TIP: I like to use `grep -i -r "ctf" *` and it helps me to analyze faster the files. I found a match!

step 4 - `strings I Warned You.jpeg` and flag found!

flag: **CTF{Du$t1nS_D0jo}**
