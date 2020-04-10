# mysql-final-test

2019-2020 mysql final test

姓名：王逸健

学号：17061524

说明1：考试为开卷，可以上网，自觉不要相互电话和QQ；

说明2：考试时间为：2020 年 4 月 10 日 8:10分-9:40分。

说明3：试题比较多，抓紧时间，超时提交的github commit不被接受。未避免完全超时提交，可以在做题过程中多 commit 几次。

说明4：结束后发邮件给 42225@hdu.edu.cn 标题为“MySQL期末考试,姓名+学号”，内容为github链接。


1 打印当前时间（例如 2020-04-07 13:41:42），写出SQL语句和结果
```sql
mysql> create table time(
    -> datetime DATETIME);
Query OK, 0 rows affected (0.04 sec)

mysql> select now();
+---------------------+
| now()               |
+---------------------+
| 2020-04-10 08:01:45 |
+---------------------+
1 row in set (0.00 sec)
```
2 组合打印自己的姓名和学号
```sql
mysql> create table me(
    -> name VARCHAR(20),
    -> id INT);
Query OK, 0 rows affected (0.05 sec)

mysql> select CONCAT('王逸健','+','17061524');
+---------------------------------+
| CONCAT('王逸健','+','17061524') |
+---------------------------------+
| 王逸健+17061524                 |
+---------------------------------+
1 row in set (0.01 sec)
```
(例如 张三+123456 或者 zhangsan+123456 显示需包含加号)，写出SQL语句和结果

3 建立如下表1和表2，写出建表语句和插入语句。

表1：其中deptno为主键
```
deptno, deptno,    loc
(10, "ACCOUNTING", "NEW YORK"),
(20, "RESEARCH", "DALLAS"),
(30, "SALES", "CHICAGO"),
(40, "OPERATIONS", "BOSTON")
```

```sql
mysql> create table t_table1(
    -> deptno INT PRIMARY KEY,
    -> dname VARCHAR(20),
    -> loc VARCHAR(20)
    -> );
Query OK, 0 rows affected (0.05 sec)

mysql> desc t_table1;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| deptno | int(11)     | NO   | PRI | NULL    |       |
| dname  | varchar(20) | YES  |     | NULL    |       |
| loc    | varchar(20) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql> INSERT INTO t_table1
    -> VALUES(10, "ACCOUNTING", "NEW YORK"),
    -> (20, "RESEARCH", "DALLAS"),
    -> (30, "SALES", "CHICAGO"),
    -> (40, "OPERATIONS", "BOSTON");
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM t_table1;
+--------+------------+----------+
| deptno | dname      | loc      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
4 rows in set (0.00 sec)
```
表2：其中empno字段为主键
```
        empno, ename,    job,    MGR,   Hiredate,    sal,   comm, deptno
        (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
	(7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
	(7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
	(7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
	(7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
	(7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
	(7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
	(7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
	(7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
	(7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
	(7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
```

```SQL
mysql> CREATE TABLE t_table2(
    -> empno INT PRIMARY KEY,
    -> ename VARCHAR(20),
    -> job VARCHAR(20),
    -> MGR INT,
    -> Hiredate Date,
    -> sal float,
    -> comm float,
    -> deptno INT NOT NULL
    -> );
Query OK, 0 rows affected (0.06 sec)

mysql> INSERT INTO t_table2
    -> VALUES(7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
    -> (7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
    -> (7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
    -> (7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
    -> (7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
    -> (7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
    -> (7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
    -> (7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
    -> (7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
    -> (7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
    -> (7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10);
Query OK, 13 rows affected (0.00 sec)
Records: 13  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM t_table2;
+-------+--------+-----------+------+------------+------+------+--------+
| empno | ename  | job       | MGR  | Hiredate   | sal  | comm | deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|  7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
13 rows in set (0.00 sec)
```
3.1 表2 中再插入一条记录：

`(你的学号，你的姓名或者拼音， “CLERK”, 7782, 你的生日,  NULL, NULL, 10)`
 
