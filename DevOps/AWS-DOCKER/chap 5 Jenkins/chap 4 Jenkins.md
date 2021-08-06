# 젠킨스
대표적인 ci_Continuous Integration_툴
 
기본적인 배포부터 코딩규약준수여부 확인

직접 서버 1개1개 접속해서 배포하지 않고,

젠킨스를 통해 표준컴파일,빌드테스트&코딩규약 준수 체크, 젠킨스 프로젝트 세팅(git에서 가져오기),배포 및 파이프라인 작업, 소스 변경 시 성능변화 감시, 다시 순환

!!bitbucket도 파이프라인 설정 및 배포 가능하나 젠킨스를 쓰는이유 !! 자동화테스트 제공
https://ksy93.tistory.com/entry/Jira-Bitbucket-Jenkins


# 설치방법
 사내 서버에 설치_특히 도커를 통해서
 로컬 호스트에 설치_ 우리 실습내용

## 실습 1
일단 그냥 내 노트북에 설치하는 과정이고 설치방법은 젠킨스 홈페이지에서
윈도우 버전을 다운받는것이다.

다만 귀찮은 것은 
C:\Windows\system32\config\systemprofile\AppData\Local\Jenkins\.jenkins\secrets\initialAdminPassword
가서 내용물을 봐야하는데 vi도 안되고 여차저차 관리자 권한으로 직접 폴더 하나씩들어가서
notepad로 읽음.

## 실습 1 젠킨스 설정과 java, mvn, git(bitbucket) 연동=>위 작업을 위한 기본세팅
1. plugin 설치
 원래라면 자동설치 되야하는데, 원인 불명으로 설치가 안되고, 수동설치 사이트도 적절하지 않다가
'젠킨스 (다운로드 실패 api 복붙)' 하니까 신뢰할만한 젠킨스 플러그인 자료를 다운로드 받을 수 있게됨.

uri로는
https://plugins.jenkins.io/(해당플러그인명)/#releases
인줄 알았으나, 스페이스 바의 경우 uri 상에서 -로 치환되기 때문에 그냥 구글에서

jenkins (해당플러그인 명)

방식으로 전환

이후 내 컴퓨터의 경로에 일부 + jenkins/plugins 디렉토리 아래에 배치하면됨

2. jdk 설정
jenkins 관리 탭에서 global tool configuration 클릭, jdk 설정
 제일 무난한 8버전 중 최신으로 클릭하고
오라클 접근을 위해
내 오라클 계정 정보를 미리 기입해둔다.

3. Git 설정
우선 로컬인 내 노트북에 git이 설치되어있어야함, 나는 이전에 깜

!!! git 위치 경로 찾기
윈도우 powershell에서 왠만한 리눅스 명령어도 지원하는데,
분명 윈도우로서 find, which 안먹고 
dir git
으로 해야 git 폴더 위치 경로 찾을 수 있음

이것도 경로에 넣고 화면 맨아래 save 클릭

4. 새로운 아이템 형성_ 젠킨스는 아이템이 단위인가봄
ppt와 영상대로 따라서 설정하는데
여기서 소스 코드 관리 탭에서 jdk 자동설치 때와 마찬가지로
나의 빗버킷 url을 기입하고,
 '빗버켓 접속을 위해 빗버킷 접속 아이디와 비번, 이메일로 구성된' credential을 생성하여 선택해야한다.

그 다음 build 탭에서 
invok top level maven target 선택
goals 에는 package

저장한다음 build now

1try- oracle 아뒤 비번 틀림
2try- 수업 영상대로 로컬 폴더의 권한을 변경해줘야함. 터미널로


--실습 2 ; 젠킨스 배폰
1. publish over ssh란 플러그 추가 설치

2. 시스템 설정에서 ssh 사용을 위한 키랑 경로를 세팅, 
 실제로 서버 1개1개 접속해서 배포하듯이, 이에 대응하여
 해당 ip로 접근 후 보안절차를 거치고, 해당 톰캣폴더로 접근해야하니까.
 이러한 세팅 후 젠킨스가 빗버킷에서 프로젝트 코드를 전달받아 우선 war를 만드는것으로 보이고, 그 다음 이를 서버에 전달
