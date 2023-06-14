# **FORTUNE COOKIES**
Cookie injection adalah serangan yang dilakukan dengan menyisipkan atau memanipulasi nilai cookie pada permintaan HTTP yang dikirimkan ke server. 
## **About the challenge**
Pada Challenge ini, Probleset meminta pemain untuk mencuri cookies dari sebuah website.

![cookies1](./image/cookies1.PNG)
## **Solution**
- Masuk ke website yang telah diberikan oleh probleset
- click Get your fortune 
- Buka inspect element, cari network lalu cari set cookies
- Saya melihat flag=0 yang nilainya false sehingga bisa diganti nilainya menjadi True
- Download Cookies editor di chrome extension/web app store
- Ganti value dari flag dari 0 menjadi 1
- Save, lalu reload page dari website tersebut
- And we got flag
```
ForestyHC{here_is_your_fortun3_cookie_4a0a47}
```
