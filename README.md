# Sisop-1-2024-MH-IT02
## Deskripsi Pengerjaan

Pertama, buka terminal linux dan masukkan command chmod +x Sandbox.csv untuk mengatur hak akses file. Selanjutnya kita akan menggunakancommand 'ls' untuk mengecek apakah file Sandbox.csv dan Sandbox.sh sudah tersedia. Jika sudah, selanjutnya kita akan memakai skrip ./Sandbox.sh untuk menjalankan hak akses dari file tersebut.

## Penjelasan

### wget --no-check-certificate 'https://drive.google.com/uc?export=download&id=1cC6MYBI3wRwDgqlFQE1OQUN83JAreId0' -O Sandbox.csv 

command  wget digunakan untuk mengunduh file Sandbox.csv, --no-check-certificate: digunakan supaya tidak perlu repot mengecek file sehingga proses mengunduh jadi lebih cepat, -O: Mengontrol nama file dari link yang di download

### ls 
untuk menampilkan daftar file dan direktori dalam sebuah direktori atau folder.

### cat Sandbox.csv 
menampilkan seluruh isi dari file Sandbox.csv ke layar/terminal.

### echo BUYER DENGAN SALES TERTINGGI 
command 'echo' berfungsi untuk menampilkan output ke layar
### awk -F ',' 'NR > 1  {sales[$6] += $17; if (sales[$6] > highest_sales) highest_sales = sales[$6]} END {for (buyer in sales) if (sales[buyer] == highest_sales) print buyer, sales[buyer]}' Sandbox.csv 
awk: perintah untuk menjalankan program AWK. 

-F ',':  menentukan pemisah field sebagai koma (,). Artinya, setiap baris input akan dipecah menjadi field-field yang dipisahkan oleh koma.

'NR > 1 { ... }': pola AWK yang hanya akan memproses baris-baris setelah baris pertama. Dengan kata lain, baris pertama (header) akan diabaikan.

sales[$6] += $17;: Untuk setiap baris yang diproses, kode ini akan menambahkan nilai dari field ke-17 ($17) ke dalam array sales dengan indeks yang sama dengan nilai field ke-6 ($6). Ini berarti nilai-nilai akan diakumulasikan berdasarkan nilai field ke-6. 

if (sales[$6] > highest_sales) highest_sales = sales[$6]: Setelah mengakumulasikan nilai, kode ini akan memeriksa apakah nilai yang baru diakumulasikan (sales[$6]) lebih besar dari nilai tertinggi yang ditemukan sebelumnya (highest_sales). Jika iya, maka highest_sales akan diperbarui dengan nilai baru tersebut.

END { ... }:  pola AWK yang akan dieksekusi setelah semua baris diproses.

for (buyer in sales) { ... }: Setelah semua baris diproses, kode ini akan melakukan iterasi melalui semua elemen dalam array sales.

if (sales[buyer] == highest_sales) print buyer, sales[buyer]: Untuk setiap elemen dalam array sales, kode ini akan memeriksa apakah nilainya sama dengan highest_sales. Jika iya, maka kode akan mencetak nama pembeli dan nilai akumulasi penjualan tertinggi.

Secara keseluruhan, kode AWK ini akan membaca file CSV, mengakumulasikan nilai penjualan untuk setiap pembeli, mencari nilai penjualan tertinggi, dan mencetak pembeli dengan nilai penjualan tertinggi beserta nilai penjualannya.

### echo BUYER DENGAN PROFIT TERENDAH 
'echo' menampilkan output pada layar

### awk -F ',' 'NR > 1 {profits[$6] += $20; if (profits[$6] < lowest_profit || lowest_profit == "") lowest_profit = profits[$6]} END {for (buyer in profits) if (profits[buyer] == lowest_profit) print buyer, profits[buyer]}' Sandbox.csv

-F ',': Opsi ini menyetel pemisah bidang ke koma

NR > 1: Kondisi ini memastikan bahwa skrip hanya memproses baris setelah baris pertama

profits[$6] += $20: Baris ini menambahkan nilai pada kolom ke-20 ke nilai pada kolom ke-6 setiap baris. Hasilnya disimpan dalam array, menggunakan nilai di kolom ke-6 sebagai indeks.profits

if (profits[$6] < lowest_profit || lowest_profit == "") lowest_profit = profits[$6]: Kondisi ini memeriksa apakah nilai saat ini dalam array lebih kecil dari variabel atau kosong. Jika salah satu kondisi benar, nilai saat ini dalam array ditetapkan ke .profitslowest_profitlowest_profitprofitslowest_profit

END {for (buyer in profits) if (profits[buyer] == lowest_profit) print buyer, profits[buyer]}: Blok ini dijalankan di akhir skrip. Command ini akan mengulangi array dan mencetak nama pembeli dan nilai keuntungan yang sesuai jika cocok dengan variabel.profitslowest_profit

Skrip AWK ini memproses file CSV dengan menambahkan nilai di kolom ke-20 ke nilai di kolom ke-6 untuk setiap baris, mencatat nilai keuntungan terendah, lalu mencetak nama pembeli dan nilai keuntungan yang sesuai jika cocok. nilai keuntungan terendah.

### echo TOP 3 CATEGORIES WITH HIGHEST PROFIT
### cut -d ',' -f 14,20 Sandbox.csv | sort -k20 -nr | head -3

Command cut -d ',' -f 14,20 Sandbox.csv mengambil baris dari file CSV Sandbox.csv yang memiliki data pada kolom ke-14 dan ke-20.

sort -k20 -nr mengurutkan data tersebut berdasarkan nilai pada kolom ke-20 dalam urutan negatif (descending order).

head -3 mengambil tiga baris teratas dari data yang telah diurutkan.

Secara keseluruhan, command ini akan mengambil tiga baris dari file CSV Sandbox.csv yang memiliki data pada kolom ke-14 dan ke-20, kemudian mengurutkan data berdasarkan nilai pada kolom ke-20 dalam urutan negatif, dan mengambil tiga baris teratas dari data yang telah diurutkan.

### echo MENCARI PURCHASE DATE DAN QUANTITY ATAS NAMA ADRIENS
### awk '/Adriaens/ {print}' Sandbox.csv

awk '/Adriaens/ {print}' Sandbox.csv akan membaca file Sandbox.csv baris per baris, dan mencetak setiap baris yang mengandung string "Adriaens" ke output standar (layar/terminal). 
