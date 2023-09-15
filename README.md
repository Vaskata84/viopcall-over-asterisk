# SimpleVoipCallOverAsterisk
voip call over astersik on linux with zoiper android client

## 1. install asterisk on ubuntu
``` sudo apt install asterisk dahdi libpri1.4 ```



## 2. config astersik 
you can read zoiper documentation  [Zoiper](https://www.zoiper.com/downloads/documentation/How_to_place_video_calls_with_Zoiper3.pdf).




copy following code into ```/etc/astersik/sip.conf```
```
[general]
context=default
allowoverlap=no
bindaddr=0.0.0.0
srvlookup=yes
videosupport=yes

[Vasko]
type=friend
username=vasko
callerid="Vasil Dobchev"<7001>
secret=password
host=dynamic
context=ztest
disallow=all
allow=ulaw
allow=alaw
canreinvite=no
qualify=yes
dtmfmode=auto
allow=h263p
allow=h264
allow=vp8
videosupport=yes

[Toshko]
type=friend
username=Toshko
callerid="Toshko Kolev"<7002>
secret=password
hosT=dynamic
context=ztest
disallow=all
allow=ulaw
allow=alaw
canreinvite=no
qualify=yes
dtmfmode=auto
allow=h263p
allow=h264
allow=vp8
videosupport=yes

```


then copy this to ``` /etc/asterisk/extensions.conf ```




```

[general]
static=yes
writeprotect=no
clearglobalvars=no
[ztest]
exten => 7001,1,Dial(SIP/Vasko)  
exten => 7002,1,Dial(SIP/Toshko)
```

## 3. config zoiper on android
we need 2 android phone  . first install zoiper from google play.


open zoiper -> config -> Account -> Add account -> Yes -> Manua configuration -> SIP 

>phone 1 : 
```
Account name : Vasko
Host : <linux ip>
Username : Vasko
Password : password
```



>phone 2 : 
```
Account name : Toshko
Host : <linux ip>
Username : Toshko
Password : password
```

congratulation :)
 
 if you do tutoial step by step correct , you can simply call from alireza to elyas by dialing 7002 or wiceversa

**make sure all devices on same network**
