# SQL
## 建表
```sql
CREATE TABLE student(
	name VARCHAR(20) NOT NULL,
	id CHAR(5) PRIMARY KEY,
	sex CHAR(1),
	age SMALLINT,
	teacherid CHAR(5),
	CONSTRAINT chk_stu_sex CHECK(sex = 'm' OR sex = 'f'),
	CONSTRAINT chk_stu_age CHECK(age < 150 AND age > 10),
	CONSTRAINT fk_id FOREIGN KEY (teacherid) REFERENCES advisor (id) ON DELETE SET NULL ON UPDATE CASCADE,
);
CREATE TABLE advisor(
	name VARCHAR(20) not null,
	id CHAR(5) PRIMARY KEY,
	sex CHAR(1),
	age SMALLINT,
	CONSTRAINT chk_stu_sex CHECK(sex = 'm' OR sex = 'f'),
	CONSTRAINT chk_stu_age CHECK(age < 150 AND age > 10),
);
```
