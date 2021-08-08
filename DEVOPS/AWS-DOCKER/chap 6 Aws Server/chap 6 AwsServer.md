# AWS server config with Jira issue
텍스트와 글을 저장하기 위한 RDS,s3 생성, 로그인 기능 구현 등 이슈를 Jira에 등록한 뒤 이를 바탕으로 문제 해결

## RDS 생성
기존 RDS 인스턴스 활용

### DBeaver란 DB툴을 통한 DB접근
나는 기존 mysql workbench 활용

새로운 스키마 생성; devsacti_spring_webservice
charset/collations; 강의와 같이, utf8mb4, utf8mb4_general_ci

![columns](https://user-images.githubusercontent.com/82523058/126755463-aab56727-711e-49ce-bc9c-349ab844956f.JPG)

### application.properties 설정

#### SERVER PORT
server.port=8081
server.servlet-path=/*

기존 플젝도 8080이라, 8081로 설정(참고로 장고는 8000)

#### VIEW
spring.datasource.driverClassName=net.sf.log4jdbc.sql.jdbcapi.DriverSpy
spring.datasource.url=jdbc:log4jdbc:mariadb://review.cm03m1qy5nzi.ap-northeast-2.rds.amazonaws.com:3306/review
spring.datasource.username=admin
spring.datasource.password=admin142536

spring boot 플젝의 real-db와 같이, 

관련 드라이브, 내 db url, 그리고 아이디 비번
(참고로 여기에는 노출하지 않고, 더불어 이제부턴 pom을 gitingore에 추가, 이런 문제를 위해서 원래는 서버에 별도로 관련 파일을 올리는 것이 정법이라한다.)

### pom.xml 설정
나의 경우, 최근 rds이고, mariadb라 정확하게 변경함

        	<dependency>
			<groupId>org.mariadb.jdbc</groupId>
			<artifactId>mariadb-java-client</artifactId>
			<scope>runtime</scope>
		</dependency>

## S3 생성
aws s3에서 default값으로 생성하면됨, 거의 폴더 생성급 난이도

아마도, apache로 구현한 웹서버와 같은 형태로 예상, 그러므로 임의접근 매우 엄격히 조절해야할듯


외부 브라우져에서 접근할수있게하려면,

우선 'bitbucket', 그리고 'file' 두 단계에 걸쳐 액세스를 퍼블릭으로 설정해줘야함
일단 학습상 모두에게 access허용했는데, Access Control List라는 걸로 제어해줘야함.
근데 약간 복잡해서 추후보강
