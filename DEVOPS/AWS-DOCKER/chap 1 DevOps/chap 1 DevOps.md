# DevOps
개발와 운영의 유기적 연결을 중요시하고 지원하는 소프트웨어 개발 방법론 => jira(애자일 기반, '협업툴', '프로젝트 이슈 관리툴') with aws/docker

+참고
agile + devops에 대한 설명, https://ksy93.tistory.com/entry/Jira-Bitbucket-Jenkins

+참고
DDD(Domain Driven Design) which consists of strategic design과 tactical design(각각 Domain model과 layered architecture~기술명세서, 혹은 개념설계와 프로그래밍을 위한 구체적 설계)

비즈니스 Domain 에 충실해서 설계하자!(strategic design or modeling)

요구계획서는 하늘에서 뚝 떨어지는 게 아니라, 실제 비즈니스 영역들(Business Domain별 expert)와의 소통에서 만들어짐, 근데 전문적인 영역일수록, 실무자와 운영 및 개발자 간의 괴리가 상당

대체로 실무자쪽에서의 일방적인 Contexts_특정 상황이나 사건 그리고 이에 대한 선택지나 처리방법 등_ 제공과 요구로 인해 개발자는 개발에 있어 엄청난 비효율성과 반복작업 발생함.
특히, 도메인별로 의미가 다른 동음이의어들도 상당한 문제를 일으켰다고함. 그래서 devops의 협업툴에서 이러한 부분을 도메인별로 미리 정리하여 해소하기 위해 Ubiquitous Language를 만든다고 함.

이러한 기존 '쌍방'의사소통 문제를 해결하기 위해 주어진 domains별 contexts들을 비즈니스 목적별로 그룹핑
 
Context Map_Bounded Context 간 관계지도_와 이에 대응하는 Micro service로 대응, 이런 것들이 모여서 Domain Model이 생성되고 이를 바탕으로 구현을 위한 설계도(tactical design) 생성 

https://happycloud-lee.tistory.com/94

# Jira
'개발 프로세스(작업 흐름)'; Operations측의 요구계획서, 코드, 빌드, 테스트, 패키지(ex WAR), 릴리즈, 모니터링'의 순환 를 jira를 통해서 관리가능하다.
같은 회사 상품인 atlassian인 conflunce(프로젝트 자료관리 툴?, saas by atlassian cloud), bitbucket(형상관리 툴)와 연계 용이

Confluence와의 병용을 통해 기존의 엑셀, 파워포인트 등의 보고서 같은 것을 대체했다고 볼수있음, 소통 속에서 변질되거나 누락되는 정보를 최소화가능


# devops summary based on chap 7

## step1 confluence 와 Jira로 업무 관련 자료와 이슈 생성
프로젝트 참여자들이 같은 워크플로우 및 이슈 그리고 자료를 공유하면서 개발 운영

## step2 eclipse,AWS RDS, S3 스프링 프로젝트 개발
maven, spring(sts), rds&s3, tomcat

## step3 bitbucket의 develop branch에 push, pr 그리고 merge
여기서 바로 서버에 배포가능

## step4
### Jenkins를 통한 빌드와 배포

### (독립적으로)도커 이미지 생성 및 push and pull 그리고 배포
