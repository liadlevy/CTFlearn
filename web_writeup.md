# WEB
A writeup of CTFlearn web challenges
#  Easy
## gobustme
step 1 - open website and find the hints:
- https://gobustme.ctflearn.com
- hints:
	- The name of the challenge is gobustme (we probably need to use `dirbuster`)
	- In the website there is a wordlist we should download it

step 2 - run dirbuster with the wordlist:
`dirbuster -u https://gobustme.ctflearn.com/ -l wordlist.txt`

flag is in https://gobustme.ctflearn.com/hide/ 

flag: **CTFlearn{gh0sbu5t3rs_4ever}**

#  Medium
## Don't Bump Your Head(er)
step 1 - open the website and look for hints
- When viewing source code we see a hidden comment that looks like the user agent (UA) we need to use bypass the UA filter

step 2 - get the webpage using the "Sup3rS3cr3tAg3nt" UA:
- `wget -U "Sup3rS3cr3tAg3nt" "http://165.227.106.113/header.php" -O - ` 

step 3 - there is a referer filter too (Sorry, it seems as if you did not just come from the site, "awesomesauce.com"):
-  `wget -U "Sup3rS3cr3tAg3nt" "http://165.227.106.113/header.php" --referer "awesomesauce.com" -O -`

flag: **flag{did_this_m3ss_with_y0ur_h34d}**

#  HARD
## Inj3ction Time
step 1 - using jsql to automate the sql injection
- put the https://web.ctflearn.com/web8/?id= in the url

step 2 - sql injection was successful and we got the DB
- open the table webeight.w0w_y0u_f0und_m3 and we found the flag!

flag: **abctf{uni0n_1s_4_gr34t_c0mm4nd}**
