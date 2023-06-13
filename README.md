# Hangman 서비스를 Docker Image로 빌드하기
> 프로그래머스 데브코스 - 데이터 엔지니어링 1기
>
> 11주차 2일차 숙제  

Flask로 hangman 게임이 작성된 [레파지토리](https://github.com/learndataeng/hangman_web)의 소스를 fork 한 후,   
해당 서비스가 Docker Container 실행될 수 있도록 Dockerfile을 추가하는 실습  

<br>

## #️⃣ 구현사항
- Dockerfile
- 만든 Docker Image를 [Docker Hub](https://hub.docker.com/repository/docker/hmk9667/hangman/general)에 등록 

## #️⃣ 과정 
1. Dockerfile 작성하기
    - `FROM` : 기본 베이스 이미지는 python:3.8-slim-buster 
    - `LABLE` : 메타데이터. Maintainer로 작성자
    - `EXPOSE` : 실제로 포트 맵핑하는 것이 아님. 추후 사용자가 포트번호를 할 때 참고하라고 적는 정보
    - `CMD` : 컨테이너 run할 때 실행할 명령어를 리스트로 작성함
2. 이미지로 빌드 후 정보 확인 (Windows)
```shell
docker build -t hmk9667/hangman .
docker image ls
docker inspect hmk9667/hangman
```
3. 컨테이너로 실행하기
    - `-d` : 백그라운드로 실행함
    - `-p 4000:4000` : 컨테이너 내부 4000포트를 호스트(로컬)의 4000포트와 맵핑
```shell
docker run -p 4000:4000 hmk9667/hangman
```

4. Docker Hub로 이미지 업로드
```shell
docker push hmk9667/hangman
``` 
<br>

## #️⃣ 결과화면
![image](https://github.com/HyeM207/hangman_web/assets/63229014/cbdea548-28dc-45e3-9e49-2ab4e81acf04)


