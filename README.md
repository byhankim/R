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
- new script(메뉴창에서 열거나 Ctrl + Shift + N) 에서 작업한 후 실행 코드 블락 드래그한 후 Run 버튼 클릭 혹은 Ctrl+Enter
- setwd(): More에서 현재 워킹 디렉토리 변경 가능
- Tools -> Global Options : 전체 글꼴, 색 등 테마 변경 가능
- 직접 데이터 가져오기 : 풀다운 메뉴에서 File - Import Dataset 혹은 Environment 탭 안의 Import Dataset 버튼을 눌러 여러 형태의 데이터를 읽을 수 있다

5. R의 기타 기능
- 구글, 스택 오버플로우, DataCamp.com의 Quick-R 사이트(www.statmethods.net) 에서 R, 통계, 그래프 그리기에 대한 튜토리얼 및 도움말 풍부
- R의 최신 패키지들은 The R Journal, Journal of Statistical Software 등과 같은 무료 저널을 통해 받을 수 있다.

## Lec03_데이터 입력과 저장
1. 데이터 입력
- R 활용 작업시 작업 디렉토리 변경 필요
  - 기본 작업경로가 길거나 복잡할 경우 경로를 일일히 설정/찾아내는 것이 번거로우므로 작업디렉토리를 변경
    ```sh
    setwd('D:\\datav')    // backslash: used with escape character
    // 현 작업 디렉토리 확인은 getwd() 함수를 사용하면 된다.
    ```
  - c()함수를 이용한 입력
    - c() 함수는 가장 기본적인 데이터 입력 방법
      - 좌측에 벡터 이름(객체명), <- 나 = 연산자는 데이터가 할당됨 의미
      - 우측은 입력대상인 데이터의 관측값이 c 함수 내에 나타나게 됨
      ```sh
      ex) 1,2,3,4,5 다섯 개의 관측값을 갖는 벡터 x 생성
      > x <- c(1,2,3,4,5)
      > x
      [1] 1 2 3 4 5

      ex) 괄호로 생성문 전체를 감싸 10, 20, 30, 40, 50 다섯 개의 관측값을 갖는 벡터 y를 생성하되 입력결과를 바로 화면에 출력
      > (y <- c(10,20,30,40,50))
      [1] 10 20 30 40 50
      ```
    - cbind() 함수를 사용한 동일 길이의 두 벡터 결합
      ```sh
      > x<-c(1,2,3,4,5)
      > y<-c(10,20,30,40,50)
      > dat<-cbind(x,y)
      > dat
      x y       // 행렬구조
      [1,] 1 10
      [2,] 2 20
      [3,] 3 30
      [4,] 4 40
      [5,] 5 50
      ```
    - scan함수를 활용하여 바로 데이터 입력
      - 함수 실행시 실행 prompt가 "1:"로 바뀌는데, 이때 자료를 하나씩 입력하고 Enter 키를 치면 다음 값을 입력할 수 있다.
      ```sh
      > w1 <- scan()
      1: 23
      2: 4
      3: 5
      4: 6
      5: 7
      6:
      Read 5 items
      > w1
      [1] 23 4 5 6 7
      ```
    - edit 함수를 이용하여 데이터 엑셀과 비슷한 입력창(데이터프레임 자료구조)이 생성됨
      - 하지만 성능이 구려서 잘은 안쓰고 보통 외부 엑셀 등 파일들을 불러온다
      ```sh
      > dat<-data.frame()   // dataframe이 입력될 빈 공간 생성
      > dat3 = edit(dat3)
      // 자료 입력
      > dat3
      // 행렬 출력
      ```

2. 데이터 저장(R 기준에서 외부 출력과 같은 의미)
- sink 함수를 활용하여 화면에 출력된 모든 결과를 파일로 저장할 수 있다
  - 시작시 저장할 파일명을 지정하고 원하는 함수를 실행한 뒤 종료시 sink()로 마감
  ```sh
  // sink()로 여닫기
  > sink('printa.txt')  // 작업디렉토리에 해당 파일이 생성된다
  > summary(iris)       // summary: 중간값, 25%, 75%, 평균 등 기술통계량 계산 함수 | iris: R 내부데이터로 꽃 품종별 데이터이다.
  > sink()
  ```
