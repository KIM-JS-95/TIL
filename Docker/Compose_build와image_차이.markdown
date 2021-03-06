# ๐ ์ปดํฌ๋ํธ์์์ build ์ image์ ์ฐจ์ด ๐

## ๐ image

`image` means docker compose will run a container based on that image

Docker Hub์์ ํด๋น ์ด๋ฏธ์ง๋ฅผ ๋ค์ด๋ก๋ ํ ์ด๋ฏธ์ง์์ ์ปจํ์ด๋๋ฅผ ์คํํ๋ค.

## ๐ build

`build` means docker compose will first build an image based on the Dockerfile found 
in the path associated with build (and then run a container based on that image).

ํด๋น ๊ฒฝ๋ก์ `Dockerfile`์ ๊ธฐ๋ฐ์ผ๋ก ๋จผ์  ์ด๋ฏธ์ง๋ฅผ ๋น๋ํ๊ณ  ๊ทธ๊ฒ์ ๊ธฐ๋ฐ์ผ๋ก ์ปจํ์ด๋๋ฅผ ์คํํ๋ค.



## ๐ ๊ถ๊ธ์ฆ ๋ฐ์

### 1.`build` ๋ช๋ น์ด ๋ณด๋ค `image`๋ฅผ ์ฌ์ฉํ๋ ๊ฒ์ด ์ข์ง ์์๊น?

[StackOverFlow](https://stackoverflow.com/questions/42170124/docker-compose-when-to-use-image-over-build) ์ ๋ฐ๋ฅด๋ฉด `build` ๋ช๋ น์ด๋ฅผ 2๊ฐ์ง ์ํฉ์์ ์ฌ์ฉํ๊ธฐ๋ฅผ ๊ถ์ฅํ๋ค.

- development
- automated testing

์ผ๋ฐ์ ์ผ๋ก `build`๋ image๋ฅผ ์ฝ๋ ํ๋ก๋์์ด ์ค๋น ์ค์ด๊ฑฐ๋ ํ์คํธ ๊ณผ์ ์์ ์ฌ์ฉํจ์ ์๋ ธ์ผ๋ฉฐ ์ดํ ๊ฐ์ธ Docker Hub์ ์ด๋ฏธ์ง๋ฅผ ์๋ก๋ ํ์ฌ
๋ถ๋ฌ์ค๋ ๋ฐฉ์์ผ๋ก ์ค๊ณํ๋ค ๋งํ๋ค.

๋ค์๋งํ๋ฉด Hub์ ์กด์ฌํ๋ image๋ ์ด๋ฏธ ๊ฒ์ฆ๋ ์ด๋ฏธ์ง ์ด๋ฉฐ ์ฌ์ฉํ๊ธฐ ์์ ํจ์ ์ฃผ์ฅํ๊ณ  

`build` ๋์์ด ๋๋ Dockerfile์ ๊ฒฝ์ฐ ๋น ๋ฅธ ํ์คํธ๋ฅผ ํ์ธํ  ์ ์๋ ์ฅ์ ๊ณผ Hub์ ๋ฐ๋ณต์ ์ธ push๋ฅผ ํผํ๊ธฐ ์ํจ์ธ ๊ฒ์ด๋ค.

### 2. ์ ๋ฆฌ

๊ทธ๋ฌ๋ `@GHETTO.CHILD` ์ ์ ์ ์ฝ๋ฉํธ์๋ **ํญ์ ์ด๋ฌํ ๋ฐฉ๋ฒ์ด ํด๋ต์ ์๋๋ค.** ๋ผ๊ณ  ์๋ ธ๋ค. 

์ฆ, ์์์ ํ๋ฆ์ ๋ฐ๋ผ ๋ณ๊ฒฝ๋  ์ ์๋ ๋ฌธ์ ์ด๋ฉฐ ์ด๊ฒ์ ํ์ฌ์ ์ง์นจ์ ๋ฐ๋ฅด๋ ๊ฒ์ด ์ข๋ค ๋งํ๋ค.

- How teams run their build, ship, deploy varies greatly as they figure out what works best for them and their product so the above build . scenarios may not be accurate for all cases, but is accurate for how my company uses compose.
- This assumes build . in a docker-compose context and not a docker
 build context.

# ๐ Reference

- [Docker Compose when to use image over build - StackOverFlow](https://stackoverflow.com/questions/42170124/docker-compose-when-to-use-image-over-build)
- [Difference between 'image' and 'build' within docker compose - StackOverFlow](https://stackoverflow.com/questions/34316047/difference-between-image-and-build-within-docker-compose)