例如：`(12345,  "Zhangsan", "sTUDENT", 7782, "2000-03-12", NULL, NULL, 10)`
```sql
mysql> INSERT INTO t_table2
    -> VALUES(17061524,"WangYijian","stduent",7788,"1999-04-23",NULL,NULL,10);
Query OK, 1 row affected (0.01 sec)

mysql> SELECT*FROM t_table2;
+----------+------------+-----------+------+------------+------+------+--------+
| empno    | ename      | job       | MGR  | Hiredate   | sal  | comm | deptno |
+----------+------------+-----------+------+------------+------+------+--------+
|     7369 | SMITH      | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|     7499 | ALLEN      | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|     7521 | WARD       | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|     7566 | JONES      | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|     7654 | MARTIN     | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|     7698 | BLAKE      | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|     7788 | SCOTT      | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7839 | KING       | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|     7844 | TURNER     | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|     7878 | ADAMS      | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|     7900 | JAMES      | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|     7902 | FORD       | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7934 | MILLER     | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
| 17061524 | WangYijian | stduent   | 7788 | 1999-04-23 | NULL | NULL |     10 |
+----------+------------+-----------+------+------------+------+------+--------+
14 rows in set (0.00 sec)
```
3.2 表中入职时间（Hiredate字段）最短的人。
```sql
mysql> SELECT * FROM t_table2 WHERE Hiredate = (SELECT MAX(Hiredate) FROM t_table2);
+----------+------------+---------+------+------------+------+------+--------+
| empno    | ename      | job     | MGR  | Hiredate   | sal  | comm | deptno |
+----------+------------+---------+------+------------+------+------+--------+
| 17061524 | WangYijian | stduent | 7788 | 1999-04-23 | NULL | NULL |     10 |
+----------+------------+---------+------+------------+------+------+--------+
1 row in set (0.00 sec)
```
**入职时间最短的人为WangYijian。**

3.3 有几种职位（job字段）？在关系代数中，本操作是什么运算？
```sql
mysql> select distinct job
    -> from t_table2;
+-----------+
| job       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
| stduent   |
+-----------+
6 rows in set (0.00 sec)

mysql> select found_rows();
+--------------+
| found_rows() |
+--------------+
|            6 |
+--------------+
1 row in set (0.01 sec)
```
**job字段中有6个职位
在关系代数中，本操作是 选择运算**

