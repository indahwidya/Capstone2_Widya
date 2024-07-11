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

### DATA CLEANSING
