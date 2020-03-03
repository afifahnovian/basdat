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