- write.csv() 함수를 이용한 데이터 저장
  - R에서 생성된 객체(obj)는 외부파일로 저장할 수 있다.
  - 다르경로가 지정되어있지 않다면 이 파일은 기존 워킹 디렉토리에 저장된다.
  ```sh
  # csv 파일: Comma Separated Value로 ','로 각 데이터가 구분된다. txt형태로 되어있다.
  > write.csv(dat, 'dat_exam1.csv')  // 데이터 이름, (경로 + )파일명 설정 가능. 경로명 없을시 현 wd에 저장됨
  ```
- write.table() 함수를 이용한 데이터 저장
  - write.table()함수는 comma로 구분하지 않고 기본 구분자를 공백으로 설정한다.
  - 공백 대신 sep="문자" 옵션을 세번째 인자로 줄 수 있다.
  ```write.table(dat, 'dat_exam2.txt', sep=",")

3. 데이터 불러오기
- read.csv() 함수를 이용하여 간단하게 불러올 수 있다.
  ```sh
  ** 외부데이터를 불러올땐 새로운 객체에 넣어줘야 호출할 수 있다.
  ** 만약 불러오는 데이터가 comma separated가 아니면 모두 하나의 변수로 취급하니 주의!
  > dat2 <- read.csv("dat_exam1.csv")
  ** 변수명 (i.e. x y)이 들어가는 데이터면서 comma separated 라면 header=T 옵션을 주어야 한다
  > us_dat<-read.csv("USArrestd.csv", header=T)
  > head(us_dat)
  ```
- 불러온 자료의 자료구조를 확인하려면 str() 함수 사용
  ```sh
  > str(us_dat)
  'data.frame': 50 obs. of 5 variables:
  $ State: Factor w/ 50 levels "Alabama", "Alaska"...: 1 2 3 4 5 6 7 8 9 10 ...
  // State 변수가 자동으로 Factor 변수로 변환되는데, 이를 방지하려면 stringAsFactors=F" 옵션 추가하여 문자로 인식
  ```
- 문자변수가 Factor 변수로 인식되지 않도록 지정
  ```sh
  > us_dat2 < read.csv("USArrestd.csv", header=T, stringAsFactor=F)
  > str(us_dat2)
  'data.frame': 50 obs. of 5 variables:
  $ State: chr "Alabama" "Alaska" "Arizona" "Arkansas" ...
  ```
- read.table() 함수를 이용한 데이터 로드
  - 텍스트 파일은 read.csv() 외에도 read.table()을 사용하여 불러올 수 있음
  - 현 wd에 저장된 data_exam2.txt 파일을 read.table() 을 사용하여 불러오기
    ```sh
    ** header 옵션 지정여부에 따라 맨 첫줄 관측치를 변수명으로 인식하는지를 결정한다.
    > new_dat = read.table('dat_exam2.txt', header=T)
    ```
- R에서는 결측치가 NA 로 표시되나, 데이터를 읽어오면서 na.strings 와 같은 옵션을 지정해주면 특정 문자를 결측치로 인식한다
  - 이전에 작업한 객체 dat3이 현 wd에 dat3_exam1.txt라는 이름으로 저장되어 있다고 할 때, 관측값 'aa'를 결측치로 인식하여 데이터 로드하기
    ```sh
    ** 마찬가지로 header 옵션 지정여부가 첫째줄 관측치를 변수명으로 인식하는지를 결정.
    > nadat <- read.table('dat3_exam1.txt', na.strings='aa', header=T)
    ```

4. 객체(object) 확인 및 삭제
- ls() 함수: 현재까지의 작업 중 만들어진 object를 전부 확인할 수 있다
  - 동일한 변수를 계속 쓸 경우 지속적으로 덮어쓰기된다.
- rm(list=ls()) : 지금까지 만든 모든 객체를 한번에 삭제한다.
