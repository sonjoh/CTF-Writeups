# UIUCTF 2021 Writeup

![UIUCTF 2021](https://github.com/sonjoh/CTF-Writeups/blob/main/uiuctf-2021/res/uiuctf-2021.png?raw=true)

Written by [usr: Slipner team:R49n4r0k](https://ctftime.org/user/107395)

---

## phpfuck (Points: 50)
### Task
i hate php
<br/>
<http://phpfuck.chal.uiuc.tf>
<br/>
author: arxenix
### Writeup
In the top of the site we see this code
```php
<?php
// Flag is inside ./flag.php :)
($x=str_replace("`","",strval($_REQUEST["x"])))&&strlen(count_chars($x,3))<=5?print(eval("return $x;")):show_source(__FILE__)&&phpinfo();
```
2nd line is the hint
> // Flag is inside ./flag.php :)

After going to http://phpfuck.chal.uiuc.tf/flag.php i could simply view the source code for the flag
### Flag
```
uiuctf{pl3as3_n0_m0rE_pHpee}
```

---

## emote (Points: 50)
### Task
recently i've been converting strings into images for funsies and staring at them. anytime time to go share those images with my friends in discord!
<br/>
warning: staring at noise in visual form may or may not introduce you to the abyss
<br/>
author: ian5v
### Writeup
In the discord channel there was a wierd emote that looked a bit like noise. I downloaded the file as emote with no file extention (ive added the .png extention in the file uploaded here).
Pic:
![emote.png](https://raw.githubusercontent.com/sonjoh/CTF-Writeups/main/uiuctf-2021/emote/emote.png)
With ubuntu i ran the emote through zsteg and got the flag.
### Flag
```
uiuctf{staring_at_pixels_is_fun}
```

---

## CEO (Points: 50)
### Task
You just wirelessly captured the handshake of the CEO of a multi-million dollar company! Use your password cracking skills to get the password! Wrap the password in the flag format. E.g: uiuctf{password}
<br/>
author: Rohans885
### Writeup
The first thing that came to my mind was aircrack-ng. But i didnt know the bssid to use so i had to start analyzing the cap file in wireshark. Here i saw that the very first frame captured was a Broadcast / Beacon frame. If you open the frame you can find the bssid under Transmitter and Source address; e4:95:6e:45:90:24. I started a kali VM where i knew i had aircrack and wordlists and ran the command.
```
aircrack-ng ~/ctf/uiuctf-2021/CEO/megacorp-01.cap -b e4:95:6e:45:90:24 -w /usr/share/wordlists/rockyou.txt
```
Output: (after a couple of minutes)
> KEY FOUND! [ nanotechnology ]
### Flag
```
uiuctf{nanotechnology}
```

---

## Chaplin's PR Nightmare - 2 (Points: 50)
### Task
Charlie made an advertisement to promote his company, he is using the modern media platform YouTube to present it! Can you find it?
<br/>
The inner content of this flag begins with "ch"
<br/>
author: Thomas
### Writeup
On this task i thought i started on another task with the action house bot on discord. When i tried the command
```
/flag
```
i got a DM:
> My friend @ChaplinCoding has some of those, he has been doing coding recently on twitter??? Otherwise we are auctioning some off if you got the cash.

I serched for @ChaplinCoding on google and found the channel [@ChaplinCoding](https://www.youtube.com/channel/UCxPyHVMa8TyKrOj05x86osA/featured) , from this link i quicly went through the only video on the channel and found the flag on the screen in the end of the video.
### Flag
```
uiuctf{ch@plin_on_th3_tV!!}
```

---

## wasmbaby (Points: 50)
### Task
wasm's a cool new technology! <http://wasmbaby.chal.uiuc.tf>
<br/>
author: ian5v
### Writeup
I did a search for the engine that runs the site and found it was a engine for webassembely. I then realized i shoud've understood this when i read the title.
I entered the source code for index.wasm and searched for uiuctf and found the flag.
### Flag
```
uiuctf{welcome_to_wasm_e3c3bdd1}
```

<!--
## back_to_basics (Points: ) -UNSOLVED
### Task
Shoutout to those people who think that base64 is proper encryption
author: epistemologist

Attachments: main.py, flag_enc
### Writeup
### Flag
## Welcome to UIUCTF'21 1 (Points: 1)
### Task
Welcome to UIUCTF'21! Your flag can be found on this very page.
>Hint:
>take a closer look at the wonderful background art :)
### Writeup
Found the flag in the bacgroud picture on uiuc.tf
### Flag
```
uiuctf{secret_pictures}
```

## Join our Discord 1 (Points: 1)
### Task
Join the discord
### Flag
```
uiuctf{y0u_j01n3d_tH3_dIsCorD!!!}
```
--->
 -- SJ
