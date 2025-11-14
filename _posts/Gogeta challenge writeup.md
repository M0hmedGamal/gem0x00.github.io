Hello , At first when I saw the website it was like this :
![[Pasted image 20251114230844.png]]

The source Code is very simple but there is something took my eye :

![[Pasted image 20251114230956.png]]

After researching the vulnerability and methods of exploitation, the following GitHub issue provided essential insight and a proof-of-concept that facilitated successful exploitation: [https://github.com/golang/go/issues/23867](https://github.com/golang/go/issues/23867).

At first i tried the exploit in it :
```
khashaev.ru/go-vuln/index.html
```

that is the online page that carry the payload and it worked :
![[Pasted image 20251114232502.png]]
![[Pasted image 20251114232549.png]]

Then I crafted my own exploit to get the flag and hosted it via `ngrok`:
![[Pasted image 20251114232654.png]]

The Exploit and got the flag :
![[Pasted image 20251114232829.png]]
