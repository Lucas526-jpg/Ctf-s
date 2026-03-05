# 💥 Level 15 💥

## Meta de nivel
La contraseña para el siguiente nivel se puede recuperar enviando la contraseña del nivel actual al puerto 30001 en el host local usando encriptación SSL/TLS.

Nota útil: ¿Está obteniendo "TERMINADO", "RENEGOCIANDO" o "ACTUALIZANDO"? Lea la sección "COMANDOS CONECTADOS" en la página de manual.

Comandos que puedes necesitar para resolver este nivel:
ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss

## Solucion

Para esto, seguimos un poco la logica del nivel anterior, solo que esta vez con la encriptacion ssl, para eso, usaremos openssl s_client que es como la conexion de nc pero con encriptacion:

```bash
bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
Can't use SSL_get_servername
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
SSL handshake has read 2103 bytes and written 373 bytes
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
    Session-ID: EBA4ECFE38937E98C703F8603CC0DE8727B2D39B49F5B2BA1357DB0FB62F8B53
    Session-ID-ctx: 
    Resumption PSK: CBB05EF614EACBE9B584B3F5FA2B9905D2C983A36D705FECE2AB63CDD24FB0671BDB4DEC8EAE19831A258BC13F24CEB0
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 3b b6 1d 68 dd 14 e9 df-4f e6 32 c2 6f 13 ab bd   ;..h....O.2.o...
    0010 - 73 c8 e5 bb 99 46 22 e8-b7 09 c9 da 31 c8 6d 56   s....F".....1.mV
    0020 - f0 f6 f7 aa 82 f9 37 61-6d 64 e0 f2 90 85 32 53   ......7amd....2S
    0030 - 2f 09 a7 36 c1 0a fe 2c-b4 30 d8 6e 64 01 bc 1c   /..6...,.0.nd...
    0040 - 73 11 87 57 b2 fc 61 5a-52 e4 0e ba b1 6b b9 a4   s..W..aZR....k..
    0050 - f2 9f 66 73 fc 6f 34 11-e3 b6 85 89 5b 39 26 f4   ..fs.o4.....[9&.
    0060 - 88 fb b1 8f 47 63 6c 9d-ff 6e 5c b4 98 17 69 3a   ....Gcl..n\...i:
    0070 - 29 26 eb 99 26 91 7f 59-62 bc 7f 51 b6 9b 28 e0   )&..&..Yb..Q..(.
    0080 - 59 be e7 e7 5b 2b 27 0a-1b 59 19 61 0b 95 19 27   Y...[+'..Y.a...'
    0090 - 3e 83 14 5e a3 d4 7a 83-1d e8 15 42 88 10 0b e7   >..^..z....B....
    00a0 - 89 3c b8 96 1b 3e 9b 05-38 cd f6 7a 9d 10 12 15   .<...>..8..z....
    00b0 - 3e 94 a1 51 4c 53 83 11-64 36 9c 54 b2 1e 97 8b   >..QLS..d6.T....
    00c0 - 3e 8a 72 d4 0c 74 fa d1-a6 c1 e5 b9 b6 eb 15 08   >.r..t..........
    00d0 - 5f ff c4 c6 c2 7e a1 9b-1d 89 cf b5 04 e8 55 b4   _....~........U.

    Start Time: 1772469932
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
    Session-ID: 8D7022C368D33F9938547ED38BE615E3429BC7D8543C5FFD5809BE2C9C85DEA1
    Session-ID-ctx: 
    Resumption PSK: F0BA5645FDE90843A89BA635D26A6E6DDA03251D8C94ADEFF6C9A91A405AB9FFFCE73900740AE2D73285839CA22253BF
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 3b b6 1d 68 dd 14 e9 df-4f e6 32 c2 6f 13 ab bd   ;..h....O.2.o...
    0010 - 7b 04 e1 f2 ef 88 98 66-c8 c8 67 db 12 16 39 87   {......f..g...9.
    0020 - be 5b 41 eb a9 53 9c 5a-01 8e 4d 28 80 13 d8 d4   .[A..S.Z..M(....
    0030 - c5 47 ca 51 d6 dd 06 7a-94 69 fe ae aa 42 53 d3   .G.Q...z.i...BS.
    0040 - 5c 8b 8d 03 dc d5 7b 97-03 b6 7e 42 30 0f 7a cf   \.....{...~B0.z.
    0050 - 56 71 bd f5 99 82 0e 08-79 fd cc f6 76 95 3d db   Vq......y...v.=.
    0060 - 5e 32 b5 50 a5 b0 cf 25-71 7f eb 0d b6 ec dc e1   ^2.P...%q.......
    0070 - 39 c7 26 09 a9 06 49 67-47 d5 be a4 46 54 47 f9   9.&...IgG...FTG.
    0080 - 33 39 40 7b af f8 3c 30-92 ab ef 15 2c d6 eb 8a   39@{..<0....,...
    0090 - 6e 04 bc 3c d4 85 07 76-24 a9 94 ca 70 78 91 df   n..<...v$...px..
    00a0 - 06 08 29 27 72 1b 92 a5-03 74 22 93 bd 12 35 4d   ..)'r....t"...5M
    00b0 - 96 a9 bf 03 74 70 50 71-30 40 95 e7 d5 6d 5c 13   ....tpPq0@...m\.
    00c0 - 00 23 4f 18 6e ff 8d fc-86 32 53 6f 51 a0 2c ed   .#O.n....2SoQ.,.
    00d0 - d7 68 48 0a ae 89 df 68-6d 62 0d 92 58 d1 7d 40   .hH....hmb..X.}@

    Start Time: 1772469932
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
```
 
Al poner la contraseña de este nivel, nos dara el sfiguiente mensaje:

```bash
Correct!
Bandera: Descrubela tu!

closed
bandit15@bandit:~$ 
```
