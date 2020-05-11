## Bigdata 2020

# Dokumentasi Tugas 6

* [MLIB to PMML](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#dokumentasi-mllib-model-to-pmml-knime)<br/>
* [Spark compiled predictor](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#dokumentasi-spark-compiled-predictor)<br/>

# Dokumentasi MLlib model to PMML KNIME

* [Business Understanding](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#business-understanding-mlib)<br/>
* [Data Understanding](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#data-understanding-mlib)<br/>
* [Data Preparation](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#data-preparation-mlib)<br/>
* [Modeling](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#modeling-mlib)<br/>
* [Evaluation](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#evaluation-mlib)<br/>
* [Deployment](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#deployment-mlib)<br/>

# Business Understanding (MLib) 

Kemungkinan-kemungkinan yg dapat dilakukan yaitu Dari data tersebut, dapat dilakukan proses klasifikasi<br/> 
terhadap dataset bunga bunga iris yang terssedia. dari sini juga dapat dijadikan pembelajaran untuk memagami<br/>
machine learning model.

# Data Understanding (MLib)

- Dataset iris ini terdiri dari 150 row dan 6 coloumns, dataset ini mengandung 3 spesies iris dengan memiliki 50 <br/>
  sampel masing-masing, serta menyampaikan beberapa informasi atau properti tentang masing-masing bunga.
  
- coloumn unique di representasi oleh id

- dataset berisi csv sebagai berikut :
  - id
  - SepalLength(Cm)
  - SepalWidth(Cm)
  - PetalLength(Cm)
  - PetalWidth(Cm)
  - Species (Iris setosa, iris versicolour, iris virginica)
  
- Source dataset : https://www.kaggle.com/uciml/iris

# Data Preparation (MLib)

- menyiapkan node file reader untuk membaca file dari dataset iris <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/1.PNG "file reader")<br/>

- mengatur node file reader untuk file dengan mengarahkan ke dataset iris <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/1_conf.PNG "file reader")<br/>

- menyiapkan node local big data environment<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/2.PNG "file reader")<br/>

- mengatur pada node local big data environment<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/2_conf.PNG "file reader")<br/>

- menyiapkan node table to spark <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/3.PNG "file reader")<br/>

- didapati hasil dari node tersebut seperti dibawah ini<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/3_conf.PNG "file reader")<br/>

- gambar dari data preparation<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/4.PNG "file reader")<br/>

# Modeling (MLib)

- proses modeling dimulai dengan menggunakan node spark k-means untuk melakukan train pada table sebelumnya<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/5.PNG "add field")<br/>

- melakukan pengaturan di node spark k-means dengan memaskkan semua parameter yang ada<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/5_conf.PNG "add field")<br/>

- memasang node spark MLIB to PMML agar mengubah model dari spark menjadi PMML<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/6.PNG "add field")<br/>

- memasang node PMML compiler agar bisa dijalankan oleh node compiled model predictor<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/7.PNG "add field")<br/>

- node ini mengubah model pmml ke java bytecode <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/7_conf.PNG "add field")<br/>

- gambar dari Modeling<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/8.PNG "file reader")<br/>

# Evaluation (MLib)

- pada proses pertama evaluation ini mengambil data lagi dari file reader sebagai test data<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/9.PNG "file reader")<br/>

- pada proses pertama evaluation ini mengambil data lagi dari file reader sebagai test data<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/9_conf.PNG "file reader")<br/>
 
 - memasang node compiled model predictor untuk mendapati hasil dari entropynya<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/10.PNG "file reader")<br/>

- dari node model predictor didapati hasil dari entropynya<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/10_conf.PNG "file reader")<br>

 - memasang node entropy scorer. untuk melakukan perhitungan<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/11.PNG "file reader")<br/>

- berikut adalah hasil perhitungan
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/11_conf.PNG "file reader")<br/>

- berikut adalah gambar dari evaluation<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/12.PNG "file reader")<br/>
 
# Deployment (MLib)

- dari data sebelumnya yang telah diprediksi, kita memasang node dengan format json, dan memasang node json to table<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/13.PNG "file reader")<br/>