3.4 将 MILLER 的 comm 增加 100； 然后，找到 comm 比 MILLER 低的人；
```sql
mysql> select ename from t_table2 WHERE sal>(
    -> select sal+100 from t_table2 WHERE ename='MILLER');
+--------+
| ename  |
+--------+
| ALLEN  |
| JONES  |
| BLAKE  |
| SCOTT  |
| KING   |
| TURNER |
| FORD   |
+--------+
7 rows in set (0.01 sec)

mysql> select * from t_table2 WHERE sal>(
    -> select sal+100 from t_table2 WHERE ename='MILLER');
+-------+--------+-----------+------+------------+------+------+--------+
| empno | ename  | job       | MGR  | Hiredate   | sal  | comm | deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
+-------+--------+-----------+------+------------+------+------+--------+
7 rows in set (0.00 sec)
```
3.5 计算每个人的收入(ename, sal + comm)；计算总共有多少人；计算所有人的平均收入。 提示：计算时 NULL 要当做 0 处理； 
```sql
mysql> select ename,sal+comm from t_table2;
+------------+----------+
| ename      | sal+comm |
+------------+----------+
| SMITH      |     NULL |
| ALLEN      |     1900 |
| WARD       |     1750 |
| JONES      |     NULL |
| MARTIN     |     2650 |
| BLAKE      |     NULL |
| SCOTT      |     NULL |
| KING       |     NULL |
| TURNER     |     1500 |
| ADAMS      |     NULL |
| JAMES      |     NULL |
| FORD       |     NULL |
| MILLER     |     1400 |
| WangYijian |     NULL |
+------------+----------+
14 rows in set (0.00 sec)

mysql>  select found_rows();
+--------------+
| found_rows() |
+--------------+
|           14 |
+--------------+
1 row in set (0.00 sec)

mysql> select ename,sal+comm,count(ename) counts,AVG(sal+comm) average_sal_comm from t_table2;
+-------+-------------+--------+---------------------+
| ename |  sal+comm   | counts | average_salary_comm |
+-------+-------------+--------+---------------------+
| SMITH |        NULL |     14 |                1840 |
+-------+-------------+--------+---------------------+
1 row in set (0.00 sec)

mysql> select ename,coalesce(sal+comm,0),count(ename),coalesce(AVG(sal+comm),0) from t_table2;
+-------+-------------------------+--------------+------------------------------+
| ename |   coalesce(sal+comm,0)  | count(ename) |   coalesce(AVG(sal+comm),0)  |
+-------+-------------------------+--------------+------------------------------+
| SMITH |                       0 |           14 |                         1840 |
+-------+-------------------------+--------------+------------------------------+
1 row in set (0.00 sec)
```
3.6 显示每个人的下属, 没有下属的显示 NULL。本操作使用关系代数中哪几种运算？
```sql
mysql> select t1.ename My_b_b_name,t2.ename My_b_name ,t3.ename My_name
    -> from (t_table2 t1 inner join t_table2 t2 on t1. empno= t2. mgr)  inner join t_table2 t3
    ->  on t2.empno = t3.mgr;
+-------------+-----------+------------+
| My_b_b_name | My_b_name | My_name    |
+-------------+-----------+------------+
| JONES       | FORD      | SMITH      |
| KING        | BLAKE     | ALLEN      |
| KING        | BLAKE     | WARD       |
| KING        | BLAKE     | MARTIN     |
| KING        | JONES     | SCOTT      |
| JONES       | SCOTT     | ADAMS      |
| KING        | BLAKE     | JAMES      |
| KING        | JONES     | FORD       |
| JONES       | SCOTT     | WangYijian |
+-------------+-----------+------------+
9 rows in set (0.01 sec)
```
3.7 建立一个视图：每个人的empno, ename, job 和 loc。简述为什么要建立本视图。
```sql
mysql> select * from t_table1 t1 inner join t_table2 t2 on t1.deptno=t2.deptno;
+--------+------------+----------+----------+------------+-----------+------+------------+--------+------+--------+
| deptno | dname      | loc      | empno    | ename      | job       | MGR  | Hiredate   | salary | comm | deptno |
+--------+------------+----------+----------+------------+-----------+------+------------+--------+------+--------+
|     20 | RESEARCH   | DALLAS   |     7369 | SMITH      | CLERK     | 7902 | 1981-03-12 |    800 | NULL |     20 |
|     30 | SALES      | CHICAGO  |     7499 | ALLEN      | SALESMAN  | 7698 | 1982-03-12 |   1600 |  300 |     30 |
|     30 | SALES      | CHICAGO  |     7521 | WARD       | SALESMAN  | 7698 | 1838-03-12 |   1250 |  500 |     30 |
|     20 | RESEARCH   | DALLAS   |     7566 | JONES      | MANAGER   | 7839 | 1981-03-12 |   2975 | NULL |     20 |
|     30 | SALES      | CHICAGO  |     7654 | MARTIN     | SALESMAN  | 7698 | 1981-01-12 |   1250 | 1400 |     30 |
|     10 | ACCOUNTING | NEW YORK |     7698 | BLAKE      | MANAGER   | 7839 | 1985-03-12 |   2450 | NULL |     10 |
|     20 | RESEARCH   | DALLAS   |     7788 | SCOTT      | ANALYST   | 7566 | 1981-03-12 |   3000 | NULL |     20 |
|     10 | ACCOUNTING | NEW YORK |     7839 | KING       | PRESIDENT | NULL | 1981-03-12 |   5000 | NULL |     10 |
|     30 | SALES      | CHICAGO  |     7844 | TURNER     | SALESMAN  | 7689 | 1981-03-12 |   1500 |    0 |     30 |
|     20 | RESEARCH   | DALLAS   |     7878 | ADAMS      | CLERK     | 7788 | 1981-03-12 |   1100 | NULL |     20 |
|     30 | SALES      | CHICAGO  |     7900 | JAMES      | CLERK     | 7698 | 1981-03-12 |    950 | NULL |     30 |
|     20 | RESEARCH   | DALLAS   |     7902 | FORD       | ANALYST   | 7566 | 1981-03-12 |   3000 | NULL |     20 |
|     10 | ACCOUNTING | NEW YORK |     7934 | MILLER     | CLERK     | 7782 | 1981-03-12 |   1300 |  100 |     10 |
|     10 | ACCOUNTING | NEW YORK | 17061524 | WangYijian | stduent   | 7788 | 1999-04-23 |   NULL | NULL |     10 |
+--------+------------+----------+----------+------------+-----------+------+------------+--------+------+--------+
14 rows in set (0.01 sec)

mysql> select empno,ename,job,loc from t_table1 t1 inner join t_table2 t2 on t1.deptno=t2.deptno;
+----------+------------+-----------+----------+
| empno    | ename      | job       | loc      |
+----------+------------+-----------+----------+
|     7369 | SMITH      | CLERK     | DALLAS   |
|     7499 | ALLEN      | SALESMAN  | CHICAGO  |
|     7521 | WARD       | SALESMAN  | CHICAGO  |
|     7566 | JONES      | MANAGER   | DALLAS   |
|     7654 | MARTIN     | SALESMAN  | CHICAGO  |
|     7698 | BLAKE      | MANAGER   | NEW YORK |
|     7788 | SCOTT      | ANALYST   | DALLAS   |
|     7839 | KING       | PRESIDENT | NEW YORK |
|     7844 | TURNER     | SALESMAN  | CHICAGO  |
|     7878 | ADAMS      | CLERK     | DALLAS   |
|     7900 | JAMES      | CLERK     | CHICAGO  |
|     7902 | FORD       | ANALYST   | DALLAS   |
|     7934 | MILLER     | CLERK     | NEW YORK |
| 17061524 | WangYijian | stduent   | NEW YORK |
+----------+------------+-----------+----------+
14 rows in set (0.00 sec)
```
**建立视图的目的：为了提高复杂SQL语句的复用性和表操作的安全性,MySQL数据库管理系统提供了视图特性。视图并不在数据库中以存储的数据值形式存在。行和列数据来自定义视图的查询所引用基本表，并且在具体引用视图时动态生成。视图使程序员只关心感兴趣的某些特定数据和他们所负责的特定任务。这样程序员只能看到视图中所定义的数据，而不是视图所引用表中的数据，从而提高了数据库中数据的安全性。**

