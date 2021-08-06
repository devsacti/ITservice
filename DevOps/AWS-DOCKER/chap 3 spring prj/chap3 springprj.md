# config spring
maven과 spring을 활용한 웹서비스 구현

## spring project git push
!! 수업과의 동일환경을 위해 bitbucket에 푸시 !!

https://bitbucket.org/devsacti/devsacti-springboot-webservice/src/master/

!! 다만, chap 6에서 새로운 추가되는 코드에 DB 계정정보가 있기 때문에, chap3 이후는 푸시안함(Jenkins는 비공개 bitbucket repo활용) !!

## deploy
/home/ec2-user에서 작업하던 스프링 부트 수업과 달리,

/ 디렉토리, 즉 루트 디렉토리에 원래 존재하는
opt라는 디렉토리에서 작업함

/opt에서 tomcat이라는 디렉토리에서 톰캣설치 후, webapp이란 디렉토리를 또 만들고 여기에 war를 올린다.

그리고 기존에 설정되서 제공된 server.xml과 가동된 톰캣을 바탕으로 review란 디렉토리가 또 생성되고 웹서비스가 실행

# chap 6 관련 추가 내용
## src/main/resources/resources 에서 외부 DB 참조 설정
pom.xml에서 외부 DB 정보를 기입
## src/main/resources/mapper 에서 데이터 송수신 설정
resources 디렉 하위에 mapper 디렉을 만들고 그곳에 review.xml을 만든다. html와 유사한 값의 양식에 따라 select 태그 하위에 원하는 SQL 기입(id는 getReviewList)

그리고 이것과 연동할 (ex)ReviewVO.java파일을 기입

## src/main/java/../mapper 에서 (ex)ReviewVO.java 생성
~VO.java의 역할은 DAO와 유사, 통신할 데이터 구조를 정의한 클랙스

##  src/main/java/../mapper 에서 java project 프로그램과 DB 사이를 중개할 interface 생성
이 인터페이스가 ReviewVO 단위로 생성된 리스트로 정의된 함수(이자 xml파일 내 명령문의 id)를 호출준비
특이점은 이클립스 인텔리제이와 달리, I마크가 따로 새겨지진 않는듯함

##  src/main/java/../service 에서 ReviewService.java 생성하고 implement는 아니고 autowired로 위 인터페이스 사용
참고로 mapper 디렉과 같은 층위


## project of [gradle and springboot, JPA]와의 비교
### 의존성 설정
pom.xml of maven vs build.gradle of gradle

### 파일 구조 및 경로
resource 디렉토리의
application.propertes + main의 config 폴더의 java파일들  vs application.propertes

### 데이터 양식
VO vs DTO,DAO
* 실무마다 다르겠지만 일단 위와같이 정리, Value object로서 데이터 송수신의 단위이고 특별히 세분화 안된것같다.
* 또한 수업의 경우, lombok 없이 getter setter를 자동생성함

### 작동과정 from DB
mapper의 review.xml with ReviewVO.java(클래스), ReviewMapper.java(인터페이스) with Reviewservice.java  => controller 형태로 구현할듯

작동과정은 이 역순으로

controller가 ReviewService 호출, 인터페이스의 함수가 호출되는데,

아마도 마이베티스가 xml 내에 이 함수명과 동일한 id로 생성된 SQL문과 지정된 VO로 모델로 전달해서 데이터를 얻음

!! 일반적으로 자바 인터페이스를 implement한 클래스가 자신의 클래스 내에서 인터페이스에 선언된 함수에 대응하여 새로 함수를 재정의하듯이,

여기선 인터페이스에 선언된 함수에 대해서 재정의되는 과정은 동일한데, 그 매핑의 종착지가 SQL문 with VO

#### JPA

repository,Dao, service => controller

### Tip
error 리스트로 보기
window -> show views -> problems
