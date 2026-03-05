# 💥 Level 16 💥

## Meta de nivel
Las credenciales para el siguiente nivel se pueden obtener enviando la contraseña del nivel actual a un puerto del host local en el rango 31000 a 32000. Primero, averigüe cuáles de estos puertos tienen un servidor escuchando. Luego, determine cuáles admiten SSL/TLS y cuáles no. Solo un servidor proporcionará las siguientes credenciales; los demás simplemente le enviarán lo que usted les envíe.

Nota útil: ¿Está obteniendo "TERMINADO", "RENEGOCIANDO" o "ACTUALIZANDO"? Lea la sección "COMANDOS CONECTADOS" en la página de manual.

Comandos que puedes necesitar para resolver este nivel:
**ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss**

## Solucion

Primero analizamos cuales puertos estan abiertos entre 31000 y 32000:

```bash
bandit16@bandit:~$ nmap -p 31000-32000 localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2026-03-02 16:49 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00027s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.08 seconds
bandit16@bandit:~$ 
```

Una vez que tenemos los puertos, analizamos cual de todos admiten ssl:

```bash
bandit16@bandit:~$ openssl s_client -connect localhost:31691 -servername locahost
CONNECTED(00000003)
4087F0F7FF7F0000:error:0A0000F4:SSL routines:ossl_statem_client_read_transition:unexpected message:../ssl/statem/statem_clnt.c:398:
---
no peer certificate available
---
No client certificate CA names sent
---
SSL handshake has read 310 bytes and written 317 bytes
Verification: OK
---
New, (NONE), Cipher is (NONE)
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 0 (ok)
---
```

En este puerto podemos ver que no es admitido, analizamos el siguiente:

```bash
bandit16@bandit:~$ openssl s_client -connect localhost:31790 -servername locahost
CONNECTED(00000003)
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
---
Certificate chain
 0 s:CN = SnakeOil
   i:CN = SnakeOil
   a:PKEY: rsaEncryption, 4096 (bit); sigalg: RSA-SHA256
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN = SnakeOil
issuer=CN = SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2107 bytes and written 390 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 4096 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: A54350517124D1485AFE467DEAA63F66D29A7EB2BB709AC7ABCAFF1F70F97D29
    Session-ID-ctx: 
    Resumption PSK: D042F1A0F547C2CCE1A6D2F570374BD98D098E8B6201EFCB8A1D1BAD2A27EB95D58DC1340A37044A20B9D2270CE9C365
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 9d f6 52 f9 df 97 90 d7-e4 78 02 5f 2a dd 09 1a   ..R......x._*...
    0010 - 74 e5 d7 6a 9f 89 ad ef-a5 f6 22 5a 27 da b2 c2   t..j......"Z'...
    0020 - 68 92 08 cc ec d4 c2 44-e2 52 c6 6b d2 bb 7d 72   h......D.R.k..}r
    0030 - 1b 88 71 4b 4b f5 6d 21-93 bd 3b 65 9a 12 04 d1   ..qKK.m!..;e....
    0040 - dc f8 21 4b 5f b7 ab 8b-a1 e1 44 30 6c 74 fa 2f   ..!K_.....D0lt./
    0050 - f3 a2 04 2b 17 34 fb 7e-6d fd 84 8f e7 78 09 7c   ...+.4.~m....x.|
    0060 - fe 96 5b 91 76 89 67 0b-b3 a6 94 cc 8f f6 f9 00   ..[.v.g.........
    0070 - dd 6a e0 f6 b2 2c 2e d0-cc c2 49 73 3d ce dd 64   .j...,....Is=..d
    0080 - 66 a8 de ad fd bb 6e f8-d2 5b e7 62 eb 22 72 49   f.....n..[.b."rI
    0090 - 48 4d 49 60 8b 9a 7c 52-71 64 de a0 0f 14 be 9b   HMI`..|Rqd......
    00a0 - be 6b 47 a5 7a cb a2 0f-4b 4d d7 97 06 45 03 ce   .kG.z...KM...E..
    00b0 - d1 cb f5 32 59 45 c7 a7-db ec 49 d5 1c 6f af 50   ...2YE....I..o.P
    00c0 - 8f 47 5d 9e 3c d5 9e 45-13 49 68 2b 35 7f 07 7a   .G].<..E.Ih+5..z
    00d0 - aa e2 d9 26 dc d9 a0 89-51 2b db 56 53 bf 11 43   ...&....Q+.VS..C
    00e0 - 49 4f cb b9 fc fd 94 e2-7c c6 08 5d 2d 38 30 2b   IO......|..]-80+

    Start Time: 1772470439
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 5637D38CE7B0832B4A058628C444D2EB29C7D2D774B7C9A2BB8ED82AB5B8C175
    Session-ID-ctx: 
    Resumption PSK: C564153A81C4BDC85999ABF2343BF7B034A5BA056B341A80F971F6B1F8AFA6448C1BD9E3442F0F75DFD99E80B8C3D134
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 9d f6 52 f9 df 97 90 d7-e4 78 02 5f 2a dd 09 1a   ..R......x._*...
    0010 - 30 83 0b 6e f2 b4 0d 37-7e 5b 5c 19 7d 47 74 f5   0..n...7~[\.}Gt.
    0020 - 6c 2e 1c 2e 02 14 1b f8-f3 95 a8 59 b9 c3 9b 48   l..........Y...H
    0030 - 21 46 49 4b c1 cb 4c 5d-4d fb 61 94 b2 cd a5 b2   !FIK..L]M.a.....
    0040 - fb 64 f9 60 6b e5 8c d7-e2 d5 75 f3 f0 7a 73 28   .d.`k.....u..zs(
    0050 - e2 51 54 41 87 4b 72 41-5e 24 d1 fc b3 cb 99 02   .QTA.KrA^$......
    0060 - 28 36 29 40 82 a4 87 ae-6a 62 4f db 86 c8 b8 93   (6)@....jbO.....
    0070 - 22 68 12 31 1b 58 a4 fc-f0 82 cb c8 a0 a6 00 67   "h.1.X.........g
    0080 - 65 2b 44 2f 80 61 a0 70-68 aa d4 f4 30 b9 ab 62   e+D/.a.ph...0..b
    0090 - 14 2e fd 9d 90 2f a5 d2-db 99 40 3d b4 ab f6 67   ...../....@=...g
    00a0 - f5 f1 3d 0a a0 53 86 9f-38 53 2e 55 44 45 a8 6a   ..=..S..8S.UDE.j
    00b0 - 90 26 11 3a 6c 3e a7 13-95 76 d4 27 0c f2 cd 4f   .&.:l>...v.'...O
    00c0 - eb 37 08 60 df 5d 1c 19-1e 72 35 3e d4 ff 26 04   .7.`.]...r5>..&.
    00d0 - 89 0a c2 d3 c2 64 bb de-95 95 be 9e b0 c7 7a 51   .....d........zQ
    00e0 - 66 c4 df f9 ef 9a 1a de-ed 67 eb 93 cf 50 0b 35   f........g...P.5

    Start Time: 1772470439
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
CONTRASEÑA
KEYUPDATE

