## Bigdata 2020

# Dokumentasi Tugas 7

* [Business Understanding](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/README.md#business-understanding-mlib)<br/>
* [Data Understanding](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/README.md#data-understanding-mlib)<br/>
* [Data Preparation](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/README.md#data-preparation-mlib)<br/>
* [Modeling](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/README.md#modeling-mlib)<br/>
* [Evaluation](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/README.md#evaluation-mlib)<br/>
* [Deployment](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/README.md#deployment-mlib)<br/>

# Business Understanding (MLib) 

Kemungkinan-kemungkinan yang dapat dilakukan dari Data tersebut adalah untuk menganalisa proses yang terdapat<br/>
pda dataset, dan menganalisa kebutuhan energi yang ada di irlandia

# Data Understanding (MLib)

- Dataset iris ini terdiri dari 3 coloumns dan 5000++ rows yang berisi data penggunaan energi di irlandia

- dataset berisi sebagai berikut :
  - meterID
  - enc_datetime
  - reading  

- kolom meterID merupakan kolom unique yang merupakan id dari pengguna

- kolom enc_datetime merupakan kolom yang berisi waktu yang telah di konversi

- kolom reading merupakan kolom energi data meter

# Data Preparation (MLib)

- workflow<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/1.PNG "file reader")<br/>

- menyiapkan node file reader untuk membaca file dari dataset data meters <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/1.PNG "file reader")<br/>

- melakukan konfigurasi yang mengarahkan pada dataset tersebut <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/2.PNG "file reader")<br/>

- mengatur konfiguras pada local environment big data <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/4.PNG "file reader")<br/>

- memasang node table DB Table Creator yang dilihat dari node tersebut <br/>
Node ini disambung dari connection dari environment sebelumnya
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/5.PNG "file reader")<br/>

- memasang konfigurasi dari node table DB Table Creator <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/6.PNG "file reader")<br/>

- memasang node DB Loader untuk membaca table dan data yang sudah ada sebelumnya <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/7.PNG "file reader")<br/>

- memasang konfigurasi dari node DB Loader yang sudah disesuakan nama tablenya <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/8.PNG "file reader")<br/>

- Didapati hasi seperti dibawah ini<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/9.PNG "file reader")<br/>

- Memasang node hive to spark untuk mengubah table dari hive menjadi spark <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/10.PNG "file reader")<br/>

- Menjalankan konfigurasi yang ada dan mendapati hasil seperti dibawah ini setelah di convert <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/11.PNG "file reader")<br/>

- karna melakukan pemrosesan pada data waktu, data waktu yang ada ini merupadakan data integer, yang mana harus <br/>
menjadi bentuk date dan waktu. perubahan ini dilakukan menggunakan node spark sql
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/12.PNG "file reader")<br/>

``` SELECT 

meterid,
enc_datetime,
reading as kw30,
date_add(cast('2008-12-31' as timestamp), cast(substr(enc_datetime, 1, 3) as int)) as eventDate,
concat(
	substr(concat("00", cast(cast((cast(substr(enc_datetime, 4) as int) * 30 / 60) as int) %24 as string)), -2, 2),":", 
	substr(concat("00", cast(cast(cast(substr(enc_datetime, 4) as int) * 30 % 60 as int) as string)), -2, 2)
) as my_time

FROM #table# t1
```
- query ini merubah data yang ada di table, data yang akan di konversi ialah data yang ada di enc_datetime<br/>

- hasilnya tertera pada dibawah ini<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/13.PNG "file reader")<br/>

- memasang node spark dql qury dengan tujuan berbeda, yaitu dengan meng ekstrak fitur datetime<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/14.PNG "file reader")<br/>

``` SELECT 

meterid,
kw30,
eventDate,
year(eventDate) as year,
month(eventDate) as month,
weekofyear(eventDate) as week,
date_format(eventDate, 'EEEE') as dayOfWeek,
hour(my_time) as hour

FROM #table# t1
```

- mengekstrak atribut menggunakan sintaks diatas, menggunakan node diatas, dan didapati kolom baru tahun,buan, minggu, hari dan jam<br/>
dan didapati hasil seperti ini<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/15.PNG "file reader")<br/>

- memasang node spark dql qury dengan tujuan berbeda, yaitu dengan meng ekstraksi pada weekend/weekdays<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/16.PNG "file reader")<br/>

``` SELECT *, 
CASE 
WHEN dayOfWeek in ('Saturday','Sunday') 	THEN 'WE' 
									        ELSE 'BD' 
END as dayClassifier

from #table#
```

- dengan menjalankan sintaks ini dan mendapati hasil seperti ini<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/17.PNG "file reader")<br/>

- memasang node spark dql qury dengan tujuan berbeda, yaitu dengan mengkategorikan menjadi 5 kategori<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/18.PNG "file reader")<br/>

``` SELECT meterID, kw30, eventDate, year, month, week, dayOfWeek, dayClassifier, hour,
CASE 
WHEN hour >=7 AND hour <9 THEN '7-9'
WHEN hour >=9 AND hour <13 THEN '9-13' 
WHEN hour >=13 AND hour <17 THEN '13-17' 
WHEN hour >=17 AND hour <21 THEN '17-21' 
WHEN hour >=21 OR hour <7 THEN '21-7'  
								 
END as daySegment

from #table#
```

