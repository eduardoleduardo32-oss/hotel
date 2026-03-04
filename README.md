```
MariaDB [(none)]> CREATE DATABASE hotel;
Query OK, 0 rows affected (0.072 sec)
 MariaDB [(none)]> use hotel;
Query OK, 1 row affected (0.001 sec)
Database changed 
```
MariaDB [hotel]> CREATE TABLE pelanggan (

    ->     id_pelanggan INT PRIMARY KEY AUTO_INCREMENT,
    
    ->     nama_pelanggan VARCHAR(100) NOT NULL,
    
    ->     no_telepon VARCHAR(15),
    
    ->     alamat TEXT
    
    -> );
Query OK, 0 rows affected (0.077 sec) 

MariaDB [hotel]> CREATE TABLE kamar (

    ->     id_kamar INT PRIMARY KEY AUTO_INCREMENT,
    
    ->     nomor_kamar VARCHAR(10) NOT NULL,
    
    ->     tipe_kamar VARCHAR(50),
    
    ->     harga_per_malam DECIMAL(10,2),
    
    ->     status_kamar VARCHAR(20)
    
    -> );
Query OK, 0 rows affected (0.068 sec)

MariaDB [hotel]> CREATE TABLE reservasi 
(
    ->     id_reservasi INT PRIMARY KEY AUTO_INCREMENT,
    
    ->     id_pelanggan INT,
    
    ->     id_kamar INT,
    
    ->     tanggal_checkin DATE,
    
    ->     tanggal_checkout DATE,
    
    ->     FOREIGN KEY (id_pelanggan) REFERENCES pelanggan(id_pelanggan),
    
    ->     FOREIGN KEY (id_kamar) REFERENCES kamar(id_kamar)
    
    -> );
    
Query OK, 0 rows affected (0.283 sec)

INSERT INTO pelanggan (nama_pelanggan, no_telepon, alamat)

VALUES

('ado', '085814157439','jakarta'),

('dee', '085714157439', 'bogor'),

('cihuy', '085614157439', 'sukahati'),

('kakaw', '085214157439', 'keraken');

Query OK, 4 rows affected (0.340 sec)

MariaDB [hotel]> INSERT INTO kamar (nomor_kamar, tipe_kamar, harga_per_malam, status_kamar)VALUES

    ->      ('100', 'Misquen', '150000', 'Tersedia'),
    
    ->     ('101', 'Umr', '250000', 'Tersedia'),
    
    ->     ('102', 'Tajir', '500000', 'Tersedia'),
    
    ->     ('103', 'Sultan', '1000000', 'Tersedia');
    
Query OK, 4 rows affected (0.005 sec)

MariaDB [hotel]> INSERT INTO reservasi (id_pelanggan, id_kamar, tanggal_checkin, tanggal_checkout)VALUES

    ->      (1, 2, '2025-12-31', '2026-01-01'),
    
    ->      (2, 1, '2026-01-31', '2026-02-01'),
    
    ->      (3, 3, '2026-02-28', '2026-03-01');
    
Query OK, 3 rows affected (0.007 sec)

MariaDB [hotel]> SELECT pelanggan.nama_pelanggan, kamar.nomor_kamar, reservasi.tanggal_checkin, reservasi.tanggal_checkout

    ->      FROM reservasi
    
    ->      INNER JOIN pelanggan ON reservasi.id_pelanggan = reservasi.id_pelanggan
    
    ->      INNER JOIN kamar ON kamar.id_kamar = kamar.id_kamar;
    
+----------------+-------------+-----------------+------------------+

| nama_pelanggan | nomor_kamar | tanggal_checkin | tanggal_checkout |

+----------------+-------------+-----------------+------------------+

| ado            | 100         | 2025-12-31      | 2026-01-01       |

| ado            | 100         | 2026-01-31      | 2026-02-01       |

| ado            | 100         | 2026-02-28      | 2026-03-01       |

| dee            | 100         | 2025-12-31      | 2026-01-01       |

| dee            | 100         | 2026-01-31      | 2026-02-01       |

| dee            | 100         | 2026-02-28      | 2026-03-01       |

