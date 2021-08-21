# Forensics


# Hard

## Corrupted file

step 1:
downlad corrupted gif:
https://mega.nz/#!aKwGFARR!rS60DdUh8-jHMac572TSsdsANClqEsl9PD2sGl-SyDk

step 2:
`
xxd unopenable.gif | xxd -r -s 4 > new_gif.gif; 
data="GIF8"; 
echo -n $data | xxd -p | xxd -r -p - new_gif.gif
`
