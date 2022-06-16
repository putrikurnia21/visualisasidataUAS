# Implementasi Algoritma K-Means Clustering dan Visualisasi Dashboard Untuk Analisis Upaya Warga dalam Menjaga Keamanan Berdasarkan Provinsi di Indonesia 

## Abstrak
<p align="justify"> Negara berkembang seperti Indonesia memiliki beberapa masalah serius, salah satunya ialah kriminalitas. Penelitian ini menggunakan salah satu teknik data mining, yaitu dengan metode K-Means Clustering agar dapat mengelompokkan 34 provinsi dan mendapatkan provinsi yang baik dan buruk dalam melakukan upaya menjaga keamanan di daerahnya. Setelah itu dilakukan visualisasi terhadap hasil clustering dalam bentuk dashboard. Dengan adanya pengelompokan dan pembuatan dashboard diharapkan adanya solusi baik dari pemerintah maupun masyarakat untuk bekerja sama agar dapat meningkatkan keamanan pada provinsi di Indonesia, khususnya untuk daerah yang tergolong belum baik. Data pada penelitian ini diambil dari publikasi Statistik Kriminal 2021 yang berisi data kriminalitas 34 provinsi di Indonesia, dengan variabel yang digunakan yaitu Membangun Poskamling, Membentuk Regu Kamling, Menambah Anggota Hansip, dan Pelaporan Tamu yang Menginap dalam Kurun Waktu 1x24 jam. Dari hasil analisis cluster didapatkan bahwa provinsi dengan kategori baik dalam mengupayakan keamanan berjumlah 23 provinsi, sedangkan provinsi dengan kategori buruk berjumlah 11. </p>
 
## Dataset yang digunakan
Data yang digunakan ialah data Jumlah Desa/Kelurahan Menurut Jenis Upaya Warganya untuk Menjaga Keamanan Menurut Provinsi Tahun 2018.
Variabel yang digunakan adalah sebagai berikut :
- Membangun Poskamling
- Membentuk Regu Kamling
- Menambah Anggota Hansip
- Pelaporan Tamu Menginap (1x24 jam)
Berikut adalah data yang digunakan :


         
## K-Means Clustering
<p align="justify">K-Means Clustering adalah salah cara untuk menganalisis kelompok dengan metode pengelompokan non hierarki (Supranto, 2004). Metode ini merupakan metode yang tepat untuk data yang cukup besar, selain itu proses pengelompokan pada metode non hirarki lebih cepat daripada metode hierarki. </p>

### Menentukan banyaknya kelompok (Metode Silhouette)
```{r}
fviz_nbclust(df_num, kmeans, method = "silhouette") 
```

### Proses Clustering
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

## Visualisasi Data dan Pembuatan Dashboard


