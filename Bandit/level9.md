# 💥 Level 9 💥

## Meta de nivel
La contraseña para el siguiente nivel se almacena en el archivo data.txt en una de las pocas cadenas legibles por humanos, precedida por varios caracteres '='.

Comandos que puedes necesitar para resolver este nivel:
**grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd**

## Solucion

Primero analizamos si el archivo data se encuentra donde estamos ubicados:

```bash
bandit9@bandit:~$ ls
data.txt
```

por curiosidad decidi ver que contenia el archivo data con el comando cat:

```bash
bandit9@bandit:~$ cat data.txt
�&��,���P�
          vE��ݮ()�&�&�a���U��;��\E�`r��(�/�@�
                                             ��8n������7�N��\YXm�[��1�9���Kx wh�9�R���E��LrL�}��?J�rA~�?��Ł7��G�8'��=� 
                                       .?=Dm�%�|kXq<-ް7aN�[���(�C����Q�ZPI�4Y#��v����^_�[�QH}(�WX6��Nu��%�.D���ȁ�0ݔX�����)o����/�
                                                B7�oZ�O&A=n����q�z3E��@&�F(\��RN�{�C��H��A��=Э~v2��HA����<miQ�ys"EA�|׹<��I
                                          (,�SV^*\M����5�T�(�2�`Y`�B'h��:U�.L��KM|@�"C���W��nԎ��4�w6����H^��Qc�5========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
�Ր��l�;�m�KETyب��J4���	�`���Q���E�3nM�E9��i"\PE����L1yR;�5�����@�#)P��$
                                                                        ��{R��yb���Pg�zaVJ�p�c���
b�F3&3?k��2�ީ��
              є�cy�J�p��Q��5����n�ن�A �Q�K�W>D|���p�-E�I��jf�R��'��a����]5ɇ_��F��p�
�;�!�x!�ii�%_�L'��3ޡ���'�X�]c:��3����~��:���D?�(�b�aۤ�0��Hx�k̅��[7��[ڹ�ĉeIw�� i�"����jHna��hlꬰn�s�w��(�r`�&d�x� �4d�B�@����U�Y�t[Ǆc"�7�x'2�xG,�c�>�Lh		��+b��}vŰ7��&X��(�ɵ.���fa�(M�����u~+�)�A��rDA]|Ԇ7�]4J���
                                                       ��|Ǧ1�����G�xr��^˱_��r�ꤾ�o��eA`w�iq_M�xi7{C�f�cx!��3�&����*����
                                      l�U��N��
                                              <V��QD���J�qr[*fV�,��x�?���k5Z�c%���#r���Ĥ�Y��
���˽z0{�!
����8ǊA`�X�7S�1���\6�<y_���⇮=XX�]��\<�Қ6(�ӫ��-Py�	����x?�.@�=*^Y�G0��D���>�+N=
    �޺�D��5#_p0�i�&~e+]t�d�-�z/��
                                 ���i�M��~Ry�HP۞�N�ǃ����
                                                        �n�&+��8� �0�<�$M7�i#z�na���,�Ɋ��!i�
/"<����R�s���i�~��C�=�cd�Yw<��5C/��a�a�'&�M�=L3jT���~��o��6,"y�x�tY
5�������/��+e�FC)�g���Ւh��������/)��H�`o�8M�[�f@ݬ/#�r���fG��
���r���"g���%��`E��
��T�w��5�{>uַ�4��)���jěl5�L�D0m����)ٖ_��<���>Ɛ�H�:�.���ܒ��B�8
�A��H�T�a�iI;��y�$��uI�qu��K���l�/���P������U?��CF�:L�������)�PB>����d��&
                                                                         ���+$_r��̚��טS�i���č#*2�w�MF�#P[y"�i�^�#�!�0d�K/3��Q_r���D?²

l�~"Qxs�,�es�z��/�jਉ��(`sѿT�����t���G��JĿ��>sH}��wp[g���e��OG3
                                                ?9�B��
                                                      ��v۷���E<*,�<���
jdu#�D���r�~�� �2�D��'���eh�N�                                        �B[�����6
                              mx�u�F*��
                                       aΉ�z'f��Q��7��H��ciӿ���<б�;�u�SA��}Gr��?c/��Tɖ6��x0�X�6�g��Q��C�3��2{$�G-����p�פ���݋d���ɂ��N�Nb�
��!N���$��F�^Y��0�#������
,�s�~/�@l�<thy�啒�b�xKJ�o<��
��f�5jf
��e'㯻���^B��VV����)Z=�7	+�3Q�h��gj;�҉�����*ҟh�WDS��L9�+/$�z���E�u���%�|T��'����f����,�����eL��� K����C����SRRބ]z��Ճ5Ϯ���#�q
                                                  ����B�;�b7��(X�T�t.w'6(�'�bi~X�&Ec��dCB�Tn����]�L�N񯨟v]p�J��@I��띪��@�0x@�Gs��jڵ"#"�h�3�r�P����3{Ua-����_���O��wߵ�
   0/aJ���[��+={�:�a�#TpaR�~���E�e�h�%M
                                       _��1���n�\�ǘ����)�TE�;�-�id�3�k<=,�?p��0��
 �*)Q���So��`��Zs��)9Á�w������X�i^q�	TVi~��CU���"���˻��Z�C��*�9?��|����k��qۢ���S']TS�}�Hn���Z��}��t�,�
                        ��7��R)n����g��i��B��Y�7�jE̯�
D.R�.t��%����M��s*DUU麟��2�p	��f3�H�I��V�}��c�Վ
T��)�H.��c!     �0�%t9�ͦ|��YG��Չߺ1��n~,mL�&T���P��Y[����1�T�8�hWy5�y�ʚU
�C�	A#�Ԕ=#�G��ˊߪx��D�l��w0m~V}�YI=��Mf&B��n)ح�-͞����%��%ɕ��6�jU�9%�q�j5��bݘ
��͘�h>��T��+2��ft��u�u���a�&�b�rߛ�Ƿ0U-��7
[Ꮬ@�����wȟ��Ek[��$'�f���]���q=�Q��Υ&'��ֵrӘkL�,��ix�p
�[�5Y/N��K{�!Ζ`���Mۃ� �+=NBf�o� �7+E@��7E�|�8��&�ᨀ[�E�+�j��q�����
                                                                 (
                                                                  ����N�Uv�����Ň�8��Lݕ�ӡ��v�
            =��
               [Y� �Z�Ր�M�C��o��&	ٱA]VDa��~j��P��/�X�c/�~���c��`�onFг��$7� e�����AȳQ�ӣ�v�}��*&�K��ڭ<n̿?q��~
                                � �-��W�~
�v���*%>Lt(��C��
```

aunque a simple vista podemos ver la bandera, la idea es que usemos comandos para analizar el archivo, ya que no siempre contaremos con esta suerte y es mejor saber para que sirve y como usar una herramienta que nos ayude.

Usaremos el comando string para extreer lo que sea legible para un humano:

```bash
bandit9@bandit:~$ strings data.txt 
{7(b
FB`=
F`qYJ
%I"r
~5m~
iy\3
L^G^
@shLq
tC5!
G	2)
lHQS
5@8Y;)$X
c\5D=
7r}Q
TN#,p
b5A5
o 3`
hvSB
========== the
(V_g
{"%z
yzJq
%x"R
{n?a
jSBk
&F0N
Neb!
F3O*
b%LF
S)~i
d>",
X<8Yz3
^j?M
3`?;c
W`m	
[YK 
FrJUmX
?/=l
JGL;7
Y)FR9|
v(&N'
0w'F
 "|h	
+$)#
v0s@W
#N-Gnw
sv@q
1V*:
N~NP
f-Mw
=Uc1
=vG*2P
j\GX
2	#b
ExfpP
d2IO1 
({";
h]mjA
9G((
h?Du'
R-;'
t@&c]
1$[{
========== password
LjvU
LN<%|v.
Ol3Bl
VP+r
]f*k
&.2F
z>Sur
2*w?
e~WBf\
>(Xg9
xP:*
)jQzl
z@X91
S(^8
(>78
pDZ{
@xubd
k=ezG
(KcV
E========== is
pz]p{
;4r2 
chOw
>NBi
g	a}
:9[-i
Sz9E
3F~I
dmMI.
5.}HA+]
,usX%
#U:L>
/K@@
)[f+T
W.N0
l&zX
?XpV
!DSx
(]PO:)
yVq\
O,Rl
".`M
<bf2c~?I
	oKa
xZ@S
xLr0
";~($
L }j
k;J+o
Ty>~
a%}(
 ab$2
*sK^B
tHc?
W~~w
{4X){
^l,A
8Y84
q0Io@
m,>`h
6bp:((
3)]	
!$WkMi
\S\L
.l$0N
S,i7V
m2^^
xc+O
h&"Yf
J9XFq
!.F<
uqi(
2q<m
cjay
f))xf
8u^*Z
FJOG
^@Ut
W(]XpT[%
	P%O
\a{8qD
t%{	
r9<o
wW/c
H3ih1&&aN
{0DzD7
v2's
kgY2
vxw-
>#3&
U18<
pV5E
]UXZo
[5fc
>255
A(z/s
R9gt
Q`	\
!u)c
/r6W
@}!5wS
m}l9
${v/
~t2 
dPFER
Co{z/vw
&GU7?
n$}3
u_?;R
{)_uqt<L
j>y(
~'m"
%4nOv
{5N]_
Ga_SL
yII5w
:Xf+1
B+6,
=%r_
w``/iw
UV>)
qsAL
ap,U
\KZK
;9pM
l,);J
-B$y
[a[1n
cz+X
\YXm
L;p`Y
Kx wh
.?=Dm
|kXq<-
QH}(
O&A=n
<miQ
^*\M
5========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
KETy
L1yR;
zaVJ
F3&3?k
W>D|
FY!<v
d4dB$mU-R
jHna
Lh		
rDA]|
xi7{C
qr[*
C?OK+7
=*^Y
5#_p0
e+]t
=L3jT
6,"y
+$_r
#P[y"
s" dp
wp[g
~"Qxs
>sH}
E<*,
jdu#
l52	
#gJ'
<thy
t.w'6(
3{Ua-
0/aJ
#TpaR
q<=,
	TVi~
S']TS
*DUU
n~,mL
hWy5
w0m~V}
Mf&B
'QHE=
CU_:
s$}b
p6^P
!RBHA
5Y/N
+=NBf
7+E@
A]VDa
*%>L
;j:I
```

aunque ya es un poco mas facil de ver, podemos hacerlo aun mas, con la pista que nos dieron:

```bash
bandit9@bandit:~$ strings data.txt | grep "==="
========== the
========== password
E========== is
5========== Bandera: Descrubela tu!
bandit9@bandit:~$ 
```






