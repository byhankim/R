# R 강의 정리

## Lec02
1. R 패키지 및 설치
- 패키지란: 특정 분석을 수행할 수 있는 함수, 객체, 도움말, 데이터 등의 집합
  - R 설치시 기본 설치되는 패키지는 **library()** 함수로 조회
  - R 시작과 함께 **동시에 시작되는 기본 패키지**는 **search()** 함수로 조회
- R에서 기본 설치가 되지 않는 패키지는 사용자가 CRAN을 통해 직접 설치할 필요가 있다
  - **install.packages("pkg_name")** 과 같이 R 콘솔에서 직접 실행 가능 || 풀다운 메뉴의 패키지들 -> 패키지 설치하기를 클릭, 미러사이트에서 원하는 패키지를 찾아 설치하기도 OK
- 인스톨 후 **libary("pkg_name")** 으로 호출!

2. R 패키지의 활성화
- 사용자가 직접 설치한 패키지의 경우, **install.packages("rpart")** 후에 꼭 **library("rpart")** 명령어를 실행하여 패키지를 _활성화_ 해주어야 한다!
``` sh
install.packages("rpart")
library("rpart")
help(package="rpart")   # 웹 기반 패키지 설명서
library(help="rpart")   # 텍스트 기반 패키지 설명서
```
**설치 에러날시 관리자 권한으로 실행**   
- R 콘솔에서 data(package="패키지명") 명령문 사용시 저장되어있는 데이터의 목록 출력. data(데이터명, package="패키지명") 명령문을 통해 패키지 내부에 저장된 데이터를 불러오는 것도 가능

3. R Studio
- IDE(Integrated Development Environment)
  - IDE란 기본적으로 편집기, 컴파일러, 프로그램 디버깅, GUI 등 여러 애플리케이션 패키지를 묶어 한 프로그램 안에 구현한 프로그래밍 환경을 의미
  - 데이터 관리, 문서 및 프리젠테이션 자료 편집, HTML 작업 등 다양한 추가 기능들을 활용할 수 있음
- 편집기 / 작업공간(Workspace) / 작업이력(history) / R 콘솔 / 그래프(plots) / 패키지 / 도움말 등으로 구성

4. R Studio 사용하기
- new script에서 작업한 후 실행 코드 블락 드래그한 후 Run 버튼 클릭 혹은 Ctrl+Enter
- 풀다운 메뉴에서 File - Import Dataset 혹은 Environment 탭 안의 Import Dataset 버튼을 눌러 여러 형태의 데이터를 읽을 수 있다

5. R의 기타 기능
- 구글, 스택 오버플로우, DataCamp.com의 Quick-R 사이트(www.statmethods.net)에서 R, 통계, 그래프 그리기에 대한 튜토리얼 및 도움말 풍부
- R의 최신 패키지들은 The R Journal, Journal of Statistical Software 등과 같은 무료 저널을 통해 받을 수 있다.
