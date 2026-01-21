# SQL – szybkie notatki

### INSERT
Wrzucamy dane do bazy.

```sql
INSERT INTO tabela VALUES ('chuj', 'pipa');
CREATE TABLE
```
### Tworzenie tabeli.


```sql
CREATE TABLE tabela (
  ID int,
  Name varchar(255),
  isVerified bool
);
```
### ALTER TABLE

Pozwala na dodawanie, modyfikowanie oraz usuwanie kolumn w tabelach

```sql
ALTER TABLE tabelka
ADD imie varchar(255);

ALTER TABLE tabelka
DROP COLUMN imie;

ALTER TABLE tabelka
RENAME COLUMN imie to new_imie;
```


### PRIMARY KEY
Unikalna wartość w tabeli, która identyfikuje dany wpis (np. ID).

```sql
CREATE TABLE tabela (
  ID int PRIMARY KEY,
  Name varchar(255),
  isVerified bool
);
```
### NOT NULL

Wartość, która nigdy nie będzie NULL (zawsze musi być jakaś wartość w komórce).

```sql

CREATE TABLE tabela (
  ID int,
  Name varchar(255) NOT NULL,
  isVerified bool NOT NULL
);

```
### MAX
Zwraca maksymalną wartość z kolumny.

```sql
SELECT MAX(wynagrodzenie) FROM Pracownicy;
```

### MIN
Zwraca minimalną wartość z kolumny.

```sql
SELECT MIN(wynagrodzenie) FROM Pracownicy;
```
### AVG
 Zwraca średnią wartość z kolumny.
```sql
SELECT AVG(wynagrodzenie) FROM Pracownicy;
```

### JOIN ... ON
Łączy dwie (lub więcej) tabele, bazując na pasujących kolumnach.

```sql
SELECT Orders.OrderID, Customers.CustomerName
FROM Orders
JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
```

### SELECT
Wybiera dane i zwraca je z tabeli.
```sql
SELECT * FROM Pracownicy;
```
### ORDER BY
Sortuje dane rosnąco / malejąco według kolumny.

```sql
SELECT wynagrodzenie
FROM Pracownicy
ORDER BY wynagrodzenie ASC; -- lub DESC
```
### WHERE
Filtrowanie danych według warunku.
```sql
SELECT * FROM Pracownicy WHERE wynagrodzenie > 3000;

-- % działa jako "cokolwiek"
SELECT * FROM Pracownicy WHERE imie LIKE '%a'; -- kończy się na "a"
```

### COUNT
Zwraca liczbę wpisów, które spełniają warunek.

```sql
SELECT COUNT(*) FROM Users WHERE isVerified = true;
```

### GROUP BY
Grupuje dane po tej samej wartości (np. per kraj) i pozwala liczyć podsumowania.
```sql
SELECT Country, COUNT(*) AS liczba
FROM Users
GROUP BY Country;
```
### UNION
Łączy dwa lub więcej SELECTów, skleja wyniki w jedno i usuwa duplikaty.

```sql 
SELECT email FROM users
UNION
SELECT email FROM subscribers;
```

### INTERSECT
Łączy dwa lub więcej SELECTów, ale pokazuje tylko część wspólną wyników.

```sql
SELECT email FROM users
INTERSECT
SELECT email FROM subscribers;
```

### LIMIT
Ogranicza liczbę zwróconych wyników.

```sql
SELECT wynagrodzenie FROM Pracownicy LIMIT 5;
```