- container input json, merupakan konfigurasi dari node tersebut<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/13_conf.PNG "file reader")<br/>

- kemudian diubah di node json to table agar bisa dibaca<br/>

- setelah memasang node table to json yang terdapat pada gambar, dipasang node container output json, untuk proses deployment<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/14.PNG "file reader")<br/>

- setelah memasang node output json, akan terdapati hasil seperti ini pada proses deployment<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/15.PNG "file reader")<br/>

- gambar lengkap dari proses deployment<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/15.PNG "file reader")<br/>

- workflow secara keseluruhan<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/16_a.PNG "file reader")<br>

# Dokumentasi Spark compiled predictor

* [Business Understanding](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#business-understanding-spark)<br/>
* [Data Understanding](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#data-understanding-spark)<br/>
* [Data Preparation](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#data-preparation-spark)<br/>
* [Modeling](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#modeling-spark)<br/>
* [Evaluation](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#evaluation-spark)<br/>
* [Deployment](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#deployment-spark)<br/>

# Business Understanding (Spark) 

Kemungkinan-kemungkinan yg dapat dilakukan yaitu Dari data tersebut, dapat dilakukan proses klasifikasi menggunakan berbagai<br/> 
algoritma terhadap dataset bunga bunga iris yang terssedia. dari sini juga dapat dijadikan pembelajaran untuk memagami<br/>
machine learning model.

# Data Understanding (Spark)

- Dataset iris ini terdiri dari 150 row dan 6 coloumns, dataset ini mengandung 3 spesies iris dengan memiliki 50 <br/>
  sampel masing-masing, serta menyampaikan beberapa informasi atau properti tentang masing-masing bunga.
  
- coloumn unique di representasi oleh id

- dataset berisi csv sebagai berikut :
  - id
  - SepalLength(Cm)
  - SepalWidth(Cm)
  - PetalLength(Cm)
  - PetalWidth(Cm)
  - Species (Iris setosa, iris versicolour, iris virginica)
  
- Source dataset : https://www.kaggle.com/uciml/iris

# Data Preparation (Spark)

- memasang node file reader untuk membaca dataset<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/1_a.PNG "file reader")<br/>

- melakukan pengaturan terhadap node file reader<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/1_a_conf.PNG "file reader")<br/>

- memasang node decision tree learner<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/2_a.PNG "file reader")<br/>

- melakukan pengaturan terhadap node decision tree learner<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/2_a_conf.PNG "file reader")<br/>

- memasang node mlp learner<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/3_a.PNG "file reader")<br/>

- melakukan pengaturan terhadapt node mlp learner<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/3_a_conf.PNG "file reader")<br/>

- workflow dari data preparation<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/4_a.PNG "file reader")<br/>

# Modeling (Spark)

- berikut adalah workflow modeling ,melakukan pemasangan node concatenate untuk menggabungkan dua learner yang berbeda<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/5_a.PNG "file reader")<br/>

- melakukan pemasangana table to pmml ensemble untuk menggabungkan tabel dokumen pmml menjadi satu dengan model mining<br/>
  untuk dilakukan compiler<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/6_a.PNG "file reader")<br/>

- dan yang terakhir node pmml compiler untuk menganti model pmml ke java bytecode agar bisa dijalankan<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/7_a.PNG "file reader")<br/>

# Evaluation (Spark)

- merupakan workflow dari proses evaluation<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/8_a.PNG "file reader")<br/>

- menambahkan data untuk test, dengan konfigurasi seperti ini<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/9_a.PNG "file reader")<br/>

- memasang node table to spark agar bisa di eksekusi<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/10_a.PNG "file reader")<br/>

- dan didapati hasil di node spark compiled model predictor seperti ini<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/11_a.PNG "file reader")<br/>
 
# Deployment (Spark)

- merupakan workflow dari proses deployment<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/12_a.PNG "file reader")<br>

- di tahap ini kita merubah data ke dalam table, dan didapati hasil dalam node scorer seperti ini<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/13_a.PNG "file reader")<br>

- jika ingin dideploy ke bentuk csv akan seperti ini <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/14_a.PNG "file reader")<br>

- workflow secara keseluruhan<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/15_a.PNG "file reader")<br>
