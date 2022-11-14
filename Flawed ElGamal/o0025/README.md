Flawed ElGamal
===
## Summary
**Author:** Mystiz  
**Categories:** crypto, ★☆☆☆☆  
**Points:** 50

## Description

Cryptography is difficult. It is hard to implement -- every small mistakes would lead to a total break down.

I tried my very best to implement the ElGamal according to the Wikipedia page. What can go wrong?

`nc chal.hkcert22.pwnable.hk 28021`

### Given Writeup

- https://hackmd.io/@blackb6a/hkcert-ctf-2022-i-en-3f8a9ef6#%E6%B5%B7%E5%B1%B1%E6%A8%93--Flawed-ElGamal-Crypto

### Attachment

- [elgamal_0463dd0701797c02de46bae07b26de2e.zip](https://github.com/T0x1cL/t0x1cl.github.io/raw/writeup/elgamal_0463dd0701797c02de46bae07b26de2e.zip)

---

- When you `nc chal.hkcert22.pwnable.hk 28021`, you get something like this:  
> c1 = 699544092687287445486787072698963098701615751701551173940663224415258564466897694438047546231947352178068300366945985078603626175281352727928713366032872  
c2 = 116627313506287897522563682613789057558267825740474021763338761932096116163078336002567378972587396451867870967898923226631496151926080359403341514030971465716775859745560604885344264400177437106237028867750058103876300890036458151117377913786779883385567068914006981510853929891193818594278267724665386  
- You really only need the `c2` that it gives you, because `m = gcd(c2, c2', c2'', ...)` as given by writeup. I `nc` it 10 times 
- Once you have the `m` you can get the flag by using `int.to_bytes`.  

---

## Script Used
see `solve.py`

### Output
`b'\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00hkcert22{4nd_th1s_t1m3_7h3_i5su3_1s_s0l31y_n0t_t4k1n9_m0du10s}'`

---
## Flag
hkcert22{4nd_th1s_t1m3_7h3_i5su3_1s_s0l31y_n0t_t4k1n9_m0du10s}
