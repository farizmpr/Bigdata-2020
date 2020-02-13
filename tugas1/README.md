## Bigdata 2020

# Dokumentasi Praktek ETL menggunakan KNIME

* [Business Understanding](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/README.md#business-understanding)<br/>
* [Data Understanding](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/README.md#data-understanding)<br/>
* [Data Preparation](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/README.md#data-preparation)<br/>
* [Modeling](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/README.md#modeling)<br/>
  - [Proses membaca data dari dua sumber yang berbeda](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/README.md#proses-membaca-data-dari-dua-sumber-yang-berbeda)<br/>
  - [Proses Modeling](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/README.md#proses-modeling)<br/>
* [Evaluation](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/README.md#evaluation)<br/>
* [Deployment](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/README.md#deployment)<br/>

# Business Understanding

# Data Understanding

- Super bowl adalah acara tahunan American Football yang menentukan jawara dari National<br/>
  Football League (NFL). Pertandingan puncak pada satu musim NFL dan menghasilkan kesimpulan dari<br/>
  NFL playoffs. Pertandingan ini dihelat di salah satu kota amerika, ditentukan empat tahun sebelum<br/>
  penyelenggaraan. mulai dari januari 1971, pemenang dari AFC akan menghadapi pemenang dari NFC dan kedua<br/>
  tim akan diadu pada laga puncak NFL Playoffs.  
  
- dataset ini berisi para finalis dari superbowls, mulai dari tahun 1967 sampai 2020.

- dataset ini 54 row dan mempunyai 10 coloumns
  - Date : Tanggal dilaksanakan superbowl final
  - SB : Superbowl Tittle, superbowl final pertama kali dilaksanakan tahun 1967, setiap tahunnya superbowl<br/>
        memasang tittle dengan menggunakan huruf romawi , superbowl terakhir adalah LIV(54).\
  - Winner : nama tim yang keluar sebagai pemenang
  - Winner pts : points yang diraih pada tim pemenang pada laga final
  - Loser : nama tim yang mengalami kekalahan
  - Loser pts : points yang diraih oleh tim yang mengalami kekalahan
  - MVP : nama most valuable player pada superbowl
  - Stadium : Lokasi stadium dilaksanakannya partai puncak
  - City : Lokasi kota dilaksanakan partai puncak
  - State : negara bagian amerika tempat dihelatnya pertandingan puncak

- Source dataset : https://www.kaggle.com/timoboz/superbowl-history-1967-2020

# Data Preparation
# Modeling
### Proses membaca data dari dua sumber yang berbeda
#### Proses membaca dari MYSQL
- yang pertama membaca data dari mysql, dengan menggunakan mysql connector nodes dari knime<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/mysql_connector-membaca.PNG "mysql connector")
<br/>
- data di mysql seperti dibawah<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/sql_import-membaca.PNG "mysql data")
<br/>
- Merapikan row yang ada di mysql dengan menggunakan syntax ini<br/>
``` DELETE FROM `table 1` WHERE `COL 1`='Date' ```<br/>
<br/>
- hasil menjalankan syntax di atas<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/hasil_rapih_mysql.PNG "hasil mysql")<br/>
<br/>
- melakukan configurasi disesuaikan dengan mysql yang ada di phpmyadmin, mulai dari database, port dari localhost dan username.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/proses_configure_mysql.PNG "configure mysql")<br/>
<br/>
- db table selector untuk mengambil Koneksi DB sebagai input dan memungkinkan untuk memilih tabel atau tampilan dari dalam database yang terhubung.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/db_table_selector.PNG "db table selector")<br/>
<br/>
- db reader untuk Mengeksekusi kueri input dalam database dan mengambil hasilnya ke dalam tabel data KNIME.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/db_reader.PNG "db reader")<br/>
<br/>
- hasil akhir dari pembacaan database yang terhubung dari mysql<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/data_mysql.PNG "hasil mysql")<br/>
<br/>
#### Proses membaca dari csv

### Proses Modeling
# Evaluation
# Deployment
 






