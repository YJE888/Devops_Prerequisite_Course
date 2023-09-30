# Database
### SQL
- 데이터는 테이블에 행과 열 형태로 저장되며, 데이터의 구조가 엄격하게 정의됨
- 정적이므로, 데이터의 구조가 변경되면 스키마 변경이 어렵고 번거로울 수 있음
- SQL 쿼리 언어를 사용하여 데이터에 접근하고 조작 (ex. SELECT * from persons where AGE > 10)
### NoSQL
- 주로 사용되는 모델에는 문서 (Document), 키-값 (Key-Value), 열 지향 (Column-family), 그래프 (Graph) 등이 있으며, 스키마가 유연하게 처리됨
- 데이터 모델을 유연하게 변경 가능
- 다양한 쿼리 언어 또는 API 사용 (ex. db.persons.find( { age: { $gt: 10 } } )

## MySQL
- 특징
  - 오픈 소스
  - 빠름
  - 신뢰성이 높음
  - SQL
- 설치
  ```
  $ yum install -y mysql
  ```
- 로그 확인
  ```
  $ cat /var/log/mysqld.log
  ```
- 접속
  - 처음 설치하면 위의 로그에서 root 패스워드를 확인할 수 있음
  ```
  $ mysql -u root -pPASSWORD
  ```
- 기본 패스워드 변경
  - `alter user~` 를 사용하는 것 보다 `mysql_secure_installation`을 사용하면 불필요한 사용자 및 테스트 데이터베이스등을 삭제, 원격 로그인 비활성화, root의 최소권한 부여로 *보안성이 강화*됨
  ```
  $ mysql_secure_installation
  ```
- 데이터 베이스 사용
  ```bash
  # 확인
  mysql> SHOW DATABASES;

  # 생성
  mysql> CREATE DATABASE school;

  # 데이터베이스 선택
  mysql> USE school;

  # 테이블 생성
  mysql> CREATE TABLE persons
  (
      Name varchr(255),
      Age int,
      Location varchr(255)
  );

  mysql> SHOW TABLES;

  # 테이블에 데이터 입력
  mysql> INSERT INTO persons values ("John Doe", 45, "New York");

  mysql> SELECT * FROM persons;
  ```
- 사용자 계정 생성
  - 보안 강화를 위해 root 계정이 아닌 사용자 계정 사용
  ```
  # user명 : john@localhost(username@host), password : MyNewPass4!
  # john은 locathost의 서버에서 접속 가능
  mysql> CREATE USER 'john'@'localhost' IDENTIFIED BY 'MyNewPass4!';

  # john이 192.168.1.10에서 접속하려면 host에 192.168.1.10 입력
  # john이 모든 노드에 접속하고 싶게 하려면 host에 % 입력
- 권한 설정
  - 권한(**PERMISSION**)의 종류
    - CREATE
    - DROP
    - DELETE
    - INSERT
    - SELECT
    - UPDATE
    - APP PRIVIEGES
  ```
  mysql> GRANT <PERMISSION> ON <DB.TABLE> TO 'john'@'%';
  # john에게 학교 DB의 사람 테이블에 SELECT 권한 허용
  mysql> GRANT SELECT ON school.persons TO 'john'@'%';

  # john에게 학교 DB의 모든 테이블에 SELECT와 UPDATE 권한 허용
  mysql> GRANT SELECT, UPDATE ON school.* TO 'john'@'%';

  # john에게 모든 DB의 모든 테이블에 모든 권한 허용
  mysql> GRANT ALL PRIVILEGES ON *.* TO 'john'@'%';

  mysql> SHOW GRANTS FOR 'john'@'localhost';
  ```

  ## MongoDB
  - 특징
    - Open source
    - NoSQL
    - 확장성
    - 고성능
    - 27017 포트에서 동작함
  - 설치
    - repo 추가 후 설치 가능
  - 서비스 시작
    ```bash
    $ systemctl start mongod
    $ systemctl status mongod
    ```
  - 로그 확인
    ```bash
    $ cat /var/log/mongodb/mongod.log
    ```
  - 설정 확인
    ```bash
    $ cat /etc/mongod.conf
    ```
  - 접속
    ```
    $ mongo
    ```
  - mongodb 사용
    ```
    # db 확인
    mongo> show dbs

    # db 생성과 db 스위치
    mongo> use school
    
    # 현재 사용 중인 db 확인
    mongo> db

    # persons이라는 콜렉션 생선(테이블과 유사한 단위)
    mongo> db.createCollection("persons")
    mongo> show collections
    
    # persons 콜렉션에 John Doe라는 문서 추가
    mongo> db.persons.insert({
            "name": "John Doe",
            "age": 45,
            "location": "New York",
            "salary": 5000
          })
    # persons 콜렉션에서 문서를 검색
    mongo> db.persons.find()

    # persons 콜렉션에서 나이가 30인 문서 검색
    mongo> db.persons.find({ age: 30})
    ```
    <img width="493" alt="image" src="https://github.com/YJE888/Devops_Prerequisite_Course/assets/75539276/0cbc5859-f606-4cdd-9284-7b01a037471e">
