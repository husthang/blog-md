---
title: mysql笔记2
date: 2016-11-03 14:46:12
tags: [mysql]
description: mysql笔记2,数据完整性,多表查询,DQL复杂查询语句,mysql中的函数,数据库的备份与恢复
categories: JavaWeb
---

####  练习源码
+ [mysql练习代码2](ftp://123.206.232.76/resource/)

### 练习1:合并结果集
```sql
-- ------------联合查询------------------
create table A(
  name varchar(10),
  score int
);

create table B(
  name varchar(10),
  score int
);

  insert into A values('a',10),('b',20),('c',30);
insert into B values('a',10),('b',20),('d',40);
select * from A union select * from B;

-- union 被合并的两个结果,列数,列类型必须相同(名字可不同)
-- union all不去重复
```

### 练习2:定义表约束
```sql
-- 主键约束 primary key
-- 特点:主键数据唯一,且不能为null;每个表中要有一个主键

drop table student;
desc student;

-- 方法一
create table student(
  id int primary key,
  name varchar(50)
);
-- 方法二, 可以用来创建联合主键
create table student(
  id int,
  name varchar(50),
  primary key(id)
);
create table student(
  id int ,
  classId int,
  name varchar(50),
  primary key(id,classId)
);
-- 方法三
create table student(
  id int,
  name varchar(50)
);
alter table student add primary key(id);

-- 唯一约束 unique
-- 特点:数据不能重复
create table student(
  id int primary key,
  name varchar(50) unique
);

-- 自动增长列 auto_increment oracle (sequence)
create table student(
  id int primary key auto_increment,
  name varchar(50)
);
insert into student (name)values('Tom');

-- 域完整性
-- 限制字段的格式

-- 非空 not null
-- 默认值约束 default
drop table student;
create table student(
  id int primary key,
  name varchar(50) not null,
  gender varchar(10) default '男'
);

-- 引用完整性
-- 外键约束 foreign key
-- 联合查询
-- 学生表
CREATE TABLE student(
  stuid VARCHAR(10)PRIMARY KEY,
  stuname VARCHAR(50)
);
CREATE TABLE score(
  stuid VARCHAR(10),
  score INT,
  courseid INT,
  CONSTRAINT fk_stu_sco  FOREIGN KEY(stuid) REFERENCES student(stuid)
);



```

### 练习3:多表查询
```sql
-- 多表查询练习

CREATE TABLE emp(
  empno		INT,
  ename		VARCHAR(50),
  job		VARCHAR(50),
  mgr		INT,
  hiredate	DATE,
  sal		DECIMAL(7,2),-- 小数
  comm		DECIMAL(7,2),
  deptno		INT
) ;

INSERT INTO emp VALUES(7369,'SMITH','CLERK',7902,'1980-12-17',800,NULL,20);
INSERT INTO emp VALUES(7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30);
INSERT INTO emp VALUES(7521,'WARD','SALESMAN',7698,'1981-02-22',1250,500,30);
INSERT INTO emp VALUES(7566,'JONES','MANAGER',7839,'1981-04-02',2975,NULL,20);
INSERT INTO emp VALUES(7654,'MARTIN','SALESMAN',7698,'1981-09-28',1250,1400,30);
INSERT INTO emp VALUES(7698,'BLAKE','MANAGER',7839,'1981-05-01',2850,NULL,30);
INSERT INTO emp VALUES(7782,'CLARK','MANAGER',7839,'1981-06-09',2450,NULL,10);
INSERT INTO emp VALUES(7788,'SCOTT','ANALYST',7566,'1987-04-19',3000,NULL,20);
INSERT INTO emp VALUES(7839,'KING','PRESIDENT',NULL,'1981-11-17',5000,NULL,10);
INSERT INTO emp VALUES(7844,'TURNER','SALESMAN',7698,'1981-09-08',1500,0,30);
INSERT INTO emp VALUES(7876,'ADAMS','CLERK',7788,'1987-05-23',1100,NULL,20);
INSERT INTO emp VALUES(7900,'JAMES','CLERK',7698,'1981-12-03',950,NULL,30);
INSERT INTO emp VALUES(7902,'FORD','ANALYST',7566,'1981-12-03',3000,NULL,20);
INSERT INTO emp VALUES(7934,'MILLER','CLERK',7782,'1982-01-23',1300,NULL,10);
CREATE TABLE dept(
  deptno		INT,
  dname		VARCHAR(14),
  loc		VARCHAR(13)
);
INSERT INTO dept VALUES(10, 'ACCOUNTING', 'NEW YORK');
INSERT INTO dept VALUES(20, 'RESEARCH', 'DALLAS');
INSERT INTO dept VALUES(30, 'SALES', 'CHICAGO');
INSERT INTO dept VALUES(40, 'OPERATIONS', 'BOSTON');

-- 内连接 必须满足查询条件
select * from emp e inner join dept d on e.deptno=d.deptno;

insert into emp values(1014,'张三','保洁员',1009,'19991231',1000,500,50);

-- 外连接:查询的结果可能不满足条件
-- 左连接  先查询左表(以左为主),右表总满足条件的显示出来,不满足条件的显示null
-- 右连接  先查询右表(以右为主),右表中所有记录查询出来,左表总满足条件的显示出来,不满足条件的显示null
-- 左外连接
select * from emp left outer join dept on emp.deptno=dept.deptno;
-- 右外连接
select * from emp right outer join dept on emp.deptno=dept.deptno;

-- 自然连接
-- 两张连接的表中,名称和类型完全一致 会被自然连接找到
select * from emp natural join dept;
select * from emp natural left join dept;
select * from emp natural right join dept;

-- 子查询(重要)
-- 一个select语句中包含另一个完整的select语句
-- 练习一 工资高于JONES的员工
select * from emp where sal>(select sal from emp where ename='JONES');
-- 练习二 查询与SCOOT同一部门的员工 子查询结果为单行单列
select* from emp where deptno=(select deptno from emp where ename='SCOTT');
-- 练习三 工资高于30号部门所有人的员工信息 可使用all关键字
select * from emp where sal>(select max(sal) from emp where deptno=30);
select * from emp where sal>all(select sal from emp where deptno=30);
-- 练习四 查询工作和工资与MARTIN完全相同的员工信息 in 关键字使用
select * from emp where (job,sal)in (select job,sal from emp where ename='MARTIN');
-- 练习五 有两个以上直接下属的员工信息  (重要)
select * from emp where empno in(select mgr from emp group by mgr having count(mgr)>=2);
-- 练习六 查询编号为7788的员工名称,员工工资,部门名称,部门地址
select emp.ename,emp.sal,dept.dname,dept.loc from emp,dept where emp.deptno=dept.deptno and emp.empno=7788;
-- 练习七 求各个部门薪水最高的员工的所有信息
select * from emp where sal in (select max(sal) from emp group by deptno);-- 这样查是有问题的,没有加上部门约束
select * from emp where (sal,deptno) in (select max(sal),deptno from emp group by deptno);

```
