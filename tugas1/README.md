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
        memasang tittle dengan menggunakan huruf romawi , superbowl terakhir adalah LIV(54).
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

- data di mysql seperti dibawah<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/sql_import-membaca.PNG "mysql data")

- Merapikan row yang ada di mysql dengan menggunakan syntax ini<br/>
``` DELETE FROM `table 1` WHERE `COL 1`='Date' ```<br/>

- hasil menjalankan syntax di atas<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/hasil_rapih_mysql.PNG "hasil mysql")<br/>

- melakukan configurasi disesuaikan dengan mysql yang ada di phpmyadmin, mulai dari database, port dari localhost dan username.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/proses_configure_mysql.PNG "configure mysql")<br/>

- db table selector untuk mengambil Koneksi DB sebagai input dan memungkinkan untuk memilih tabel atau tampilan dari dalam database yang terhubung.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/db_table_selector.PNG "db table selector")<br/>

- db reader untuk Mengeksekusi kueri input dalam database dan mengambil hasilnya ke dalam tabel data KNIME.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/db_reader.PNG "db reader")<br/>

- hasil akhir dari pembacaan database yang terhubung dari mysql<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/data_mysql.PNG "hasil mysql")<br/>

#### Proses membaca dari csv
- memasang csv reader untuk membaca file csv<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/csv_reader.PNG " csv baca")<br/>
- melakukan konfigurasi , menentukan path file dimana csv disimpan<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/csv_baca.PNG " csv reader")<br/>
- hasil dari csv reader<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/hasil_csv.PNG " csv hasil")<br/>

### Proses Modeling
- menggunakan joiner node, dengan mengsambungkan node dari database yang mengolah mysql dan csv<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/joiner.PNG " joiner")<br/>

- melakukan configure dengan memilih kolom yang urutan nya sama , bisa dibilang foreign key agar datanya berhasil di append<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/configure_joiner.PNG " configure joiner")<br/>

- dan hasilnya seperti ini<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/join_belumGantiNama.PNG " configure joiner")<br/>

- nama coloumn di sesuaikan agar mudah dimengerti<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/RENAME_COULOMNS.PNG " configure joiner")<br/>

- menggunakan coloumn filter untuk menentukan coloumn mana yang mau ditampilkan
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/coloumn_filter.PNG " hasil join")<br/>

- hasil akhir<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/hasil_join.PNG " hasil join")<br/>

# Evaluation

- dari kedua data yang ada di mysql dan csv telah berhasil di join

- hasil join
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/hasil_join.PNG " hasil join")<br/>

- data asli 
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/data_asli.PNG " asli")<br/>

- dari kedua data di atas, berhasil karena dari hasil join sama dengan data asli ketika sebelum dipisah

# Deployment
### simpan ke csv
- data yang pertama akan disimpan ke csv dengan menggunakan csv writer
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/csv_writer.PNG " asli csv")<br/>

- memilih penempatan dan konfigurasi lain nya
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/configure_csv.PNG " csv write")<br/>
 
- data berhasil tersimpan
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/data_csv_berhasil.PNG " csv write")<br/>

 ### simpan ke db
- data akan disimpan ke database menggunakan db writer
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/db_writer.PNG " asli csv")<br/>

- memilih konfigurasi lain nya, seperti nama dan db yang dituju
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/configure_db.PNG " asli csv")<br/>

- berhasil tersimpan
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/berhasil_db.PNG " asli csv")<br/>






