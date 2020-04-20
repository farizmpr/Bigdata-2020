## Bigdata 2020

# Dokumentasi Praktek Recommendation System menggunakan KNIME

* [Tools](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_4/README.md#Tools)<br/>
* [Install](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_4/README.md#Install)<br/>
* [Kafka Docker](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_4/README.md#Kafka_Docker)<br/>
* [Running](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_4/README.md#Running)<br/>
* [Testing](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_4/README.md#Testing)<br/>

# Tools
Dari tugas ini kita membutuhkan beberapa tools yang digunakan:
1. Docker Desktop( dengan syarat spesifikasi windows 10 pro jika di install di windows)
2. Conductor
3. zookeeper
4. kafka

# Install
- yang pertama install docker dari web yang tertera https://www.docker.com/
- conductor untuk pengecekan cluster https://www.conduktor.io/

# Kafka Docker
sebelumnya pastikan docker desktop sudah terinstall.<br/>
![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_4/picture/docker.PNG "docker")<br/>

setelah menginstall semuanya, kita akan membangun infrastruktur kafka dengan docker,<br/>
infrastruktur yang dibuat itu adalah 2 broker dan 1 zookeeper sebagai cluster.<br/>
.
```version: '2'

networks:
  kafka-net:
    driver: bridge

services:
  zookeeper-server:
    image: 'bitnami/zookeeper:latest'
    networks:
      - kafka-net
    ports:
      - '2181:2181'
    environment:
      - ALLOW_ANONYMOUS_LOGIN=yes
      
  kafka-server1:
    image: 'bitnami/kafka:latest'
    networks:
      - kafka-net    
    ports:
      - '9092:9092'
    environment:
      - KAFKA_CFG_ZOOKEEPER_CONNECT=zookeeper-server:2181
      - KAFKA_CFG_ADVERTISED_LISTENERS=PLAINTEXT://localhost:9092
      - ALLOW_PLAINTEXT_LISTENER=yes
    depends_on:
      - zookeeper-server
      
  kafka-server2:
    image: 'bitnami/kafka:latest'
    networks:
      - kafka-net    
    ports:
      - '9093:9092'
    environment:
      - KAFKA_CFG_ZOOKEEPER_CONNECT=zookeeper-server:2181
      - KAFKA_CFG_ADVERTISED_LISTENERS=PLAINTEXT://localhost:9093
      - ALLOW_PLAINTEXT_LISTENER=yes
    depends_on:
      - zookeeper-server
```
- di dalam script itu membangun zookeeper server sebagai cluster, nantinya<br/>
  ketika kafka berjalan, zookeper ini dibutuhkan pada saat itu.<br/>
- dan yang terakhir, untuk membangun broker, 2 broker. ketika menginstall <br/>
  docker kita harus mensetting port dari kafka. pada kasus ini menggunakan port.<br/>
  kita mengambil yang kafka-server2 9093:902, artinya menggunakan port 9092 dan<br/>
  tcp port 9092
  
  Information : jika ingin menambah broker dapat menambah dibawahnya saja seperti dengan<br/>
                melakukan settingan port yang dibedakan
``` kafka-server3:
    image: 'bitnami/kafka:latest'
    networks:
      - kafka-net    
    ports:
      - '9094:9092'
    environment:
      - KAFKA_CFG_ZOOKEEPER_CONNECT=zookeeper-server:2181
      - KAFKA_CFG_ADVERTISED_LISTENERS=PLAINTEXT://localhost:9094
      - ALLOW_PLAINTEXT_LISTENER=yes
    depends_on:
      - zookeeper-server
```

# Running

- yang pertama setelah membuat file docker-compose.yaml / yml di dalam folder yang telah<br/>
  dipersiapkan, jalankan syntax ``` compose up -d ```<br/>
  ![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_4/picture/compose.PNG "docker")<br/>
- dan akan menampilkan pesan seperti ini sesuai yang dipasang di script 
  ![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_4/picture/success_compose.PNG "docker")<br/>
- melakukan pengecekan di docker 
  ![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_4/picture/docker_compose.PNG "docker")<br/>

# Testing

- melakukan testing di conduktor, dan awalnya harus mensetting dengan mencocokan yang ada di script<br/>
  ![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_4/picture/conductor_install.PNG "docker")<br/>

- melakukan pengecekan bahwa kafkanya sudah terbuat<br/>
  ![alt text](https://github.com/farizmpr/Bigdata-2020/blob/master/tugas_4/picture/conductor_install.PNG "docker")<br/>


