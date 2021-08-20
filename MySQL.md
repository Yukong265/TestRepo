<h2>MySQL</h2>

- MySQL의 구조![](C:\Users\user\Desktop\SQL 구조.PNG)
  1. Database(Schema) 안에 Table이 여러개 있을 수 있는 구조이다.
  2. 그런 데이터베이스들을 여러 개 가지고 있는 것을 DB Server라고 한다.

- MySQL의 구문

  1. Create

     - Create Database

       ```Create Database
       CREATE DATABASE 데이터베이스 이름;
       ```

     - Create Table

       ```Create table
       CREATE TABLE 테이블 이름 (
       	필드 이름1, 필드 타입1,
       	필드 이름2, 필드 타입2,
       	...
       );
       ```

     - 제약 조건

       ``` Constraints
       1. NOT NULL : 해당 필드는 NULL값을 넣을 수 없습니다.
       2. UNIQUE : 해당 필드는 서로 다른 값을 가져야만 합니다.
       3. PRIMARY KEY : 해당 필드가 NOT NULL과 UNIQUE 제약 조건의 특징을 모두 가지게 됩니다.
       4. FOREIGN KEY : 하나의 테이블을 다른 테이블에 의존하게 만듭니다.
       5. DEFAULT : 해당 필드의 기본 값을 설정합니다.
       6. AUTO_INCREMENT : 이 키워드를 사용하면 해당 필드의 값을 1부터 시작하여 새로운 레코드가 추가 될 때마다 1씩 증가된 값을 저장 합니다.('=' 사용시 시작 값 변경 가능) 
       ```

  2. Alter

     - Add

       ``` 
       ALTER TABLE 테이블 이름 ADD COLUMN 컬럼이름 varchar(32) NOT NULL;
       ```

     - Modify

       ```
       ALTER TABLE 테이블 이름 MODIFY COLUMN 컬럼이름 varchar(16) NULL;
       ```

     - Change 

       ```
       ALTER TABLE 테이블 이름 DROP COLUMN 컬럼이름 바꿀이름 varchar(16) NULL;
       ```

     - Drop

       ```
       ALTER TABLE 테이블 이름 DROP COLUMN 컬럼이름;
       ```

     - Rename

       ```
       ALTER TABLE 테이블 이름 RENAME 바꿀 이름;
       ```

  3. Insert

     1. ```
        INSERT INTO 테이블이름(필드이름1, 필드이름2, 필드이름3, ...) VALUES (데이터값1, 데이터값2, 데이터값3, ...)
        ```

     2.  ```
         INSERT INTO 테이블이름 VALUES (데이터값1, 데이터값2, 데이터값3, ...)
         ```

        - 2번째는 사용할 수 있는 필드가 제한적이다.
          1. NULL을 저장 할 수 있도록 설정된 필드
          2. DEFAULT 제약 조건이 설정된 필드
          3. AUTO_INCREMENT 키워드가 설정된 필드

  4. Update

     1.  ```
         UPDATE 테이블이름 SET 필드이름1=데이터값1, 필드이름2=데이터값2,... WHERE 필드이름=데이터값
         ```

  5. Delete

     1.  ```
         DELETE FROM 테이블이름 WHERE 필드이름=데이터값
         ```

        - 만약 WHERE 절을 생략하면 해당 테이블에 저장된 모든 데이터가 삭제됨

  6. Select

     1. ```
        SELECT 필드이름 FROM 테이블이름 [WHERE 조건]
        ```







