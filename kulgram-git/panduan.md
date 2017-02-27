# Panduan Github

### Clone dulu projectnya, dengan perintah ini :

```
> git clone https://github.com/iprakom/kulgram-git
```

isikan username dan password untuk akun di github.com

### buat nama panggilan sebagai nama file, diikuti dengan md, contoh: tamami.md, isinya nama dan instansi, contoh :

```
---
layout: page
nama: Tamami
instansi: BPPKAD Kab. Brebes
---
```

Identifier seperti `layout`,`nama`, dan `instansi` huruf kecil semua.

### periksa bahwa perubahannya telah dideteksi oleh git dengan perintah :

```
> git status
```

### Pindahkan nama file yang sudah dibuat ke status staged dengan perintah :

```
> git add tamami.md
```

### lakukan commit untuk file tamami.md

```
> git commit -m "pertama commit"
```

### lakukan push ke github dengan perintah berikut :

```
> git push -u origin master
```

### seharusnya file yang di commit sudah ada di github. selesai.
