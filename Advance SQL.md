## DCL (Data Control Language)

#### GRANT and REVOKE

**GRANT** → merupakan perintah untuk memberikan hak akses (privileges) ke basis data kepada pengguna

**REVOKE** → merupakan perintah untuk mencabut hak akses (privileges) yang telah diberikan menggunakan perintah GRANT kepada pengguna

Bentuk Umum Syntax Grant
```bash
GRANT privilege_name
ON object_name
TO {user_name |PUBLIC |role_name}
[WITH GRANT OPTION];
```
Bentuk Umum syntax Revoke
```bash
REVOKE privilege_name
ON object_name
FROM {user_name |PUBLIC |role_name};
```
Keterangan
- privilege_name → tipe hak akses yang diberikan kepada pengguna, seperti ALL, EXECUTE, SELECT
- object_name → nama objek basis data, seperti TABLE, VIEW, STORED PROC, SEQUENCE
- user_name → nama pengguna yang ingin diberi atau dicabut hak akses
- PUBLIC → hak akses diberi atau dicabut dari seluruh pengguna
- WITH GRANT OPTION → mengizinkan pengguna untuk memberikan hak GRANT kepada pengguna lain

## Advanced SQL

#### Select Multiple Table

```bash
SELECT atribut1,atribur2,atribut3,atributn
FROM Table1, Table_n
WHERE PK = FK
ORDER BY PK;
```

#### JOIN Table

Melakukan selection dari beberapa tabel sekaligus, secara langsung menggabungkan tabel-tabel tersebut dengan syarat-syarat tertentu. Perintah Join memberikan hasil yang sama dengan contoh query sebelumnya yang menggunakan statement where untuk mencocokkan antar table.

```bash
SELECT [aggregation] <column>
FROM <table> JOIN <table> ON <condition>;
 ```
 
#### VIEW

Tabel bayangan yang dibangun dari satu atau beberapa tabel yang sudah ada. Secara fisik, VIEW tidak membuat penyimpanan data seperti 
tabel, melainkan hanya menyimpan referensi/ pointer ke record pada tabel-tabel yang berkaitan. 

```bash
CREATE VIEW ViewName (Field1, Field1) AS SELECT Field_1,
Field_1, …
FROM TableName
WHERE Condition;

#Contoh : 
CREATE VIEW v4 AS
SELECT SSN, CONCAT (FName,' ',LName) AS EName, DName
FROM Employee,Department
WHERE DNum = DNumber;

#DROP
DROP VIEW v1;
```

Selain CREATE, VIEW juga berlaku operasi : **ALTER, DROP, DAN SELECTION**

#### NESTED QUERY
suatu query dimana didalamnya terdapat terdapat query lain yang menjadi kondisi.

Contoh
```bash
SELECT PName
FROM Project WHERE PNumber
IN (SELECT PNum FROM Works_On);
```
#### PROCEDURE
Contoh
```bash 
CREATE OR REPLACE PROCEDURE bonus(VARCHAR, DEC) 
LANGUAGE plpgsql
AS $$
BEGIN 
 UPDATE employee 
 SET salary = salary + $2
 WHERE ssn = $1
 COMMIT;
END;
$$;
```
#### TRIGGER
jenis khusus dari procedures yang bereaksi terhadap event / aksi tertentu pada database. 
Event yang dimaksud adalah  **INSERT**, **UPDATE** , **DELETE** database 

Syntax 
```bash
CREATE TRIGGER <trigger name>
FOR|AFTER|BEFORE <[INSERT][UPDATE][DELETE]>
ON <table or view name>
FOR EACH ROW
<SQL Statement……. >;
```
