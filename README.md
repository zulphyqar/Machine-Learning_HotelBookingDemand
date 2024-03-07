# Machine-Learning_HotelBookingDemand

## *1. BUSINESS PROBLEM UNDERSTANDING*

*Context:*

Pembatalan pemesanan merupakan aspek kunci dari manajemen pendapatan hotel karena mempengaruhi sistem reservasi kamar. Pembatalan dalam reservasi pemesanan hotel dapat mengakibatkan kerugian bagi pihak hotel terhadap keputusan manajemen permintaan industri hotel. Banyak faktor yang menyebabkan pembatalan pemesanan seperti jadwal perjalanan bisnis, hari libur, lingkungan yang buruk (pandemi) dan faktor lainnya. Memahami alasan pembatalan pemesanan pelanggan merupakan aspek penting bagi pihak hotel. Mengidentifikasi faktor-faktor yang menyebabkan pembatalan pemesanan dapat membantu hotel mengatasi masalah, meningkatkan kepuasan pelanggan, dan menerapkan strategi untuk meminimalkan pembatalan. Hal ini dapat dilakukan pihak hotel untuk menyesuaikan layanan dan penawarannya agar memenuhi ekpetasi keinginan pelanggan. 

Namun hal ini menjadi tantangan untuk memprediksi faktor pembatalan pemesanan. Untuk mengurangi pembatalan reservasi, akan sangat membantu bagi hotel memiliki sistem yang dapat memprediksi apakah suatu pemesanan akan dibatalkan sehingga mereka dapat menawarkan kamar kepada pelanggan lain atau membuat rencana lainnya. Dalam industri perhotelan terdapat standard format yang bernama Passenger Name Record (PNR) yang dikembangkan oleh industri pariwisata dan perjalanan yang digunakan sebagai pengembangan model prediksi untuk mengklasifikasikan kemungkinan pembatalan pemesanan hotel.

**Problem Statement:**

LisGarve City & Resort Hotel adalah sebuah penginapan yang berada di Portugal. Saat ini mengalami penurunan pendapatan karena banyak mengalami pembatalan pemesanan yang menyebabkan kerugian bagi pihak hotel, datasets ini menunjukan banyaknya cancellation sekitar *37%. Dampak tersebut memberika cukup banyak revenue loss pada pihak hotel akibat dari pesanan yang dibatalkan dapat mencapai **15%*.

Mereka ingin mengetahui tindakan yang harus diambil oleh pihak manajemen hotel untuk mengurangi peluang terjadinya pembatalan pemesanan dengan mengidentifikasi karakteristik yang dimiliki oleh hotel. Banyak faktor yang menyebabkan pembatalan hotel, namun sulit untuk pihak hotel untuk melakukan tracking alasan calon konsumen melakukan pembatalan pemesanan. Sehingga pihak hotel memerlukan kemampuan untuk memprediksi calon konsumen mana yang berpeluang membatalkan pemesanan hotel.

Sumber :
https://revenue-hub.com/three-most-common-trends-impacting-cancellation-rates/

Goals:

**Goals:**

Tim Data mencoba membantu perusahaan LisGarve City & Resort Hotel menekan biaya marketing atau memberikan kondisi (deposit atau double booking) kepada konsumen yang berpeluang membatalkan pemesanan hotel dengan cara memahami `karakteristik penyebab pembatalan pemesanan hotel` agar tim marketing mengetahui action yang dilakukan lebih terarah, adapun beberapa poin yang dapat dijabarkan untuk menemukan karakteristik tersebut adalah :

1. Bagaimana karakteristik jarak hari dan waktu tertentu mempengaruhi kebiasaan pembatalan pemesanan hotel? (jarak hari antara tanggal pemesanan hingga tanggal dijadwalkan dan bulan tertentu)
2. Bagaimana karakteristik fasilitas dan pelayanan hotel mempengaruhi pelanggan dalam membatalkan pesanan hotel? (jenis hotel, paket makan, permintaan khusus fasilitas/layanan, perbedaan type kamar yang dipesan dan tipe kamar yang tersedia)
3. Bagaimana karakteristik pelanggan yang melakukan pembatalan pemesanan hotel? (jumlah pengunjung, banyak pembatalan sebelumnya, tipe pelanggan, sebelumnya membatalkan/tidak, tipe deposit, asal negara)

Berdasarkan permasalahan yang telah dipaparkan, pihak hotel ingin megetahui karakteristik konsumen yang berpeluang membatalkan pemesanan hotel berdasarkan fitur-fitur yang tersedia, dan mengarahkan target marketing kepada pelanggan yang memiliki karakteristik tersebut agar tim makrketing dapat menekan biaya promosi sehingga memiliki KPI yang baik sehingga mendapat conversion rate yang tinggi untuk menhindari campaign yang tidak terarah. Tim data ingin membuat program yang lebih tepat sasaran kepada calon konsumen yang berpeluang melakukan pembatalan pemesanan dengan karakteristik diatas.

Stakeholder : Tim Marketing LisGarve City & Resort Hotel
Link Model: https://drive.google.com/file/d/1Kfm61S2fKIE0W1ebo7JGID_edkOO8L9a/view?usp=sharing

**Analytic Approach:**