3.8 为表2增加一个约束：deptno字段需要在表1中存在；这称做什么完整性？
```SQL

```
`
这是实体完整性
`

3.9 为表2增加一个索引：ename 字段。简述为什么要在 ename 字段建立索引
```sql
mysql> CREATE INDEX index_ename
    -> ON t_table2 (ename);
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SHOW CREATE TABLE t_table2 \G
*************************** 1. row ***************************
       Table: t_table2
Create Table: CREATE TABLE `t_table2` (
  `empno` int(11) NOT NULL,
  `ename` varchar(20) DEFAULT NULL,
  `job` varchar(20) DEFAULT NULL,
  `MGR` int(11) DEFAULT NULL,
  `Hiredate` date DEFAULT NULL,
  `salary` float DEFAULT NULL,
  `comm` float DEFAULT NULL,
  `deptno` int(11) NOT NULL,
  PRIMARY KEY (`empno`),
  KEY `index_ename` (`ename`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1
1 row in set (0.00 sec)
```
**建立索引可以提高查找速度**

3.10 将表2的 sal 字段改名为 salary
```sql
mysql> alter table t_table2
    -> change sal salary float;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc t_table2;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| empno    | int(11)     | NO   | PRI | NULL    |       |
| ename    | varchar(20) | YES  |     | NULL    |       |
| job      | varchar(20) | YES  |     | NULL    |       |
| MGR      | int(11)     | YES  |     | NULL    |       |
| Hiredate | date        | YES  |     | NULL    |       |
| salary   | float       | YES  |     | NULL    |       |
| comm     | float       | YES  |     | NULL    |       |
| deptno   | int(11)     | NO   |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
8 rows in set (0.00 sec)
```
3.11 撰写一个函数 get_deptno_from_empno，输入 empno，输出对应的 deptno。 简述函数和存储过程有什么不同。
```sql
mysql> DELIMITER $$
mysql> CREATE FUNCTION get_deptno_from_empno (empno INT)
    -> RETURNS DOUBLE
    -> BEGIN
    -> RETURN (SELECT deptno FROM t_table2
    -> WHERE t_table2.empno = empno);
    -> END$$
Query OK, 0 rows affected (0.04 sec)

mysql> DELIMITER ;
mysql> SELECT get_deptno_from_empno (7844);
+-------------------------------+
| get_deptno_from_empno  (7844) |
+-------------------------------+
|                            30 |
+-------------------------------+
1 row in set (0.01 sec)
```
`
不同：
1.存储过程可以返回参数，函数只能返回值或者表对象
2.函数只能返回一个变量，存储过程可以返回多个变量
3.存储过程可以有三种,OUT,INOUT 类型，函数中必须包含一个有效的RETURN语句
4.存储过程一般是作为一个独立部分来执行的（EXECUTE语句执行），函数可以作为查询语句的一个部分来调用（SELECT)
`

4 建立一个新用户，账号为自己的姓名拼音，密码为自己的学号；
```SQL
mysql> CREATE USER 'WangYijian'@'localhost' IDENTIFIED BY '17061524';
Query OK, 0 rows affected (0.00 sec)
```

4.1 将表1的SELECT, INSERT, UPDATE(ename)权限赋给该账号。
```sql
mysql> GRANT SELECT,INSERT ON *.*
    -> TO 'WangYijian'@'localhost'
    -> IDENTIFIED BY '17061524'
    -> WITH GRANT OPTION;
Query OK, 0 rows affected, 1 warning (0.00 sec)
```

