##DATA DEFINITION LANGUANGE

#### Membuat Database
```bash
CREATE DATABASE dbname;
```

### Melihat daftar database yg telah ada
```bash
\l
```

#### Untuk masuk ke database
```bash
\c dbname
```

#### Untuk Drop Database
```bash
DROP DATABASE [ IF EXISTS ] dbname;

DROP DATABASE name;
```

#### MEMBUAT TABEL
```bash
CREATE TABLE table_name(
   column1 datatype,
   column2 datatype,
   column3 datatype,
   .....
   columnN datatype,
   PRIMARY KEY( one or more columns )
);

## Melihat daftar table yang telah dibuat 
\d
```

#### MENGHAPUS TABEL
```bash
DROP TABLE table_name;

Jika Table berhubungan dengan table lain, maka cara untuk menghapus

#Untuk menghapus paksa ada atau tidaknya relasi,tabel akan dihapus

DROP TABLE table_name CASCADE; 

#Untuk menghapus table namun jika ada relasi maka table tidak dapat dihapus, muncul peringatan adanya relasi 

DROP TABLE table_name RESTRICT;
```

#### MEMODIFIKASI OBJEK PADA TABEL
```bash
#Menambahkan kolom
ALTER TABLE <table-name> ADD COLUMN <column-name> <data-type>

#Menghapus kolom
ALTER TABLE <table-name> DROP COLUMN <column-name>

#Menambahkan constraint
ALTER TABLE <table-name> ADD <constraint>

#Mengghapus constraint
ALTER TABLE <table-name> DROP CONSTRAINT <constraint-name>

#Mengubah default value
ALTER TABLE <table-name> ALTER COLUMN <column-name> SET
DEFAULT <new-default-value>;

#Mengubah tipe data
ALTER TABLE <table-name> ALTER COLUMN <column-name> TYPE
<data-type>;

#Mengubah nama kolom
ALTER TABLE <table-name> RENAME COLUMN <old-column-name> TO
<new-column-name>;

#Mengubah nama tabel
ALTER TABLE <old-table-name> RENAME TO <new-table-name>;
```
```bash
Contoh penggunaan ALTER
 id | name  | age | address   | salary
----+-------+-----+-----------+--------
  1 | Paul  |  32 | California|  20000
  2 | Allen |  25 | Texas     |  15000
  3 | Teddy |  23 | Norway    |  20000
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
  6 | Kim   |  22 | South-Hall|  45000
  7 | James |  24 | Houston   |  10000
	
	ALTER TABLE COMPANY ADD GENDER char(1);
	
	 id | name  | age | address     | salary | gender
----+-------+-----+-------------+--------+--------
  1 | Paul  |  32 | California  |  20000 |
  2 | Allen |  25 | Texas       |  15000 |
  3 | Teddy |  23 | Norway      |  20000 |
  4 | Mark  |  25 | Rich-Mond   |  65000 |
  5 | David |  27 | Texas       |  85000 |
  6 | Kim   |  22 | South-Hall  |  45000 |
  7 | James |  24 | Houston     |  10000 |
(7 rows)
```

## DATA MANIPULATION LANGUAGE

#### MEMILIH TABEL YANG DIMUNCULKAN
```bash
#Untuk memlih table dengan kolom tertentu
SELECT column1, column2, columnN FROM table_name;

#memunculkan semua kolom pada table
SELECT * FROM table_name;
```

#### MEMASUKKAN DATA PADA TABEL

```bash
#Cara 1 : memasukkan data dengan menyebutkan judul kolom dan isi data yg akan dimasukkan
INSERT INTO TABLE_NAME (column1, column2, column3,...columnN)
VALUES (value1, value2, value3,...valueN);

#Cara 2 : Langsung memasukkan data yang diurutkan sesuai urutan kolom
INSERT INTO TABLE_NAME VALUES (value1,value2,value3,...valueN);
```

#### MEMPERBAHARUI DATA PADA TABLE
```bash
#UPDATE
UPDATE table_name
SET column1 = value1, column2 = value2...., columnN = valueN
WHERE [condition];

#DELETE 
##Untuk menghapus baris tertentu
DELETE FROM table_name
WHERE [condition];

##Untuk menghapus semua yang ada di dalam table
DELETE FROM table_name;
