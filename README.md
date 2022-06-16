<h1 align="center"> Implementasi Algoritma K-Means Clustering dan Visualisasi Dashboard Untuk Analisis Upaya Warga dalam Menjaga Keamanan Berdasarkan Provinsi di Indonesia </h1>

<p align="justify"> Negara berkembang seperti Indonesia memiliki beberapa masalah serius, salah satunya ialah kriminalitas. Penelitian ini menggunakan salah satu teknik data mining, yaitu dengan metode K-Means Clustering agar dapat mengelompokkan 34 provinsi dan mendapatkan provinsi yang baik dan buruk dalam melakukan upaya menjaga keamanan di daerahnya. Setelah itu dilakukan visualisasi terhadap hasil clustering dalam bentuk dashboard. Dengan adanya pengelompokan dan pembuatan dashboard diharapkan adanya solusi baik dari pemerintah maupun masyarakat untuk bekerja sama agar dapat meningkatkan keamanan pada provinsi di Indonesia, khususnya untuk daerah yang tergolong belum baik. Data pada penelitian ini diambil dari publikasi Statistik Kriminal 2021 yang berisi data kriminalitas 34 provinsi di Indonesia, dengan variabel yang digunakan yaitu Membangun Poskamling, Membentuk Regu Kamling, Menambah Anggota Hansip, dan Pelaporan Tamu yang Menginap dalam Kurun Waktu 1x24 jam. Dari hasil analisis cluster didapatkan bahwa provinsi dengan kategori baik dalam mengupayakan keamanan berjumlah 23 provinsi, sedangkan provinsi dengan kategori buruk berjumlah 11. </p>
 
## Dataset yang digunakan
Data yang digunakan ialah data Jumlah Desa/Kelurahan Menurut Jenis Upaya Warganya untuk Menjaga Keamanan Menurut Provinsi Tahun 2018.
Variabel yang digunakan adalah sebagai berikut :
- Membangun Poskamling (X1)
- Membentuk Regu Kamling (X2)
- Menambah Anggota Hansip (X3)
- Pelaporan Tamu Menginap (1x24 jam) (X4)

Berikut adalah data yang digunakan :
<p align="center">
<img src = "https://github.com/putrikurnia21/visualisasidataUAS/blob/main/Data.PNG" width="300" height="450" />
</p>

## Eksplorasi Data
* Pemeriksaan Outlier
Dari hasil boxplot pada gambar di atas didapatkan bahwa terdapat pencilan pada data khususnya pada variabel menambah anggota hansip (X3) dan pelaporan tamu menginap 1x24jam (X4). Umumnya, jika terdapat pencilan maka peneliti membuang ataupun mempertahankan pencilan tersebut dengan pertimbangan berdasarkan objek penelitian. Pada penelitian ini, pencilan tidak perlu dibuang dikarenakan merupakan data asli 

* Statistik Deskriptif
1. X1 : Papua ialah provinsi dengan persentase upaya membangun poskamling terkecil, yaitu sebesar 7,94 persen, sedangkan  Jawa Barat ialah provinsi dengan persentase desa/kelurahan dengan upaya membangun poskamling terbesar yaitu 90,80 persen. 
2. X2 : Provinsi Papua merupakan provinsi dengan persentase membentuk regu kamling terkecil, yaitu sebesar 11,65 persen. Sedangkan, provinsi DI Yogyakarta ialah provinsi dengan persentase upaya membentuk regu kamling terbesar yaitu 79,22 persen. 
3. X3 : Variabel selanjutnya adalah persentase desa/kelurahan dengan upaya menambah anggota hansip dengan rata-rata 26,53 persen. Provinsi Papua Barat merupakan provinsi  terkecil, yaitu 3,07 persen, sedangkan DI Yogyakarta ialah provinsi terbesar yaitu sebesar 50,68 persen.
4. X4 : Variabel terakhir ialah  upaya pelaporan tamu menginap dalam kurun waktu 1x24 jam dengan rata-rata 63,98 persen. Provinsi Papua merupakan provinsi terkecil, yaitu 3,07 persen, sedangkan DKI Jakarta ialah provinsi terbesar yaitu sebesar 90,64 persen
## K-Means Clustering
<p align="justify">K-Means Clustering adalah salah cara untuk menganalisis kelompok dengan metode pengelompokan non hierarki (Supranto, 2004). Metode ini merupakan metode yang tepat untuk data yang cukup besar, selain itu proses pengelompokan pada metode non hirarki lebih cepat daripada metode hierarki. </p>

#### Menentukan banyaknya kelompok (Metode Silhouette) 
```{r}
fviz_nbclust(df_num, kmeans, method = "silhouette") 
```
<p align="center">
<img src = "https://github.com/putrikurnia21/visualisasidataUAS/blob/main/kelompok.PNG" width="500" height="300" />
</p>

Pada Gambar tampak bahwa banyak klaster yang optimal terbentuk saat k=2. Maka untuk melakukan analisis kelompok akan digunakan k=2.

