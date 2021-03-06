# π Docker Logging π

μμ€νμ΄ μ μμ μΌλ‘ μ΄μλ¨μ νμΈνκ³  λ°μλ λ¬Έμ μ λν λλ²κΉμ ν¨μ¨μ μΌλ‘ κ΄λ¦¬νκ³ μ νλ€λ©΄, μ»¨νμ΄λ λͺ¨λν°λ§μ νμ μ΄λ€.

## π¦ λμ»€ κΈ°λ³Έ λ‘κΉ

λμ»€κ° μ κ³΅νλ κΈ°λ₯μΌλ‘ λ³λμ μΈμλ₯Ό λͺμνμ§ γλ³μκ±°λ λ€λ₯Έ λ‘λ© SWλ₯Ό μ€μΉνμ§ μμλ€λ©΄, `**.log`νμΌλ‘ λ¨κΈ΄λ€.

```shell
docker logs <Container Name>
```

### κΈ°λ³Έ λ‘κΉ λ¨μ 
- STDOUT / STDERR λ§ μ²λ¦¬νλ―λ‘ λ‘κ·Έλ₯Ό νμΌλ‘λ§ κΈ°λ‘ν  μ μλ€.
- μ»¨νμ΄λκ° μ΄μμ€μ μλ€λ©΄ κΈ°λ³Έ λ‘κΉ κΈ°λ₯μ logλ₯Ό κ³μν΄μ κΈ°λ‘νμ¬ μ¬μ©μμ λμ€ν¬ μ©λμ μ‘μλ¨Ήμ κ²μ΄λ€.

## π¦ ELK λ₯Ό μ΄μ©ν λ‘κΉ

