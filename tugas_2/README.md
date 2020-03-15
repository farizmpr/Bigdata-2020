## Bigdata 2020

# KNIME Big Data

* [Exercise DB](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_2/README.md#Exercise_DB)<br/>
  - [exercise DB Connect](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_2/README.md#01_db_connect)<br/>
  - [exercise DB processing exercise](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_2/README.md#02_DB_InDB_Processing_Exercise)<br/>
  - [exercise DB modelling exercise](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_2/README.md#03_DB_Modelling)<br/>
  - [exercise DB Writing To DB](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_2/README.md#04_DB_WritingToDB_Exercise)<br/>
* [Hadoop](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_2/README.md#Exercise_Hadoop)<br/>
  - [exercise Setup Hive](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_2/README.md#00_Setup_Hive_Table)<br/>
  - [exercise Hive Modelling](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_2/README.md#01_Hive_Modeling_Exercise)<br/>
  - [exercise Hive Writing to DB](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_2/README.md#02_Hive_WritingtoDB_Exercise)<br/>

# Exercise DB
### Proses Rename Data
- perubahan nama table dilakukan melalui DBeaver<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_2/picture/rename.PNG "rename table")
- Kemudian hasil akan seperti ini, pastikan path file yang tersambung antara knime dan DBeaver sama<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_2/picture/hasil_rename.PNG "result rename table")

#### Proses membaca dari MYSQL
- yang pertama membaca data dari mysql, dengan menggunakan mysql connector nodes dari knime<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/mysql_connector-membaca.PNG "mysql connector")

- data di mysql seperti dibawah<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/sql_import-membaca.PNG "mysql data")

- Merapikan row yang ada di mysql dengan menggunakan syntax ini<br/>
``` DELETE FROM `table 1` WHERE `COL 1`='Date' ```<br/>

- hasil menjalankan syntax di atas<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/hasil_rapih_mysql.PNG "hasil mysql")<br/>

- melakukan configurasi disesuaikan dengan mysql yang ada di phpmyadmin, mulai dari database, port dari localhost dan username.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/proses_configure_mysql.PNG "configure mysql")<br/>

- db table selector untuk mengambil Koneksi DB sebagai input dan memungkinkan untuk memilih tabel atau tampilan dari dalam database yang terhubung.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/db_table_selector.PNG "db table selector")<br/>

- db reader untuk Mengeksekusi kueri input dalam database dan mengambil hasilnya ke dalam tabel data KNIME.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/db_reader.PNG "db reader")<br/>

- hasil akhir dari pembacaan database yang terhubung dari mysql<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/data_mysql.PNG "hasil mysql")<br/>

#### Proses membaca dari csv
- memasang csv reader untuk membaca file csv<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/csv_reader.PNG " csv baca")<br/>
- melakukan konfigurasi , menentukan path file dimana csv disimpan<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/csv_baca.PNG " csv reader")<br/>
- hasil dari csv reader<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/hasil_csv.PNG " csv hasil")<br/>

### Proses Modeling
- menggunakan joiner node, dengan mengsambungkan node dari database yang mengolah mysql dan csv<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/joiner.PNG " joiner")<br/>

- melakukan configure dengan memilih kolom yang urutan nya sama , bisa dibilang foreign key agar datanya berhasil di append<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/configure_joiner.PNG " configure joiner")<br/>

- dan hasilnya seperti ini<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/join_belumGantiNama.PNG " configure joiner")<br/>

- nama coloumn di sesuaikan agar mudah dimengerti<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/RENAME_COULOMNS.PNG " configure joiner")<br/>

- menggunakan coloumn filter untuk menentukan coloumn mana yang mau ditampilkan<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/coloumn_filter.PNG " hasil join")<br/>

- hasil akhir<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/hasil_join.PNG " hasil join")<br/>

# Evaluation

- dari kedua data yang ada di mysql dan csv telah berhasil di join

- hasil join
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/hasil_join.PNG " hasil join")<br/>

- data asli 
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/data_asli.PNG " asli")<br/>

- dari kedua data di atas, berhasil karena dari hasil join sama dengan data asli ketika sebelum dipisah

# Deployment
### simpan ke csv
- data yang pertama akan disimpan ke csv dengan menggunakan csv writer<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/csv_writer.PNG " asli csv")<br/>

- memilih penempatan dan konfigurasi lain nya
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/configure_csv.PNG " csv write")<br/>
 
- data berhasil tersimpan
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/data_csv_berhasil.PNG " csv write")<br/>

 ### simpan ke db
- data akan disimpan ke database menggunakan db writer<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/db_writer.PNG " asli csv")<br/>

- memilih konfigurasi lain nya, seperti nama dan db yang dituju
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/configure_db.PNG " asli csv")<br/>

- berhasil tersimpan
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/berhasil_db.PNG " asli csv")<br/>

 ### gambar knime secara lengkap

![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas1/picture/knime.PNG " asli csv")<br/>



