# ๐ Dockerfile build error ๐


Dockerfile๋ก `./gradlew build` ํ  ๊ฒฝ์ฐ 

> Error with gradlew: /usr/bin/env: bash: No such file or directory


์๋ฌ๊ฐ ๋ฐ์ํ๋ค. Dosํ๊ฒฝ๊ณผ unix ํ๊ฒฝ์ ์ฐจ์ด์์ ๋ํ๋๋ ํ์๊ฐ์ผ๋
๋ฐ๊ฟ์ฃผ๋ฉด๋๋ค.

```
sudo apt-get install dos2unix
dos2unix ./gradlew
./gradlew bootRun
```