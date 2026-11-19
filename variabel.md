# Variabel 
Adalah Sebuah Properti Custom Yang Bisa Menyimpan Sebuah Nilai Mau itu warna Atau Ukuran `px`.

> Apa Maksudnya Properti Custom
>
> # Properti custom Adalah Sebuah Properti yang Bisa Dibuat Namanya Sesuka Hati . Ini Menurut Gw Btw

Menurut Ai

# Apa Itu "Properti Custom"?

**Properti custom** (*custom property*) artinya **properti CSS buatanmu sendiri**.

## Properti Biasa vs Properti Custom

CSS punya banyak properti bawaan yang sudah ditentukan browser, seperti `color`, `margin`, `font-size`, dan `background`. Kamu tidak bisa mengubah arti properti-properti itu.

Properti custom adalah properti yang **namanya kamu tentukan sendiri**. Browser tidak tahu apa fungsinya, jadi ia tidak mengubah tampilan apa pun secara langsung. Ia hanya menyimpan nilai untuk kamu pakai di tempat lain.

```css
.kotak {
  color: red;            /* properti bawaan: browser tahu artinya */
  --warna-favorit: red;  /* properti custom: nama buatan sendiri */
}
```

Baris `color: red` langsung mewarnai teks. Baris `--warna-favorit: red` tidak mewarnai apa-apa, sampai kamu memanggilnya:

```css
.kotak {
  --warna-favorit: red;
  border: 2px solid var(--warna-favorit);
}
```

## Kenapa Disebut "Properti" dan Bukan "Variabel"?

Karena cara penulisannya sama persis dengan properti CSS biasa: `nama: nilai;`. Bedanya hanya nama yang diawali dua tanda hubung (`--`).

Istilah **"variabel CSS"** adalah sebutan sehari-hari yang lebih mudah diingat, sedangkan **"custom properties"** adalah nama resmi di spesifikasi CSS. Keduanya merujuk pada hal yang sama.

## Analogi Sederhana

Bayangkan buku resep:

- **Properti bawaan** seperti bahan standar yang semua orang kenal: garam, gula, tepung.
- **Properti custom** seperti "bumbu rahasia" yang kamu racik dan beri nama sendiri, misalnya `--bumbu-andalan`. Setelah dibuat, kamu bisa memakainya di banyak resep tanpa menulis ulang racikannya.

## Aturan Penamaan

Nama harus diawali `--`, selebihnya bebas:

```css
:root {
  --warna-utama: #3b82f6;   /* valid */
  --ukuran-judul: 2rem;     /* valid */
  warna-utama: #3b82f6;     /* tidak valid sebagai custom property (tanpa --) */
}
```


# Berikut Adalah Cara Pakenya

# Cara Pakai Variabel CSS

Intinya cuma **dua langkah**: **buat** dulu, lalu **pakai**.

## Langkah 1: Buat (Deklarasi)

Tulis nama berawalan `--`, lalu nilainya. Biasanya ditaruh di `:root` supaya bisa dipakai di mana saja:

```css
:root {
  --warna-utama: #3b82f6;
  --jarak: 16px;
}
```

## Langkah 2: Pakai dengan `var()`

Panggil nama variabelnya di dalam `var()`:

```css
.tombol {
  background-color: var(--warna-utama);
  padding: var(--jarak);
}
```

Selesai. Setiap `var(--warna-utama)` akan diganti dengan `#3b82f6`.

## Contoh Lengkap yang Bisa Dicoba

Simpan sebagai file `.html` lalu buka di browser:

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    :root {
      --warna-utama: #3b82f6;
      --warna-teks: white;
      --jarak: 12px;
      --lengkung: 8px;
    }

    .tombol {
      background: var(--warna-utama);
      color: var(--warna-teks);
      padding: var(--jarak) calc(var(--jarak) * 2);
      border: none;
      border-radius: var(--lengkung);
    }

    .kotak {
      border: 2px solid var(--warna-utama);
      padding: var(--jarak);
      border-radius: var(--lengkung);
      margin-top: var(--jarak);
    }
  </style>
</head>
<body>
  <button class="tombol">Klik Saya</button>
  <div class="kotak">Ini sebuah kotak</div>
</body>
</html>
```

## Keuntungannya

Coba ubah satu baris saja:

```css
--warna-utama: #ef4444;
```

Tombol **dan** garis kotak langsung berubah jadi merah. Tanpa variabel, kamu harus mencari dan mengganti warna di setiap tempat.

## Tips Cepat

- **Taruh di `:root`** kalau mau dipakai di seluruh halaman.
- **Pakai fallback** untuk jaga-jaga: `var(--warna-utama, blue)`.
- **Nama bermakna**: `--warna-bahaya` lebih jelas daripada `--merah`.
- **Boleh ditimpa** di elemen tertentu:

```css
.tombol-bahaya {
  --warna-utama: #ef4444; /* hanya tombol ini yang merah */
}
```


# Ini Latihan Langsung gw Btw

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Aku Tydak Suka Femboy</h1>
    <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Deleniti qui eius vel nesciunt voluptatibus deserunt nostrum ad ratione doloribus? Est expedita ratione ullam voluptate voluptatum tempora, corporis explicabo qui laborum.</p>

    <div class="box">
        <h1>Halo Kamu suki Liar</h1>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Et distinctio dolores labore iusto aliquid neque?</p>
        <button>Kamu Gila</button>
    </div>
</body>
</html>
<style>

:root {
    --btnBackgroundColor: #0044ff;
    --backgroundColor: #9dff00;
    --color: #141414;
    --jarak: 20px;
}
.box {
    background-color: var(--backgroundColor);
    color: var(--color);
    padding: var(--jarak);
    border-radius: 10px;
}
.box button {
    background-color: var(--btnBackgroundColor);
    color: white;
    border: none;
    padding: var(--jarak);
    border-radius: 20px;
}
</style>
```
