
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
