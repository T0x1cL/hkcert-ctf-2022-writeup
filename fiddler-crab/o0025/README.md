fiddler-crab
===
## Summary
**Author:** harrier  
**Categories:** reverse, ★☆☆☆☆  
**Points:** 100

## Description

So you want to be a young GM... Maybe train yourself against this AI-assisted chess server?

Or you can just cheat? Winning this can make you win Magnus... Right?

P.S. The attachment is the same one from jumping-fish. You can just download it once.

`./chess-client chal.hkcert22.pwnable.hk:28046`

### Attachment

- [chess_4c333ec173e154a5101976cff17af195.zip](https://github.com/T0x1cL/t0x1cl.github.io/raw/writeup/chess_4c333ec173e154a5101976cff17af195.zip)



### Given Writeup

- https://hackmd.io/@blackb6a/hkcert-ctf-2022-i-en-3f8a9ef6#%E7%B1%B3%E5%9F%94%E8%87%AA%E7%84%B6%E8%AD%B7%E7%90%86%E5%8D%80--Fiddler-Crab-Reverse

---

- When using [tcpproxy](https://github.com/ickerwx/tcpproxy) to read the packets, you get something like  
 `rnbqkb1r/pppppppp/5n2/8/3P4/8/PPP1PPPP/RNBQKBNR w KQkq 0 1`  
  you can replace it with something like `rnbqkb1r/ppppp1pp/5n2/8/3P4/8/PPP1PPPP/RNBQKBN`
- And then I get stuck trying to replace `rnbqkbnr/pppp2pp/4pp2/8/3PP3/8/PPP2PPP/RNBQKBNR` with   
 `rnbqkbnr/ppppp2p/5p2/6p1/3P4/4P3/PPP2PPP/RNBQKBNR`, but it freezes up
- After some trial and error, I thought that you had to replace a piece with another piece or replace it with a 1, so i used
>```python tcpproxy.py -ti 43.198.35.216 -tp 28046 -lp 8000 -im replace:search=rnbqkb1r/pppppppp/5n2/8/3P4/8/PPP1PPPP/RNBQKBNR:replace=rnbqkb1r/ppppp1pp/5n2/8/3P4/8/PPP1PPPP/RNBQKBNR,replace:search=rnbqkb1r/ppppp3/6p1/8/3Pn3/8/PPP2PPP/RNB1KBNR:replace=rnbqkb1r/ppppp3/6p1/8/3PB3/8/PPP2PPP/RNB1KBNR,textdump -om textdump```
- once you win, you should get the flag in the command line

&#x200B;
- turns out it's because the length of the text you're replacing and the length of the text you're replacing it with must be the same  
- also it keeps increasing in RAM usage (possibly related to this: https://github.com/ggez/ggez/issues/1128 -harrier)
---
## Flag
hkcert22{m1tM-pr03y-c0u1d-h3lppp?e3en-st0ckf1sh15-c4n'7_w1n_u!!}

---
## Comments
- google en passant  
- holy hell
- (im pretty sure the bot player is stockfish?)
