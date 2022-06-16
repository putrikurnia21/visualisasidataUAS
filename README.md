# Implementasi Algoritma K-Means Clustering dan Visualisasi Dashboard Untuk Analisis Upaya Warga dalam Menjaga Keamanan Berdasarkan Provinsi di Indonesia 

<p align="justify"> Negara berkembang seperti Indonesia memiliki beberapa masalah serius, salah satunya ialah kriminalitas. Penelitian ini menggunakan salah satu teknik data mining, yaitu dengan metode K-Means Clustering agar dapat mengelompokkan 34 provinsi dan mendapatkan provinsi yang baik dan buruk dalam melakukan upaya menjaga keamanan di daerahnya. Setelah itu dilakukan visualisasi terhadap hasil clustering dalam bentuk dashboard. Dengan adanya pengelompokan dan pembuatan dashboard diharapkan adanya solusi baik dari pemerintah maupun masyarakat untuk bekerja sama agar dapat meningkatkan keamanan pada provinsi di Indonesia, khususnya untuk daerah yang tergolong belum baik. Data pada penelitian ini diambil dari publikasi Statistik Kriminal 2021 yang berisi data kriminalitas 34 provinsi di Indonesia, dengan variabel yang digunakan yaitu Membangun Poskamling, Membentuk Regu Kamling, Menambah Anggota Hansip, dan Pelaporan Tamu yang Menginap dalam Kurun Waktu 1x24 jam. Dari hasil analisis cluster didapatkan bahwa provinsi dengan kategori baik dalam mengupayakan keamanan berjumlah 23 provinsi, sedangkan provinsi dengan kategori buruk berjumlah 11. </p>
 
## Dataset yang digunakan
Data yang digunakan ialah data Jumlah Desa/Kelurahan Menurut Jenis Upaya Warganya untuk Menjaga Keamanan Menurut Provinsi Tahun 2018.
Variabel yang digunakan adalah sebagai berikut :
- Membangun Poskamling
- Membentuk Regu Kamling
- Menambah Anggota Hansip
- Pelaporan Tamu Menginap (1x24 jam)

Berikut adalah data yang digunakan :
![](Data.png)

## K-Means Clustering
<p align="justify">K-Means Clustering adalah salah cara untuk menganalisis kelompok dengan metode pengelompokan non hierarki (Supranto, 2004). Metode ini merupakan metode yang tepat untuk data yang cukup besar, selain itu proses pengelompokan pada metode non hirarki lebih cepat daripada metode hierarki. </p>

#### Menentukan banyaknya kelompok (Metode Silhouette)
```{r}
fviz_nbclust(df_num, kmeans, method = "silhouette") 
```

#### Proses Clustering
```{r}
model=kmeans(df_num,centers=2,nstart=20)
model
model$centers
```
### Provinsi di Tiap Kelompok
```{r}
final=data.frame(df, model$cluster)
View(final)
```

## Perancangan Dashboard

## Visualisasi (Data dan Informasi) dan Pembuatan Dashboard
Jenis visualisasi data dan informasi yang digunakan adalah :
- Peta Tematik (Choropleth)
- Tabel
- Barchart
- Boxplot
- Pie Chart
- Tree Map Chart

#### Tambahan pada Dashboard
Selain menampilkan visualisasi data dan informasi, terdapat beberapa tambahan pada dashboard untuk memudahkan pengguna.
- Sidebar   : Pada sidebar terdapat 5 navigasi yang dapat mengarahkan langsung ke halaman variabel X1, X2, X3, ataupun X4. 
- Tooltip   : Dikarenakan nama variabel yang panjang, pada button navigasi hanya ditulis X1, X2, X3, X4, dan main. Akan tetapi, apabila kursor diarahkan ke atas button navigasi maka akan keluar tooltip/keterangan yaitu nama variabel
- Download  : Dapat mendownload tampilan dashboard berupa gambar pdf, ataupun power point
- Action    : Action pada dashboard adalah apabila mengklik visualisasi salah satu provinsi pada dashboard hamalan X1, X2, X3, dan X4 maka yang akan ditampilkan hanya provinsi tersebut
- Search    : Mencari informasi berdasarkan nama provinsi

<p align="justify">Pembuatan dashboard segera dieksekusi setelah dashboard dirancang sedemikian rupa. Pada pembuatan dashboard kali ini, digunakan aplikasi Tableau Public yang mana selain dapat memvisualisasikan dengan sangat baik, dashboard juga dapat diakses secara daring oleh pembaca. Pada dashboard terdapat side bar yang dapat mengakses ke lima halaman, yaitu halaman pertama sebagai default atau dashboard main yang memvisualisasikan hasil analisis cluster. Selain itu, keempat halaman lainnya akan mewakili visualisasi untuk tiap variabel yang digunakan. Pada dashboard tersedia pilihan untuk mengunduh dashboard baik dalam bentuk gambar ataupun pdf. Search bar juga menjadi salah satu fitur pada dashboard agar memudahkan pembaca untuk mencari informasi sesuai dengan provinsi ataupun kelompok daerah (cluster).</p>

> Dashboard utama

Menampilkan visualisasi berupa peta tematik hasil clustering, boxplot untuk melihat outlier pada data yang digunakan, grouped barchart untuk membandingkan data dari tahun-tahun sebelumnya, pie chart untuk melihat perbandingan provinsi yang dikelompok baik dan buruk, serta tabel untuk menampilkan informasi centroid kelompok.
![](Vmain.png)

> Dashboard X1, X2, X3, dan X4

Menampilkan visualisasi berupa peta tematik, treemap, dan tabel untuk masing-masing variabel.
![](V1.png)
![](V2.png)
![](V3.png)
![](V4.png)