Pendekatan analisis dilakukan beberapa tahapan proses seperti pengumpulan data yang komprehensif, melakukan data cleaning, dan melakukan pengolahan data untuk mendapatkan hasil analisis. Dengan data ini untuk mendapatkan hasil analisis yang akan digunakan untuk pengambilan keputusan, kami melakukan pengolahan data dengan menggunakan pemodelan machine learning untuk memprediksi calon konsumen berpeluang melakukan pembatalan pemesanan hotel atau tidak.

**Metric Evaluation:**

![alt text](https://www.researchgate.net/publication/328148379/figure/fig1/AS:679514740895744@1539020347601/Model-performance-metrics-Visual-representation-of-the-classification-model-metrics.png)


- *(TP) True Positive*: Pelanggan diprediksi (predict) cancel dan aktualnya (actual) benar-benar cancel.
- *(FP) False Positive*: Pelanggan diprediksi (predict) cancel, tetapi sebenarnya (actual) tidak cancel.
- *(FN) False Negative*: Pelanggan diprediksi (predict) TIDAK cancel, tetapi sebenarnya (actual) cancel.
- *(TN) True Negative*: Pelanggan diprediksi (predict) TIDAK cancel dan sebenarnya (actual) TIDAK cancel.

Untuk megetahui performa suatu model memprediksi targetnya maka kita membutuhkan metric evaluation dengan mengukur nilai errornya. Karena fokus utama kita ingin meningkatkan revenue dengan memaksimalkan model pada CLass Positif dengan mengurangi kerugian yang diakibatkan dari pemesanan hotel yang aktualnya cancel namun diprediksi tidak cancel (False Negative) atau diakibatkan dari pemesan hotel yang aktualnya tidak cancel namun di prediksi cancel (False Positif). Pada percobaan ini kita menggunakan identifikasi sebagai berikut :

Target :
- 0 : Not Canceled
- 1 : Canceled

Action pihak hotel terhadap hasil prediksi:
Cancel : Melakukan *double booking* pada transaksi yang *actual*-nya *cancel* atau memberlakukan deposit pada pemesan hotel, namun harus ditinjau kembali untuk deposit karena akan mengakibatkan kehilangan pelanggan jika deposit yang dibebankan kepada konsumen cukup tinggi.

Type I Error : False Positif (Pelanggan yang aktualnya tidak cancel tetapi diprediksi cancel)
<br>
Konsekuensi : promosi untuk pemesan hotel tidak tepat sasaran, sehingga revenue yang didapatkan tidak maksimal karena tanpa perlu mengeluarkan biaya marketing Hotel bisa mendapatkan revenue booking hotel secara penuh sehingga pihak hotel mendapatkan **penurunan revenue sekitar 11%** (4-5% digital marketing dan marketing convensional 6%) sesuai referensi dibawah. Biaya tersebut juga termasuk biaya dampak dari double booking yang menurut sumber dibawah dapat mengakibatkan negatif review, sehingga tim marketing membutuhkan biaya untuk menimilkan negatif review akibat double booking tersebut

Type II Error : False Negative (Pelanggan yang aktualnya cancel tetapi diprediksi tidak cancel) 
<br>
Konsekuensi : pihak hotel kehilangan potential pelanggan yang membatalkan pesanan dan tentu saja berdampak pada kehilangan revenue. Sehingga, pihak hotel kehilangan **revenue senilai harga booking hotel**.

Untuk memberikan gambaran konsekuensi secara kuantitatif, maka kita akan coba hitung dampak biaya berdasarkan asumsi berikut :
- Rata-rata harga hotel per malam di portugal : **91.85 Euro**
- Rata-rata biaya marketing hotel
- Gaji team marketing
- Dampak negatif review dari double booking 
- poin 2-4 : 11% x harga hotel per malam = 11% x 91.85 = **10 Euro** 

Berdasarkan konsekuensinya, maka sebisa mungkin yang akan kita lakukan adalah membuat model yang dapat memfokuskan kepada model evaluation yang tertarik kepada **Kelas Positif** yaitu **(Recall, Presisi, F1)** namun dilihat secara sederhana diatas recall memiliki dampak yang cukup besar karena biaya yang ditanggung pihak hotel akan lebih besar (kehilangan kesempatan seharga satu kamar/malam). Selain itu alasan lain menggunakan recall adalah nilai Type II Error yang memiliki solusi menggunakan deposit dapat membuat Hotel kehilangan pelanggan karena pada dataset mayoritas pelanggan hotel memesan tanpa deposit sehingga dikhawatirkan akan terjadi chargebacks seperti sumber dibawah.

Namun kami harus menelusuri lagi keuntungan bisnis yang maksimal kami akan mencoba beberapa metric dan menyimpulkan metric terbaik untuk Bisnis sebagai metric utama.

sumber :
- https://www.bu.edu/bhr/2015/08/25/digital-marketing-budgets-for-independent-hotels-continuously-shifting-to-remain-competitive-in-the-online-world/
- https://www.orourkehospitality.com/resources/topic/hospitality-digital-marketing/4-tips-for-planning-your-2022-hospitality-marketing-budget/
- https://www.selecthub.com/hotel-management/double-booking/
- https://www.hoteliga.com/en/blog/how-to-minimize-hotel-booking-cancellations-and-chargebacks (deposit)

---

Link PPT : https://www.canva.com/design/DAF89YIzkkI/Qd7P3cFTHwAztbv5bZf1qg/edit?utm_content=DAF89YIzkkI&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton

Link Tableau : https://public.tableau.com/views/HotelBookingDashboard_17078230063390/Dashboard?:language=en-US&:sid=&:display_count=n&:origin=viz_share_link