- dengan menjalankan sintaks ini dengan mengkatergori 7-9,9-13,13-17,17-21,21-7<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/19.PNG "file reader")<br/>

- kemudian dilakukan metode agregation and timeseries, semua yang ada pada proses memtanode Aggregation and timeseries<br/>
dilakukan menggunakan node spark groupby dengan menentukan kolom apa saja yang digunakan dan merata-ratakan kolom yang dipilih<br/>
dan coloumn rename untuk merename nama kolom, dan node joiner untuk melihat hasil dijadikan menjadi satu.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/20.PNG "file reader")<br/>

- konfigurasi untuk memilih kolomnya dan hasil pada pengelompokan<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/21.PNG "file reader")<br/>

- konfigurasi untuk melakukan konfigurasi pada penamaan kolom dan hasil pada pengelompokan<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/22.PNG "file reader")<br/>

- hasil pada pengelompokan<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/23.PNG "file reader")<br/>

- pivot with average, untuk mengetahui pivot pada parameter yang di inginkan, dan setekah itu dilakukan coloumn rename <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/24.PNG "file reader")<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/25.PNG "file reader")<br/>

- dan didapati hasil seperti ini <br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/26.PNG "file reader")<br/>

- menggunakan node sparksql query untuk menghitung rata rata presentse pemakaian perhari datri rata-rata perminggu dan presentase persegmen<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/27.PNG "file reader")<br/>
```
SELECT `meterID`, `totalKW`, `avgYearlyKW`,`avgMonthlyKW`,`avgWeeklyKW`,
       `avgMonday`,`avgTuesday`,`avgWednesday`,`avgThursday`,`avgFriday`,`avgSaturday`,`avgSunday`,
       `avgDaily`,`avg_7to9`,`avg_9to13`,`avg_13to17`,`avg_17to21`,`avg_21to7`,`avg_BD`,`avg_WE`,`avgHourly`,
       (avgMonday / avgWeeklyKW) * 100.0 as pctMonday,
       (avgTuesday / avgWeeklyKW) * 100.0 as pctTuesday,
       (avgWednesday / avgWeeklyKW) * 100.0 as pctWednesday,
       (avgThursday / avgWeeklyKW) * 100.0 as pctThursday,
       (avgFriday / avgWeeklyKW) * 100.0 as pctFriday,
       (avgSaturday / avgWeeklyKW) * 100.0 as pctSaturday,
       (avgSunday / avgWeeklyKW) * 100.0 as pctSunday,
       (avg_7to9 / avgDaily) * 100.0 as pct_7to9,
       (avg_9to13 / avgDaily) * 100.0 as pct_9to13,
       (avg_13to17 / avgDaily) * 100.0 as pct_13to17,
       (avg_17to21 / avgDaily) * 100.0 as pct_17to21,
       (avg_21to7 / avgDaily) * 100.0 as pct_21to7
       
FROM #table#

```
- mendapati hasil dari sparksql query<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/28.PNG "file reader")<br/>

# Modeling (MLib)

- memasang node spark normalizer<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/29.PNG "file reader")<br/>

- melakukan konfigurasi dengan seperti ini<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/30.PNG "file reader")<br/>

- didapati hasil dari tersebut<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/31.PNG "file reader")<br/>

- memasang node spark PCA dengan memilih 96 % data yang tidak direduksi, yang tidak dipilih adalah kolom meterID<br/>
dan berikut adalah hasilnya<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/32.PNG "file reader")<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/33.PNG "file reader")<br/>

- memasang node spark kmeans untuk cluster dengan algoritma kmeans dan berikut adalah hasilnya<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/34.PNG "file reader")<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/35.PNG "file reader")<br/>

- memasang node spark column filter yang akan memfilter dengan memilih kolom meterid dan cluster dan berikut hasilnya<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/36.PNG "file reader")<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/37.PNG "file reader")<br/>

- memasang node spark joiner menggabungkan hasil PCA<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/38.PNG "file reader")<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/39.PNG "file reader")<br/>

# Evaluation (MLib)

- dari data yang didapat memasang node spark to table agar bisa digunakan pad node sebelumnya<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/40.PNG "file reader")<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/41.PNG "file reader")<br/>
 
- memasang node denormalizer agar mengubah nilai yang tidak dinormalisasikan<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/42.PNG "file reader")<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/43.PNG "file reader")<br/>
 
- memasang node number to string agar cluster, supaya dapat divisualisasikan dengan mudah<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/44.PNG "file reader")<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/45.PNG "file reader")<br/>

- memasang node color manager untuk mengubah warna visualisasi plot<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/46.PNG "file reader")<br/>
 
- memasang node scatter plot, untuk membuat plotting<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/47.PNG "file reader")<br/>
 
- memasang node table view untuk menampilkan interaktif table<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/48.PNG "file reader")<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/49.PNG "file reader")<br/>
 
- memasang node table to spark untuk mengubah menjadi spark<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/50.PNG "file reader")<br/>
  
- memasang node spark coloumn rename<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/51.PNG "file reader")<br/>
 
# Deployment (MLib) 

- memasang node spark to hive gunanya untuk mengeksport ke bentuk hivek<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/52.PNG "file reader")<br/>
  
- memasang node spark to parquet untuk mengeksport ke bentuk parquet<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_7/picture/53.PNG "file reader")<br/>


 


