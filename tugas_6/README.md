## Bigdata 2020

# Dokumentasi MLlib model to PMML KNIME

* [Business Understanding](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#business-understanding)<br/>
* [Data Understanding](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#data-understanding)<br/>
* [Data Preparation](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#data-preparation)<br/>
* [Modeling](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#modeling)<br/>
* [Evaluation](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#evaluation)<br/>
* [Deployment](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/README.md#deployment)<br/>

# Business Understanding
Kemungkinan-kemungkinan yg dapat dilakukan yaitu Dari data tersebut, dapat dilakukan proses klasifikasi<br/> 
terhadap dataset bunga bunga iris yang terssedia. dari sini juga dapat dijadikan pembelajaran untuk memagami<br/>
machine learning model.

# Data Understanding

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

# Data Preparation

- menyiapkan node file reader untuk membaca file dari dataset iris 
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/1.PNG "file reader")<br>

- mengatur node file reader untuk file dengan mengarahkan ke dataset iris 
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/1_conf.PNG "file reader")<br>

- menyiapkan node local big data environment
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/2.PNG "file reader")<br>

- mengatur pada node local big data environment
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/2_conf.PNG "file reader")<br>

- menyiapkan node table to spark 
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/3.PNG "file reader")<br>

- didapati hasil dari node tersebut seperti dibawah ini
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/3_conf.PNG "file reader")<br>

- gambar dari data preparation
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/4.PNG "file reader")<br>

# Modeling

- proses modeling dimulai dengan menggunakan node spark k-means untuk melakukan train pada table sebelumnya<br>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_3/picture/5.PNG "add field")<br>

- melakukan pengaturan di node spark k-means dengan memaskkan semua parameter yang ada<br>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_3/picture/5_conf.PNG "add field")<br>

- memasang node spark MLIB to PMML agar mengubah model dari spark menjadi PMML<br>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_3/picture/6.PNG "add field")<br>

- memasang node PMML compiler agar bisa dijalankan oleh node compiled model predictor<br>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_3/picture/7.PNG "add field")<br>

- node ini mengubah model pmml ke java bytecode <br>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_3/picture/7_conf.PNG "add field")<br>

- gambar dari Modeling
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/8.PNG "file reader")<br>

# Evaluation

- pada proses pertama evaluation ini mengambil data lagi dari file reader sebagai test data
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/9.PNG "file reader")<br>

- pada proses pertama evaluation ini mengambil data lagi dari file reader sebagai test data
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/9_conf.PNG "file reader")<br>
 
 - memasang node compiled model predictor untuk mendapati hasil dari entropynya
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/10.PNG "file reader")<br>

- dari node model predictor didapati hasil dari entropynya
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/10_conf.PNG "file reader")<br>

 - memasang node entropy scorer. untuk melakukan perhitungan
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/11.PNG "file reader")<br>

- berikut adalah hasil perhitungan
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/11_conf.PNG "file reader")<br>

- berikut adalah gambar dari evaluation
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/12.PNG "file reader")<br>
 
# Deployment

- dari data sebelumnya yang telah diprediksi, kita memasang node dengan format json, dan memasang node json to table<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/13.PNG "file reader")<br>

- container input json, merupakan konfigurasi dari node tersebut<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/13_conf.PNG "file reader")<br>

- kemudian diubah di node json to table agar bisa dibaca<br/>

- setelah memasang node table to json yang terdapat pada gambar, dipasang node container output json, untuk proses deployment<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/14.PNG "file reader")<br>

- setelah memasang node output json, akan terdapati hasil seperti ini pada proses deployment<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/15.PNG "file reader")<br>

- gambar lengkap dari proses deployment<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_6/picture/15.PNG "file reader")<br>



