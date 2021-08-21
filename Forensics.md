# Forensics

Hi! I'm your first Markdown file in **StackEdit**. If you want to learn about StackEdit, you can read me. If you want to play with Markdown, you can edit me. Once you have finished with me, you can create new files by opening the **file explorer** on the left corner of the navigation bar.


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
