# docker 설치 확인 at AWS Linux 2
인스턴스 생성 및 방화벽 설정 후 ssh로 접근해서 

docker ps -a

없으면, 일단 docker란 명령어가 없다고 뜨고, 

sudo um install docker-io

로 설치가능하고 추가로 시작 및 권한 부여

sudo systemctl start docker

sudo setfactl -m user:ec2-user:rw /var/run/docker.sock

후

docker ps -a 하면 리스트 확인가능

## docker 개별 컨테이너 접속하기
docker exec -it (도커 이름) /bin/bash

python 가상환경 접속이랑 유사한듯_'source myvenv/bin/activate'

## Dockerfile 편집하기
vim Dockerfile 로 문서 생성 후,아래 와같은 명령어로 편집

(서버에서 docker image가 '앞으로 서버에서 전개 됬을때의' 청사진 정도)

### 기존에 alpine 에 올라간 톰켓 '도커 이미지'(수업중에는 안한듯하다)
FROM tomcat:9-jre8-alpine 

### server.xml에 jndi 정보 및 구조정보
COPY server.xml /usr/local/tomcat/conf

### 앞으로 전개될 서버_tomcat을 활용한다면_의 앞선 환경을 모두 지우는 과정으로 이해
RUN rm -rf /usr/local/tomcat/webapps/ROOT.war
RUN rm -rf /usr/local/tomcat/webapps/ROOT
RUN rm -rf /usr/local/tomcat/webapps/docs
RUN rm -rf /usr/local/tomcat/webapps/examples
RUN rm -rf /usr/local/tomcat/webapps/host-manager
RUN rm -rf /usr/local/tomcat/webapps/manager

### 청소된 톰캣환경에 war 배치
COPY ROOT.war /usr/local/tomcat/webapps

### 타임존 설정
ENV TZ=Asia/Seoul
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

### 8080포트
EXPOSE 8080

## Dockerfile 'Image' 만들기, not file
### 현재 프로젝트 기준_maven,spring,tomcat_ Dockerfile 구성 요소
배포 시, 리눅스 상태 기준
/opt/tomcat/conf의 server.xml

/opt/tomcat/webapps의 ROOT.war

해당 리렉토리 이동 후, 각각

cp ROOT.war ~

cp server.xml ~

로 Dockerfile이 있는 홈디렉토리로 카피

### docker build -t (도커이미지명) .
아마 . 의 의미는 현재 디렉토리를 기준으로 하라는 것으로 보이고, 별도로 Dockerfile을 지명하진 않았지만,현재 기준 위치에서 그냥 싹다 담는 느낌이다

## 도커 이미지 리스트 확인
docker images

## 도커 허브 활용하기

### 자동로그인 환경 설정
docker login

### 태그 생성
push를 위해서 마치 index 추가 처럼 태그 만들어줘야함

#### docker tag (기존 id)          (새로 부여할 태그명)
이때 중요한 게, 새로부여할 태그명에서 (도커 사용자명)/가 필수라고 한다.

docker tag review/aws:lastest bloodjino/review:0.0.1

### 도커 이미지 푸시 와 풀
example)
sudo docker push bloodjino/review:0.0.1

docker pull bloodjino/review:0.0.1

!! 도커허브 홈페이지에서는 404 뜨는 이상하게 명령어 먹고 다운로드 완료됨

### pull한 도커 이미지를 내 도커허브 id에 맞춰서 변경, 확인, push
docker tage bloodjino/review:0.0.1 devsacti/dockerpractice:0.0.2

docker images

docker push devsacti/dockerpractice:0.0.2

!! 자꾸 접근 거부당해서, 살펴보니까, 강의때와 달리 레포 생성 전에 이메일 계정으로 활성화를 해야하고, 그 다음에도 안되서 재접속하니까 됨

