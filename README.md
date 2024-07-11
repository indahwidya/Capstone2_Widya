## TRANSAKSI TRANSJAKARTA : koridor dan halte Transjakarta yang mana saja yang padat beserta karakter penumpangnya saat hari kerja (weekday)

**PURWADHIKA JOB CONNECTOR DATA SCIENCE ONLINE LEARNING (JCDSOL-014) 2024**

Created by : Indah Widya Putri

**Analisis ini digunakan untuk membantu perusahaan untuk dapat menentukan strategi penambahan layanan (berbayar) dan promosi pada halte dan koridor yang memiliki jumlah pengguna yang tinggi berdasarkan karakter pengguna**

Dataset ini berisi informasi terkait informasi koridor Transjakarta, waktu tap-in dan tap-out, dan identitas pemegang kartu beserta jumlah harga tiket yang dibayar

DATABASE Fitur pada Transjakarta csv memiliki penjelasan sebagai berikut
* transID: Unique transaction id for every transaction
* payCardID: Customers main identifier. The card customers use as a ticket for entrance and exit.
* payCardBank: Customers card bank issuer name
* payCardName: Customers name that is embedded in the card.
* payCardSex: Customers sex that is embedded in the card
* payCardBirthDate: Customers birth year
* corridorID: Corridor ID / Route ID as key for route grouping.
* corridorName: Corridor Name / Route Name contains Start and Finish for each route.
* direction: 0 for Go, 1 for Back. Direction of the route.
* tapInStops: Tap In (entrance) Stops ID for identifying stops name
* tapInStopsName: Tap In (entrance) Stops Name where customers tap in.
* tapInStopsLat: Latitude of Tap In Stops
* tapInStopsLon: Longitude of Tap In Stops
* stopStartSeq: Sequence of the stops, 1st stop, 2nd stops etc. Related to direction.
* tapInTime: Time of tap in. Date and time
* tapOutStops: Tap Out (Exit) Stops ID for identifying stops name
* tapOutStopsName: Tap out (exit) Stops Name where customers tap out.
* tapOutStopsLat: Latitude of Tap Out Stops
* tapOutStopsLon: Longitude of Tap Out Stops
* stopEndSeq: Sequence of the stops, 1st stop, 2nd stops etc. Related to direction.
* tapOutTime: Time of tap out. Date and time
* payAmount: The number of what customers pay. Some are free. Some not.

## DATA UNDERSTANDING & DATA CLEANSING
Pada bagian ini dilakukan pembersihan database Transjakarta.csv (raw database) dengan menghilangkan missing values dan menghapus fitur yang tidak relevan sebagai pendukung analisis
### Missing Value
Bagian ini merupakan langkah untuk menghilangkan missing value (NaN) dari fitur-fitur sebagai berikut
#### corridorID & corridorName
Pada tahap ini, terdapat keterkaitan antara kedua fitur sehingga dapat dilakukan pengisian value yang kosong dengan value yang sama di kolom lainnya. Pengisian missing value di corridorName bertujuan untuk mengurangi persentase missing value, sehingga mengurangi baris missing value yang harus dihapus. Setelah melakukan pengisian sebagian, dilakukan penghapusan baris yang masih memiliki missing value (NaN)
#### payAmount
payAmount memiliki persentase missing value yang kecil, sehingga baris yang kosong bisa langsung dihapus
#### tapInStops & stopEndSeq
Kedua fitur ini apabila dihapus baris yang memiliki missing value dikhawatirkan akan mengurangi jumlah data yang dapat dianalisis sehingga mengurangi keakuratan data, untuk itu kedua fitur ini tidak di hapus satu baris melainkan menghilangkan kolom fitur tapInStops & stopEndSeq. Karena selain mengandung missing value, fitur ini juga tidak digunakan untuk analisis
#### tapOutStops, tapOutStopsName, tapOutStopsLat, tapOutStopsLon, dan tapOutTime
Sama halnya dengan kedua fitur diatas, fitur tapOutStops, tapOutStopsName, tapOutStopsLat, tapOutStopsLon, dan tapOutTime ini juga apabila dihapus baris yang memiliki missing value dikhawatirkan akan mengurangi jumlah data yang dapat dianalisis sehingga mengurangi keakuratan data, untuk itu fitur-fitur ini tidak di hapus satu baris melainkan menghilangkan kolom fitur. Karena selain mengandung missing value, fitur ini juga tidak digunakan untuk analisis 
### Data yang tidak relevan
Bagian ini adalah langkah untuk menghapus kolom fitur yang tidak terpakai untuk analisis
#### payCardID, direction, tapInStopsLat, tapInStopsLon, stopStartSeq
Fitur payCardID, direction, tapInStopsLat, tapInStopsLon, stopStartSeq tidak memiliki missing value tetapi fitur-fitur ini tidak memiliki relevansi untuk mendukung analisis pada masalah ini, jadi bisa langsung dihapus fiturnya
### Data yang sudah bersih
Database pada bagian ini merupakan data yang sudah bersih dari missing value dan fitur-fitur yang tidak memiliki relevansi, sehingga bisa digunakan. File data bersihnya dapat dicek di file Transjakarta (Clean).csv pada github ini
## DATA ANALYSIS
Data analisis yang dilakukan pada tahap ini difokuskan ke data di weekday untuk mengetahui halte, koridor dan karakter penumpang
### Berdasarkan tapInTime
Pada tahap ini digunakan fitur tapInTime untuk mengidentifikasi pada range jam berapa Transjakarta memiliki jumlah penumpang yang paling tinggi
### Berdasarkan transID dan corridorID
Pada tahap ini digunakan fitur transID dan corridorID untuk menentukan koridor mana saja yang memiliki jumlah penumpang yang paling tinggi berdasarkan banyaknya transID
### Berdasarkan payAmount
Tahap ini menggunakan fitur payAmount untuk memisahkan jenis layanan Transjakarta menjadi Transjakarta, Royaltrans, dan Mikrotrans karena ketiga layanan tersebut beda jumlah pembayarannya sehingga dapat dianalisis berdasarkan payAmount yang dikeluarkan
### Berdasarkan tapInStopsName
Tahap ini menggunakan fitur tapInStopsName untuk mengidentifikasi halte terpadat. Analisis ini menggunakan halte terpadat untuk dimanfaatkan ruangnya dalam pembukaan tenant, sehingga halte yang dipakai hanya yang memiliki jenis layanan Transjakarta dan Royaltrans, ini dapat dipisahkan menggunakan payAmount pada tahap sebelumnya
### Berdasarkan payCardName dan payCardBank
Pada tahap ini menggunakan fitur payCardName dan payCardBank untuk mencari sebaran jenis kartu pembayaran yang digunakan penumpang Transjakarta dalam jumlah persentase
### Berdasarkan payCardSex
Fitur payCardSex digunakan untuk mengetahui sebaran jenis kelamin di masing-masing koridor Transjakarta terpadat
### Berdasarkan payCardBirthDate
fitur payCardBirthDate digunakan pada tahap ini agar dapat mengidentifikasi median umur di koridor-koridor terpadat
## KESIMPULAN DAN REKOMENDASI
Kesimpulan yang didapatkan merupakan berasal dari data analisis yang dilakukan yang menjawab permasalahan yang ada. Berdasarkan kesimpulan tersebut akan didapatkan rekomendasi sebagai solusi untuk masalah yang dialami