4.2 显示该账号权限
```sql
mysql> SELECT Host,User,Select_priv,Grant_priv
    -> FROM mysql.user
    -> WHERE User='WangYijian';
+-----------+------------+-------------+------------+
| Host      | User       | Select_priv | Grant_priv |
+-----------+------------+-------------+------------+
| localhost | WangYijian | Y           | Y          |
+-----------+------------+-------------+------------+
1 row in set (0.00 sec)
```
4.3 `with grant option` 是什么意思。
`
with grant option可以将select ,update权限授权给第三方。
`
5 表 1 和表 2 这样设计是否符合第一范式，是否符合第二范式，为什么？
`
表一符合第一范式和第二范式。表一的关系中的每个属性不可再分，满足第一范式；表中的一个属性确定了其他的属性也随之确定，满足第二范式。
表二符合第一范式，但不符合第二范式。表一关系中的每个属性都不可再分，满足第一范式；但表中MGR属性确定了不能确定其他的属性，不满足第二范式
`
6 画出表 1 和表 2 所对应的 E-R 图

7 什么是外模式，什么是内模式。为什么要分成这几层？
`
外模式：外模式又称子模式或用户模式，对应于用户级。它是某个或某几个用户所看到的数据库的数据视图，是与某一来应用有关的数据的逻辑表示。外模式是从模式导出的一个子集，包含模式中允许特定用户使用的那部分数据。用户可以通过外模式描述语言来描述、定义对应于用户的数据记录(外模式)，也可以利用数据操纵语言(Data Manipulation Language，DML)对这些数据记录进自行操作。外模式反映了数据库的用户观。
内模式：内模式又称存储模式，百对应于物理级，它是数据库中全体数据的内部表示或底层描述，是数据库最低一级的逻辑描述，它描述了数据在存度储问介质上的存储方式和物理结构，对应着实际存储在外存储介质上的数据库。内模式由内模式描述语言来描述、定义，它是数据库的存储观。
在一个数据库系统中，只有唯一的数据库， 因而作为定义 、描述数据库存储结构的内模式和定义、描述数据库逻辑结答构的模式，也是唯一的，但建立在数据库系统之上的应用则是非常广泛、多样的，所以对应的外模式不是唯一的，也不可能是唯一的。
目的：为数据库设计了一个严谨的体系结构，数据库领域公认的标准结构是三级模式结构，它包括外模式、概念模式、内模式，有效地组织、管理数据，提高了数据库的逻辑独立性和物理独立性。用户级对应外模式，概念级对应概念模式，物理级对应内模式，使不同级别的用户对数据库形成不同的视图。
`

8 什么是ACID？
`
ACID一般是指数据库事务的ACID.一个事务一般是指多个操作的集合，比如插入数据库分两段插入，第二次插入错误，第一次插入操作也需要回退
ACID含义
原子性（Atomicity ）：指的是整个事务是一个独立的单元，要么操作成功，要么操作不成功
一致性（Consistency）：事务必须要保持和系统处于一致的状态（如果不一致会导致系统其它的方出现bug）
隔离性（Isolation ）：事务是并发控制机制，他们的交错也需要一致性，隔离隐藏，一般通过悲观或者乐观锁实现
耐久性（Durability）：一个成功的事务将永久性地改变系统的状态，所以在它结束之前，所有导致状态的变化都记录在一个持久的事务日志中
`

8.1 编写一个事务，“将 MILLER 的 comm 增加 100，如果增加后的 comm 大于 1000 则回滚”；

8.2 如何查看 MySQL 当前的隔离级别？
```sql
mysql> SELECT @@tx_isolation;
+-----------------+
| @@tx_isolation  |
+-----------------+
| REPEATABLE-READ |
+-----------------+
1 row in set, 1 warning (0.00 sec)
```

8.3 如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到的结果有哪些，原因是什么？
`
如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到原先未提交的内容（1300），因为READ-UNCOMMITED为读取未提交内容
`
9 有哪些场景不适合用关系型数据库？为什么？
`
1.图片、文件、二进制数据对数据库的读/写的速度永远都赶不上文件系统处理的速度，数据库备份变的巨大，越来越耗时间，对文件的访问需要穿越你的应用层和数据库层
2.短生命期数据使用情况统计数据，测量数据，GPS定位数据，session数据，任何只是短时间内对用户有用，或经常变化的数据。
3.日志文件也许你的日志记录做的很保守，每次web请求只产生一条日志。 对于整个网站的每个事件来说，这仍然会产生大量的数据库插入操作，争夺用户需要的数据库资源。
`