![μ λͺ© μμ](https://user-images.githubusercontent.com/65659478/171559548-2abf6a69-08da-45b4-bb8c-8cee3d1e942c.png)

### Elasticsearch

μ€ μ€μκ° κ²μ κΈ°λ₯μ μ κ³΅νλ νμ€νΈ κ²μ μμ§μ΄λ€. 

λμ©λμ λ°μ΄ν° μ²λ¦¬λ₯Ό μν΄μ μ¬λ¬ κ°μ λΈλλ‘ μ½κ² νμ₯μ΄ κ°λ₯νλλ‘ μ€κ³λμκ³ , λλμ λ‘κ·Έ κ²μμ μ ν©νλ€.

### Logstash

μμ λ‘κ·Έλ₯Ό μ½κΈ° μν λκ΅¬λ‘, λ‘κ·Έλ₯Ό λΆμνκ³  νν°λ§νμ¬ μΈλ±μ€ λλ μ μ₯μμ κ°μ λ€λ₯Έ μλΉμ€λ‘ λ‘κ·Έλ₯Ό μ λ¬νλ€.

### Kibana

μΌλ μ€ν±μμΉμ λν JS κΈ°λ°μ κ·Έλν½ μΈν°νμ΄μ€μ΄λ€. 

μΌλ μ€ν±μμΉ μΏΌλ¦¬λ₯Ό μ€ννκ³  κ²°κ³Όλ₯Ό λ€μν μ°¨νΈλ‘ μκ°νν  λ μ¬μ©λλ€.


## π¦ ELk + Logspout μ€κ³

![](https://miro.medium.com/max/1400/0*qxW9DS-RGveqqwBQ.png)

κ·Έλ¬λ `LOG μμ§κΈ°`μλ μ¬λ¬ λ°©μμ΄ μμ§λ§ Docker API μΉνμ μΈ `logspout` λ₯Ό μ¬μ©ν  κ²μ΄λ€.

μμΈν νμΌ κ΅¬μ±μ [Repository](https://github.com/KIM-JS-95/PillI-Info-Service) λ₯Ό μ°Έκ³ ν΄ μ£ΌμΈμ.

### DIR Tree

```
PILLSSERVICE_BE
β
ββ ...
β
ββ elk
β  ββ elasticsearch
β  β  ββ config
β  ββ kibana
β  β  ββ config
β  ββ logstash
β      ββ config
ββ gradle
β  ββ wrapper
ββ presentation
ββ proxy
β  ββ conf
ββ src
    ββ main
        ββ java
        β  ββ ...
        β
        ββ resources
            ββ ...
```


### docker-compose

```shell
version: '3.0'
services:

  ...

-----  1

  logspout:
    container_name: logspout
    image: gliderlabs/logspout:latest
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    links:
      - logstash
    ports:
      - "8000:80"
    command: syslog+tls://logstash:5000
    depends_on:
      - logstash
      - kibana
      - elasticsearch
    networks:
      - elk
    restart: always

-----  2

  logstash:
    build: elk/logstash/
    container_name: logstash
    volumes:
      - ./elk/logstash/config:/etc/logstash/conf.d
    links:
      - elasticsearch
    environment:
      LOGSOUT: ignore
    command: -f /etc/logstash/conf.d/
    ports:
      - "5000:5000"
    networks:
      - elk

-----  3

  kibana:
    build: elk/kibana/
    container_name: kibana
    volumes:
      - ./elk/kibana/config/:/opt/kibana/config/
    ports:
      - "5601:5601"
    links:
      - elasticsearch
    environment:
      LOGSOUT: ignore
      ELASTICSEARCH_URL: http://elasticsearch:9200
    networks:
      - elk
    depends_on:
      - elasticsearch

-----  4

  elasticsearch:
    build: elk/elasticsearch/
    volumes:
      - ./elk/elasticsearch/config/:/opt/elasticsearch/config/
    container_name: elasticsearch
    ports:
      - "9200:9200"
      - "9300:9300"
    environment:
      ES_JAVA_OPTS: "-Xms2g -Xmx2g"
      discovery.type: single-node
    networks:
      - elk

networks:
  elk:
    driver: bridge
```

### 1. logspout

`Logspout` μ Docker μ»¨νμ΄λ λ‘κ·Έμ©μΌλ‘ νΉλ³ν μ€κ³λ μ€ν μμ€ λ‘κ·Έ λΌμ°ν°μ΄λ©°
λμΌν νΈμ€νΈμμ μ€νλλ λ€λ₯Έ λͺ¨λ  μ»¨νμ΄λμμ λ‘κ·Έλ₯Ό μμ§ν λ€μ μ νν λμμΌλ‘ μ λ¬νλ μ­ν μ μννλ€.


ν΄λΉ μ΄λ―Έμ§ μ¬μ©μ Docker Hub Repoλ₯Ό νμΈν΄μΌνλ€. 

`commend: ~~` μ κ²½μ° λΈλ‘κ·Έμ λ°λΌ λ€λ₯΄κΈ° λλ¬Έμ **λ¬Έμλ₯Ό λ°λΌ μ€μ νλ κ²μ΄ μ’μ λ°©λ²μ΄λ€.**

### 2. logstash

λ‘κ·Έ λ° λ°μ΄ν° μμ§ λ° λ³ν μμ΄μ νΈ μ­ν μ μννλ€.

`configuration`μμ μ€μ λ ν¬νΈμ νμΌ νμμ λ°λΌ `Logstash`λ ElasticSearchμΌλ‘ μ λ³΄λ₯Ό μ μ‘νκ² λλ€.

### 3. kibana

Elasticsearchμ λΉ λ₯Έ κ²μμ ν΅ν΄ λ°μ΄ν°λ₯Ό μκ°ν λ° μ€μκ° λͺ¨λν°λ§μ μννλ Tool μ΄λ€.


### 4. Elasticsearch

Elasticsearchλ Apache Luceneμ κ΅¬μΆλμ΄ λ°°ν¬λ μ€μκ° κ²μ λ° λΆμ μμ§μΌλ‘

`logstash`λ‘ λΆν° λ°μ λ°μ΄ν°λ₯Ό DataMining νμ¬  λ‘κ·Έ λΆμ, μ μ²΄ νμ€νΈ κ²μ, λ³΄μ μΈνλ¦¬μ μ€, λΉμ¦λμ€ λΆμ λ° μ΄μ μΈνλ¦¬μ μ€ μ¬μ© μ¬λ‘μ μΌλ°μ μΌλ‘ μ¬μ©λλ€.

Window μμ λ€μ μλ¬κ° λ°μνλ κ²½μ° λ€μκ³Ό κ°μ΄ μ‘°μΉν΄ μ£ΌμΈμ


    ERROR: [1] bootstrap checks failed es01 | [1]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]


```shell
## Docker μμ€ν μ μ
wsl -d docker-desktop

## λμ»€ μμ²΄ μ΅λ μ©λ λ³κ²½
sysctl -w vm.max_map_count=262144

```

multi node μλ¬μ κ²½μ° `ver.7.xx` μ΄νλΆν° λ°μνμ§ μλλ€ λ°ννμ§λ§ 

λ°μνλ κ²½μ° `environment`μ λ€μκ³Ό κ°μ΄ μΆκ°νμ

```shell
discovery.type: single-node
```


 


## Result
![μ λͺ© μμ](https://user-images.githubusercontent.com/65659478/171555730-fe27fc17-968e-4688-b9e5-4454d0851935.png)

## Repository

- [PillService_Repo](https://github.com/KIM-JS-95/PillI-Info-Service)

# π Reference
- [μ λλ‘ λ°°μ°λ λμ»€](http://www.yes24.com/Product/Goods/34648781)
- [elastic](https://www.elastic.co/kr/what-is/elk-stack)
- [docker-compose ERROR: bootstrap checks failed - StackOverFlow](https://stackoverflow.com/questions/57998092/docker-compose-error-bootstrap-checks-failed-max-virtual-memory-areas-vm-ma)