#### Proses Clustering
```{r}
model=kmeans(df_num,centers=2,nstart=20)
model
model$centers
```
<p align="center">
<img src = "https://github.com/putrikurnia21/visualisasidataUAS/blob/main/centroid.PNG" />
 </p>
 
Dikarenakan centroid kelompok 2 lebih besar dibandingkan kelompok 1, maka kelompok 2 dikategorikan sebagai kelompok baik dan kelompok 1 dikategorikan sebagai kelompok buruk.

#### Provinsi di Tiap Kelompok 
```{r}
final=data.frame(df, model$cluster)
View(final)
```
<p align="center">
<img src = "https://github.com/putrikurnia21/visualisasidataUAS/blob/main/hasil.PNG" />
</p>

- Kelompok 1 (Buruk) terdiri dari 12 provinsi
- Kelompok 2 (Baik) terdiri dari 22 provinsi

## Perancangan Dashboard
<p align="justify">
Perancangan dashboard untuk memvisualisasikan hasil analisis cluster dibantu oleh Figma website yang dapat digunakan secara gratis. Selain itu, dashboard dirancang menggunakan tema Black and White agar pembaca yang memiliki buta warna baik parsial maupun total dapat memahami dashboard yang telah dibuat apalagi pada proses visualisasi banyak menggunakan peta tematik dalam bentuk choropleth yang membutuhkan gradasi warna. 
Pada sebelah kiri dashboard, terdapat side bar yang dapat digunakan untuk memilih tampilan yang diinginkan.
 </p>
 
> Perancangan Dashboard Main (Hasil clustering)
<p align="center">
<img src = "https://github.com/putrikurnia21/visualisasidataUAS/blob/main/Main.png" width="500" height="300"/>
</p>

> Perancangan Dashboard X1, X2, X3, dan X4
<p align="center">
<img src = "https://github.com/putrikurnia21/visualisasidataUAS/blob/main/Desain Var.png" width="500" height="300" />
</p>

## Visualisasi (Data dan Informasi) dan Pembuatan Dashboard
Dashboard dapat diakses secara daring melalui link (https://public.tableau.com/views/Dashboardvisdat/Main?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link)

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

<p align="center">
<img src = "https://github.com/putrikurnia21/visualisasidataUAS/blob/main/Vmain.png" width="600" height="300" />
</p>

> Dashboard X1, X2, X3, dan X4

Menampilkan visualisasi berupa peta tematik, treemap, dan tabel untuk masing-masing variabel.

<p align="center">
<img src = "https://github.com/putrikurnia21/visualisasidataUAS/blob/main/V1.png" width="600" height="300" />

<img src = "https://github.com/putrikurnia21/visualisasidataUAS/blob/main/V2.png" width="600" height="300" />

<img src = "https://github.com/putrikurnia21/visualisasidataUAS/blob/main/V3.png" width="600" height="300" />

<img src = "https://github.com/putrikurnia21/visualisasidataUAS/blob/main/V4.png" width="600" height="300" />
</p>

#### Embed Dashboard Tableau
Dashboard yang telah dibuat di tableau dapat dipublikasikan dan diakses secara daring. Apabila ingin menyimpan dalam format html maka dilakukan embed pada dashboard. Cata mengembed dashboard tableau adalah dengan menyalin embed code pada tableau lalu diletakkan pada bagian div.

```
<!doctype html>

<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Dashboard Visualisasi Data dan Informasi </title>
</head>
<body>

 #Embed Code dimulai dari sini
  <div class='tableauPlaceholder' id='viz1655375225288' style='position: relative'><noscript><a href='#'>
    <img alt='Main ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Da&#47;Dashboardvisdat&#47;Main&#47;1_rss.png' style='border: none' /></a></noscript>
    <object class='tableauViz'  style='display:none;'>
      <param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> 
      <param name='embed_code_version' value='3' /> <param name='site_root' value='' />
      <param name='name' value='Dashboardvisdat&#47;Main' />
      <param name='tabs' value='no' /><param name='toolbar' value='yes' />
      <param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Da&#47;Dashboardvisdat&#47;Main&#47;1.png' /> 
      <param name='animate_transition' value='yes' />
      <param name='display_static_image' value='yes' />
      <param name='display_spinner' value='yes' />
      <param name='display_overlay' value='yes' />
      <param name='display_count' value='yes' />
      <param name='language' value='en-US' /></object>
    </div>                
    <script type='text/javascript'>                    
    var divElement = document.getElementById('viz1655375225288');                    
    var vizElement = divElement.getElementsByTagName('object')[0];                    
    vizElement.style.width='1920px';vizElement.style.height='1107px';                    
    var scriptElement = document.createElement('script');                    
    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';                    
    vizElement.parentNode.insertBefore(scriptElement, vizElement);               
     </script>
  ## Akhir Embed Code
  
</body>
</html>
```

