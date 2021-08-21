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

## Up For A Little Challenge?
step 1 - downlad the picture:
https://mega.nz/file/LoABFK5K#0sEKbsU3sBUG8zWxpBfD1bQx_JY_MuYEWQvLrFIqWZ0

step 2 - check strings:
`strings Begin\ Hack.jpg` has a few clues:
- flag{Not_So_Simple...}
- password: Really? Again
- real_unlock_key: Nothing Is As It SeemsU
- https://mega.nz/#!z8hACJbb!vQB569ptyQjNEoxIwHrUhwWu5WCj1JWmU-OFjf90Prg

step 3 - download the zip file and unzip it

step 4 - extract zip file:
 
`\- .Processing.cerb4` is password protected, used the clue from the first step "Nothing Is As It Seems" as the password.

step 5 - open pictue and you can see a small text in the corner of the picture the flag

flag: flag{hack_complete}

## Digital Camouflage
step 1 - downlad the pcap:
https://mega.nz/file/XDBDRAQD#4jRcJvAhMkaVaZCOT3z3zkyHre2KHfmkbCN5lYpiEoY

step 2 - export http objects

step 3 - in file main we can we see an auth password with url encode and base64 (pswrd=UEFwZHNqUlRhZQ%3D%3D)

flag: **PApdsjRTae**

## Milk's Best Friend
step 1 - downlad the picture:
https://mega.nz/#!DC5F2KgR!P8UotyST_6n2iW5BS1yYnum8KnU0

step 2 - extract hidden files:
`binwalk -e oreo.jpg`

step 3 - strings on files
`strings b.jpg`

flag: **flag{eat_more_oreos}**

## A CAPture of a Flag
step 1 - downlad the pcap:

step 2 - open wireshark:
we can see there is a msg encoded with base64.. this is suspicious. let's decode it ZmxhZ3tBRmxhZ0luUENBUH0=

flag: **flag{AFlagInPCAP}**
