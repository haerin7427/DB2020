# DB TEAM PROJECT

DB수업 데이터베이스 구축을 위한 python 코드들.

## Env.
 OS : ubuntu18.04.4LTS<br>
 mySQL : 5.7.30<br>
 python3

## Files


  db.py
  ```
  Dependencies: requests, bs4, pymysql
  
  한동대학교의 수업 정보를 추출해 mySQL에 추가한다.
  추출경로는 Hisnet - 개설강의정보 페이지에 적절한 파라미터를 post하여 결과를 crawling한다.
  우선 전공을 탐색 -> 각 전공 별 과목검색. 이때 보존하고있던 전공 코드를 과목의 fk로 사용한다.
  각 과목은 한 번만 저장하고, 과목별 분반을 저장할 때는 해당 과목의 course_id를 fk로 사용한다.
  위의 작업을 유저가 제공한 연도-학기 에 대해 반복한다.
  
  Functions
  
  get_lecture_list() -> 존재하는 전공과 그에 대한 수업들을 추출하고 저장
  get_kor_inj() -> 인정구분 목록 추출하여 저장
  
  init params : (('id','pw'),year)     #year format : 20201  == 2020년 1학기
  
  ```
  ![스크린샷 2020-05-10 오후 11 42 31](https://user-images.githubusercontent.com/47979730/81502274-fa3c2d00-9317-11ea-84b4-68168d3eaa51.png)
  
  
  eval.py
  ```
  Dependencies:  bs4, pymysql, selenium
  
  한동대학교 에브리타임의 강의평가를 추출해 mySQL에 추가한다.
  requests 대신에 selenium을 사용했으므로 사용 시 chrome_driver가 필요하다.
  모든 강의평가를 추출해 해당 과목명, 개설시기를 DB상에 있는 정보에 참조하여 FK로 사용한다.
  
  id,pw를 설정한뒤 실행
  ```
  
  csvreader.py
  ```
  Dependencies: csv, pymysql
  
  2020-1 이전에 제공된 예비수강 엑셀파일을 DB에 추가한다.
  과목코드를 DB의 course 테이블과 대조해 FK키로 쓸 course_id값을 추출해주는 역할을 한다.
  
  파일 이름을 설정하고 실행
  ```
## Todo
- csvreader.py 파일이름, 연도-학기 외부 파라미터로 받게 설정
- DB.py get_kor_inj, get_eng_inj 통일화

