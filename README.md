# R 강의 정리

## Lec02
1. R 패키지 및 설치
- 패키지란: 특정 분석을 수행할 수 있는 함수, 객체, 도움말, 데이터 등의 집합
  - R 설치시 기본 설치되는 패키지는 **library()** 함수로 조회
  - R 시작과 함께 **동시에 시작되는 기본 패키지**는 **search()** 함수로 조회
- R에서 기본 설치가 되지 않는 패키지는 사용자가 CRAN을 통해 직접 설치할 필요가 있다
  - **install.packages("pkg_name")** 과 같이 R 콘솔에서 직접 실행 가능 || 풀다운 메뉴의 패키지들 -> 패키지 설치하기를 클릭, 미러사이트에서 원하는 패키지를 찾아 설치하기도 OK
- 인스톨 후 **libary("pkg_name")** 으로 호출!
