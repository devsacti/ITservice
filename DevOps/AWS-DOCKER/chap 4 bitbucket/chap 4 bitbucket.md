# 형상관리의 역할과 bitbucket활용
대표적인 형상관리 시스템 => 운영서버와 개발서버 독립, 그리고 운영용 소스(main or master)와 개발용 소스(develop) 분리
 
추가로 브랜치 전략 으로서
프로젝트 소스의 기능별로 브랜치를 만들고(일종의 도메인일듯) 이에 대해 개발자들의 컴퓨터가 접근

bitbucket은 이러한 형상관리 환경을 제공가능
같은 환경으로는 github, gitlab 등

# bitbucket 기능
eclipse git repository를 연동해서 git share

# 실습 1 bitbucket으로 형상관리 환경 만들기 및 연동

## 1. bitbucket에 repo를 만든다_ 최종목적지

이걸 하면 clone이라는 깃링크가 생성된다. 이를 통해서 이클립스와 연동

## 2. local_내 노트북_에 bitbucket repo와 연동할 local git 공간 만들기_ 중간 경유지

이클립스 windows의 show view 탭에서 Git 항목 들어가서 Git Repositories 클릭, 새로 생긴 창에서 clone a Git repository 또는 원통도형에 초록색 화살표가 우리가 찾는 것이다.

별도의 설정없이 일단 다 next하다가 finish하면된다.
참고로 이 과정에서 로컬경로를 설정_C:\Users\schiz\git_

## 프로젝트에서, local git, bitbucket repo로 
## 3. 최초 출발지인 프로젝트의 위치와 local git 연결하기
 해당프로젝트 우클릭, Team 탭, Share project 탭 클릭하고, 
'우선 '도착할 곳은 2번 스텝에서 만든 내 컴퓨터 내 빗버킷 깃위치로 잡는다.
여기가 일종의 빗버킷과 연락할 지정장소, 이때 기본값으로 설정하면 안된다.

이 다음부터는 Team 탭으로 들어가면 Share project대신 다른 것들이 뜨고, 그중 syncronize를 통해 local git과 repo 연결 제어

!! 위 작업을 통해 d 드라이브의 프로젝트가 c드라이브이 로컬 깃 위치로 이동된다. 이로인해 인덱스가 원활히 작동안한듯했는데
sts를 껐다 키니 정상됨

## 4. from local git to master of repo of bitbucket
synchronyze workspace 클릭 참고로 아직 올라간건 아니라고 한다. 
그 다음 자동으로 뜬 synchronize 탭에서 review 프로젝트를 우클릭하여 add to index를 한다.
원론적인 관리 및 처리를 위한 인덱싱으로 보인다. 서버 업로드 전에 그 다음 commits를 클릭

그러면 Git Staging 탭에 unstaged와 staged가 나뉘는데, 후자가 인덱스된 애들이라고한다.
아마도 새로운 파일과 그렇지 않은 것을 구분하는 것으로 보인다.

그리고 업로드를 하면서 개발자의 코멘트_aidsfintech@gmail.com_를 commit message에 남긴다고한다.

이때 비밀번호를 입력해야하는데 이것은 bitbucket repo의 주인계정정보_devsacti@gmail.com_이다.


# 실습 2 브랜치 생성, 관리

## 1. 브랜치 생성 at bitbucket repo and local git
### bitbucket
현재 브랜치(운영서버 격) 외 추가 브랜치 생성(개발서버), 마스터 아래 디벨럽 가지를 만든다고 한다. 그냥하위라는 큰 개념인듯
빗버킷 상에서 branches 탭 들어가서 마스터 브랜치 하위에 type은 other의 develop을 만든다.

### local git by eclipse
 상응하여 Git Repositories 탭을 클릭하여 내 로컬 깃에도 Branches를 우클릭하여 switch to의 new branch를 통해서 develop을 만든다.

## 2. from develop of local git to develop of repo
프로젝트 우클릭, Team, remote, configure fetch from Upstream 들어가면 ref mapping이란 해괴한 경로가 나온다. 참고로 ref는 reference로 보인다.

이러한 경로를 수정하기위해 경로 선택 후 modify 클릭해봤다가 영상에서 급히 advanced로 들어감. 거기서 Sourcd ref 에서 develop을 선택 후 add spec 클릭 후

이때 기존 경로는 이전꺼라 지우면 됨. 그러면 다시금 해괴한 경로가 비교적 명확해짐_ 로컬 develop깃폴더 : 빗버킷 대응장소

커밋을 위해선 '변동사항'이 있어야하므로, ReviewApplication.java에 주석 추가하면 자동으로 unstaged에 추가되고 인덱스추가후 commit and push

**그동안 commit클릭 시 자동으로 된 것이지, pycharm에서도 초기 프로그램말고는, Add 해준다음 commit가능함**

## 3 develop의 변화를 master에 반영, pull request, pr을 날린다!
### 빗버킷의 pull requests 탭 클릭, create a pull request 클릭 후, 일단은 별다른 설정 무
참고로, close branch 탭이란 개발 브랜치가 1회성인 경우 한번 합친 후 하위 가지가 사라진다고 한다. 

실행한 뒤, 추가된 내용과 사라진 내용을 볼수있다. 다만 아직 Merge를 안눌렀기 때문에 변동사항 만 파악한 것이 전부다.

### 최종권한자_devsacti@gmail.com_가 새로운 pr을 만들고 Merge 버튼을 클릭함으로써 변동사항이 반영
참고로 구글웹브라우져 2개 쓰다보면, 계정전환이랑 웹브라우져 새 창 전환에 언제나 바로 대응하지 않는듯하다.
즉, aidsfintech에서 devsacti로 계정 전환을 했지만, pr 권한이 없다고 떠서 애먹었는데,
그냥 로그아웃하고 다시 새창열고 접속하니 해결됨