| cihuy          | 100         | 2025-12-31      | 2026-01-01       |

| cihuy          | 100         | 2026-01-31      | 2026-02-01       |

| cihuy          | 100         | 2026-02-28      | 2026-03-01       |

| kakaw          | 100         | 2025-12-31      | 2026-01-01       |

| kakaw          | 100         | 2026-01-31      | 2026-02-01       |

| kakaw          | 100         | 2026-02-28      | 2026-03-01       |

| ado            | 101         | 2025-12-31      | 2026-01-01       |

| ado            | 101         | 2026-01-31      | 2026-02-01       |

| ado            | 101         | 2026-02-28      | 2026-03-01       |

| dee            | 101         | 2025-12-31      | 2026-01-01       |

| dee            | 101         | 2026-01-31      | 2026-02-01       |

| dee            | 101         | 2026-02-28      | 2026-03-01       |

| cihuy          | 101         | 2025-12-31      | 2026-01-01       |

| cihuy          | 101         | 2026-01-31      | 2026-02-01       |

| cihuy          | 101         | 2026-02-28      | 2026-03-01       |

| kakaw          | 101         | 2025-12-31      | 2026-01-01       |

| kakaw          | 101         | 2026-01-31      | 2026-02-01       |

| kakaw          | 101         | 2026-02-28      | 2026-03-01       |

| ado            | 102         | 2025-12-31      | 2026-01-01       |

| ado            | 102         | 2026-01-31      | 2026-02-01       |

| ado            | 102         | 2026-02-28      | 2026-03-01       |

| dee            | 102         | 2025-12-31      | 2026-01-01       |

| dee            | 102         | 2026-01-31      | 2026-02-01       |

| dee            | 102         | 2026-02-28      | 2026-03-01       |

| cihuy          | 102         | 2025-12-31      | 2026-01-01       |

| cihuy          | 102         | 2026-01-31      | 2026-02-01       |

| cihuy          | 102         | 2026-02-28      | 2026-03-01       |

| kakaw          | 102         | 2025-12-31      | 2026-01-01       |

| kakaw          | 102         | 2026-01-31      | 2026-02-01       |

| kakaw          | 102         | 2026-02-28      | 2026-03-01       |

| ado            | 103         | 2025-12-31      | 2026-01-01       |

| ado            | 103         | 2026-01-31      | 2026-02-01       |

| ado            | 103         | 2026-02-28      | 2026-03-01       |

| dee            | 103         | 2025-12-31      | 2026-01-01       |

| dee            | 103         | 2026-01-31      | 2026-02-01       |

| dee            | 103         | 2026-02-28      | 2026-03-01       |

| cihuy          | 103         | 2025-12-31      | 2026-01-01       |

| cihuy          | 103         | 2026-01-31      | 2026-02-01       |

| kakaw          | 103         | 2025-12-31      | 2026-01-01       |

| kakaw          | 103         | 2026-01-31      | 2026-02-01       |

| kakaw          | 103         | 2026-02-28      | 2026-03-01       |

+----------------+-------------+-----------------+------------------+

48 rows in set (0.001 sec)

MariaDB [hotel]> SELECT pelanggan.nama_pelanggan, reservasi.id_reservasi

    ->      FROM pelanggan
    
    ->      LEFT JOIN reservasi ON pelanggan.id_pelanggan = reservasi.id_pelanggan;
    
+----------------+--------------+

| nama_pelanggan | id_reservasi |

+----------------+--------------+
| ado            |            1 |
| dee            |            2 |
| cihuy          |            3 |
| kakaw          |         NULL |
+----------------+--------------+
4 rows in set (0.002 sec)
MariaDB [hotel]> SELECT kamar.nomor_kamar, reservasi.id_reservasi
    ->     FROM reservasi
    ->      RIGHT JOIN kamar ON reservasi.id_kamar = kamar.id_kamar;
+-------------+--------------+
| nomor_kamar | id_reservasi |
+-------------+--------------+
| 100         |            2 |
| 101         |            1 |
| 102         |            3 |
| 103         |         NULL |
+-------------+--------------+
4 rows in set (0.001 sec)
