---
layout: post
title: Crawling Twitter
author: Noeraliza Widyara Aurell
categories: Crawling data
tags: Crawling
image: https://cdn.pixabay.com/photo/2014/09/18/19/47/stones-451329_960_720.jpg
beforetoc: Tahap Crawling Data Twitter
date: 2022-12-14 T20:50:00.102Z
featured: true
hidden: true
---
Tahap Crawling Data Twitter
Seperti yang sudah di bilang artikel kali ini kita akan mengcrawl tanpa menggunakan api, mungkin lain kali akan saya update jika sudah di terima oleh pihak twitter.

Terus apa saja tahapnya ?

Buka Jupyter Notebook
Pastikan kamu sudah menginstal jupyter dan juga python. Untuk download jupyter bisa melalui aplikasi anaconda yang sizenya mungkin sekitar 400 mb.

Buat File Baru

Kamu bisa membuat file baru dan di beri nama sesuka hati kamu. File ini nantinya berekstensi .ipynb karena untuk running nya kita menggunakan kernel.

Instal Twint
Caranya cukup mudah kamu tinggal memasukan kode di bawah ini.

!git clone --depth=1 https://github.com/twintproject/twint.git
%cd twint
!pip3 install . -r requirements.txt
Kemudian running dan tunggulah sebentar karena kernel sedang memproses biasanya memakan waktu sekitar beberapa detik.

Emm, kalau pada saat import twint mengalami error mungkin bisa tambahkan code berikut ini, kemudian running lah.

!pip install aiohttp==3.7.0
Mungkin kalau masih tidak bisa coba untuk membuat notebook baru.

Import Twint
Setelah menginstal twint tentunya belum bisa di jalankan karena kamu perlu menginportnya terlebih dahulu supaya twint bisa digunakan.

Caranya cukup mudah masukan saja kode di bawah ini.

import nest_asyncio
nest_asyncio.apply() #digunakan sekali untuk mengaktifkan tindakan serentak dalam notebook jupyter.
import twint #untuk import twint
Proses Ambil Data Twitter
Sudah import semuanya ? kini kamu tinggal menentukan data apa yang ingin di ambil. Kita ambil saja salah satu hastag yang sedang viral di twitter yaitu #NegeriPajak.

c = twint.Config()
c.Search = '#NegeriPajak'
c.Pandas = True
twint.run.Search(c)
Kemudian running kode tersebut maka akan muncul semua data yang ada di twitter khusunya yang berhastag #NegeriPajak.

Eksport Data Twitter

Kamu bisa juga mengeksport semua data tersebut ke csv. caranya kamu masukan kode di bawah ini untuk membuat tabelnya terlebih dahulu.

Tweets_df = twint.storage.panda.Tweets_df
Tweets_df.head()
Kemudian masukan kode di bawah ini untuk mengeksport ke dalam file berekstensi csv.

Tweets_df.to_csv("negeri_pajak.csv", index=False)
Dengan menggunakan fungsi to_csv maka kamu seharusnya berhasil mengeksport semua data tersebut. Dan untuk lokasi file kamu bisa cari pada lokasi yang sama dengan file ipynb kamu.