Wrong! Please enter the correct current password.
closed
```

Como podemos ver, este es una posibilidad, intente poner la contraseña pero me dio error, intenrare con el sigiuente:

```bash
bandit16@bandit:~$ openssl s_client -connect localhost:31960 -servername locahost
CONNECTED(00000003)
4087F0F7FF7F0000:error:0A0000F4:SSL routines:ossl_statem_client_read_transition:unexpected message:../ssl/statem/statem_clnt.c:398:
---
no peer certificate available
---
No client certificate CA names sent
---
SSL handshake has read 310 bytes and written 317 bytes
Verification: OK
---
New, (NONE), Cipher is (NONE)
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 0 (ok)
---
```

Este no es, el siguiente:

```bash
bandit16@bandit:~$ openssl s_client -connect localhost:31790 -servername locahost
CONNECTED(00000003)
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
---
Certificate chain
 0 s:CN = SnakeOil
   i:CN = SnakeOil
   a:PKEY: rsaEncryption, 4096 (bit); sigalg: RSA-SHA256
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN = SnakeOil
issuer=CN = SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2107 bytes and written 390 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 4096 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 3DB076A43C4EDE39F98CF52E0DD5C2F5D0E0FF83CD0CAE5BC9312DF92A1AD9D7
    Session-ID-ctx: 
    Resumption PSK: 3A10CD2E9BA472B5FF720A5318F5AE3506CDE8812971D0A126C1CC59C3FB771E000EB2DE6A87167B0D2C93044D3CB767
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 9d f6 52 f9 df 97 90 d7-e4 78 02 5f 2a dd 09 1a   ..R......x._*...
    0010 - 2b 0b 54 9f 18 cd 4f 2c-31 dc f2 5f 0f 36 3d 87   +.T...O,1.._.6=.
    0020 - 33 6e 3f 59 9c cb 97 38-ec 86 f1 73 c6 e9 df 85   3n?Y...8...s....
    0030 - 92 53 a8 e1 f3 40 92 d3-b1 46 99 31 61 af 45 87   .S...@...F.1a.E.
    0040 - b1 45 3b 43 6e 40 47 8b-25 a1 0c 84 59 6d ac 77   .E;Cn@G.%...Ym.w
    0050 - 89 0e 88 74 b7 9e a5 38-dd e7 5c d6 a5 bc a5 eb   ...t...8..\.....
    0060 - 04 a8 8c b7 ab 3c ba f4-3e 00 a3 cc a2 e8 d0 28   .....<..>......(
    0070 - 9d 61 ba a9 39 b9 f1 ea-59 16 b1 5c 33 1a 67 c5   .a..9...Y..\3.g.
    0080 - 64 35 5a 1b 63 f8 2d 8c-dc 3d 3a b4 1b ad 0c cd   d5Z.c.-..=:.....
    0090 - ed 12 82 cc a7 a5 97 bc-86 12 c9 71 2b 33 29 d9   ...........q+3).
    00a0 - e1 28 6b 33 ce 53 a8 09-7a e9 24 1a c4 54 01 10   .(k3.S..z.$..T..
    00b0 - c7 76 51 f3 46 2a 9c 10-21 bf 1b 69 32 55 e0 a7   .vQ.F*..!..i2U..
    00c0 - 8c 21 80 28 a5 44 ae 22-d4 79 7f d7 f6 c2 8a 98   .!.(.D.".y......
    00d0 - bc f1 dc 79 75 cf 3d cc-4d 5f f0 c2 d9 7b ed 5a   ...yu.=.M_...{.Z
    00e0 - 8a 2a 74 52 ce ff bb f3-23 f0 6c e1 2f 5f 69 f9   .*tR....#.l./_i.

    Start Time: 1772470492
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 94111AABFFE7E023282C294812DF38AFFD279750E9D979B6F35B6AEDF9524B07
    Session-ID-ctx: 
    Resumption PSK: A682163E0EAACF38F2799B9B7FA31455B94D03B91B6FD3F5454BFFAD1ED744FB3CBB764A975110356FF1141023EFBAF8
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 9d f6 52 f9 df 97 90 d7-e4 78 02 5f 2a dd 09 1a   ..R......x._*...
    0010 - 36 29 2d f7 8a 0d 68 2e-97 24 ab cf f9 b3 46 89   6)-...h..$....F.
    0020 - d0 23 d4 7f 85 19 a8 df-01 63 47 9f cb 1b 5c 37   .#.......cG...\7
    0030 - fc a6 1b c7 84 be 47 67-3a e4 ec 33 44 12 c6 25   ......Gg:..3D..%
    0040 - 39 5e e4 17 38 81 4e 4f-dc c2 fe 89 44 63 1e 36   9^..8.NO....Dc.6
    0050 - 56 b5 0b 5c 4a aa 8b c0-ee e1 f5 a9 86 06 20 52   V..\J......... R
    0060 - 2e 13 cd fb c6 fd a2 7f-05 4e 84 06 3f 31 c1 f8   .........N..?1..
    0070 - 0f 6d f2 bd ca 5d 0c c7-e9 e1 5e 68 eb 07 fb 41   .m...]....^h...A
    0080 - 5f 64 69 32 02 3e f0 8a-38 c0 b6 26 66 f6 77 1a   _di2.>..8..&f.w.
    0090 - f2 07 d4 63 66 45 d8 83-57 40 eb f3 47 ef 96 18   ...cfE..W@..G...
    00a0 - 40 a8 24 ac cf a1 47 67-d8 25 50 5d 17 fa 8d cd   @.$...Gg.%P]....
    00b0 - 62 33 33 ea 78 8b 6f 2a-11 ee 9f b8 74 61 32 6c   b33.x.o*....ta2l
    00c0 - 00 ab 61 2f 64 2a 69 ee-09 d9 3b 96 b0 54 6c 5c   ..a/d*i...;..Tl\
    00d0 - 20 c2 b2 ff aa 6f b2 28-f3 4b a6 fe 6c 31 fd 01    ....o.(.K..l1..
    00e0 - 71 1f 9b 0e 9d 82 c5 c8-5f 7d 5c 52 03 eb c4 2b   q......._}\R...+

    Start Time: 1772470492
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
CONTRASEÑA
KEYUPDATE
CONTRASEÑA
KEYUPDATE
CONTRASEÑA
KEYUPDATE
^C
```

Este tiene un comportamiento extraño, intento insertar la contraseña directamente desde un echo:

```bash
bandit16@bandit:~$ echo kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx | openssl s_client -connect localhost:31790 -servername locahost
CONNECTED(00000003)
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
---
Certificate chain
 0 s:CN = SnakeOil
   i:CN = SnakeOil
   a:PKEY: rsaEncryption, 4096 (bit); sigalg: RSA-SHA256
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN = SnakeOil
issuer=CN = SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2107 bytes and written 390 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 4096 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
KEYUPDATE
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: FA2697B9A5996508E1AF688FFDC9BB5DDF4C0DA6903CBBC27A356559DAAE79D5
    Session-ID-ctx: 
    Resumption PSK: 2CF89A65E6F08794D370E11250EBE9BFC4B68282D685CE889567501A7034219728AE4087E2DBA9F5CFB4F337602105BB
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 9d f6 52 f9 df 97 90 d7-e4 78 02 5f 2a dd 09 1a   ..R......x._*...
    0010 - f0 5a 5b a6 51 74 f3 f0-5e 66 cf d7 95 20 8e f2   .Z[.Qt..^f... ..
    0020 - 4d 64 92 23 ff da a1 fb-89 6c 75 60 8d 75 a1 9a   Md.#.....lu`.u..
    0030 - ff a7 d1 48 04 04 9a a0-26 91 98 90 01 be 69 61   ...H....&.....ia
    0040 - 87 5b fa a7 9b fd 8e a6-69 b4 2a 43 43 b3 ab 2d   .[......i.*CC..-
    0050 - b5 98 c8 37 f0 3d df 82-dd 6c 59 53 90 2f 99 c7   ...7.=...lYS./..
    0060 - 3e ec 32 34 ca 85 c9 a1-76 f6 09 7b 17 66 06 43   >.24....v..{.f.C
    0070 - c0 ef 28 6d f1 e8 c9 d8-ed a5 7f 4e 57 3c c4 c6   ..(m.......NW<..
    0080 - ea 53 8a 96 29 63 10 93-9b f6 ed 7d 08 53 ce f4   .S..)c.....}.S..
    0090 - e3 77 4a 8a dd a6 e2 9f-6e 21 83 8d 0a 87 e5 1d   .wJ.....n!......
    00a0 - 4d 19 4a 3a ee f1 e8 b2-21 c2 2e 71 2d 68 2f 37   M.J:....!..q-h/7
    00b0 - 62 8f 14 65 42 16 c5 d1-8d 9f cd b0 0a b5 a6 78   b..eB..........x
    00c0 - b8 e7 ad 28 94 dc 20 eb-6d 16 07 f2 32 65 c9 8c   ...(.. .m...2e..
    00d0 - 2b cb 9e c4 07 9e b4 ce-0b 07 15 f8 12 13 41 60   +.............A`
    00e0 - c7 51 25 a0 49 9a 23 71-fd b6 5a af 16 4b 92 18   .Q%.I.#q..Z..K..

    Start Time: 1772470526
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 240AA6257EE598BFF6CF795C40AD267DBA558FBF22D5E83EC3A043711953921C
    Session-ID-ctx: 
    Resumption PSK: B1F2896C94ACDAF23F18E8E5B933359E5E19DFADDB91C8BAF4A2A62338C94042EB1EA9C16FE856ED30D3AC4BA1635543
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 9d f6 52 f9 df 97 90 d7-e4 78 02 5f 2a dd 09 1a   ..R......x._*...
    0010 - ba a8 01 3d 33 a3 07 c7-b4 8f 1b 62 18 72 04 01   ...=3......b.r..
    0020 - 8b 4a 54 5f 51 77 53 f5-15 1b 75 2a e6 55 ed 8e   .JT_QwS...u*.U..
    0030 - 67 c6 c6 3c 9d be 13 5d-6f 6d 25 a4 3e 4c b8 43   g..<...]om%.>L.C
    0040 - 22 d1 54 b8 79 25 bc 18-ed 9b 7b 60 6d 37 08 ec   ".T.y%....{`m7..
    0050 - c2 bc ee b4 3a 68 fb 78-6d 47 42 dd 0f 84 20 07   ....:h.xmGB... .
    0060 - 59 21 e8 7b 47 64 63 56-35 7c 1b a2 a0 0e e0 85   Y!.{GdcV5|......
    0070 - 7c 82 3b 30 1b 4f 13 8e-e9 82 67 13 4a 62 cb f5   |.;0.O....g.Jb..
    0080 - 01 96 76 5b 97 af 49 a6-1f 32 e2 01 9c 11 bd 8f   ..v[..I..2......
    0090 - 6b 08 27 ea 77 35 31 8a-26 1a 1f 6b 16 be e7 01   k.'.w51.&..k....
    00a0 - 50 99 38 71 55 b4 e4 c1-5e ad 00 c3 55 4e 58 95   P.8qU...^...UNX.
    00b0 - cc 59 10 cd de e1 28 b6-51 15 6f ef 4f 15 e2 fe   .Y....(.Q.o.O...
    00c0 - c0 7e 67 56 95 f7 1d 7b-44 35 34 5c 53 0e 53 1b   .~gV...{D54\S.S.
    00d0 - 80 80 0d 5d 2c 48 94 10-fd e1 00 ff 26 1a 20 81   ...],H......&. .
    00e0 - 05 0c 41 2e 4f b1 c4 d4-af 6f ca 6c c1 8a 73 f4   ..A.O....o.l..s.

    Start Time: 1772470526
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
DONE
```

Sigue siendo algo extraño, aun no nos brinda la contraseña, investigando, al usar este tipo de comandos, es recomendable usar el parametro -quiet:

```bash
bandit16@bandit:~$ echo kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx | openssl s_client -connect localhost:31790 -servername locahost -quiet
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

bandit16@bandit:~$ 
```

Como podemos ver, nos dio una sshkey, con la cual deremos conectarnos por ssh al siguiente nivel con el parametro -i, para ello creo el archivo en mi computadora y le doy los permisos necesarios antes de ejecutar:

```bash
scar@scar:~$ cat > sshbandit17.private
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
scar@scar:~$ chmod 600 sshbandit17.private 
scar@scar:~$ ssh -i sshbandit17.private -p 2220 bandit17@bandit.labs.overthewire.org
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

```

