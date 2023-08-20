# Kodluyoruz_SQL
Patika SQL
## SQL Ödev 01 | WHERE ve Mantıksal Operatörler 
1- film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
```javascript
SELECT title, description FROM film;
```
---
2-film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
```javascript
SELECT * FROM film
WHERE length > 60 AND length < 75;
```
---
3-film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
```javascript
SELECT * FROM film
WHERE rental_rate = 0.99 AND replacement_cost = 12.99
OR replacement_cost = 28.99;
```
---
4-customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
```javascript
SELECT last_name FROM customer
WHERE first_name = 'Mary';
```
---
5-film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
```javascript
SELECT * FROM film
WHERE length <= 50 
AND NOT (rental_rate = 2.99 OR rental_rate = 4.99);
```
---
## SQL Ödev 02 | BETWEEN ve IN
1-film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
```javascript
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```
---
2-actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
```javascript
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope', 'Nick', 'Ed');
```
---
3-film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)
```javascript
SELECT * FROM actor
WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);
```
---
## SQL Ödev 03 | LIKE ve ILIKE
1-country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
```javascript
SELECT country FROM country
WHERE country LIKE 'A%a';
```
Şöyle de yazılabilir:
```javascript
SELECT country FROM country
WHERE country ~~ 'A%a';
```
---
2-country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
```javascript
SELECT country FROM country
WHERE country LIKE '_____%n'
```
> NOT: en az 6 karakter için 5 adet alt çizgi eklendi!
---
3-film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
```javascript
SELECT title FROM film
WHERE title ILIKE 'T%T%T%T%';
```
Şöyle de yazılabilir:
```javascript
SELECT title FROM film
WHERE title ~~* 'T%T%T%T%';
```
---
4-film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
```javascript
SELECT * FROM film
WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;
```
---
## SQL Ödev 04 | DISTINCT ve COUNT
1-film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
```javascript
SELECT DISTINCT replacement_cost FROM film;
```
---
2-film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
```javascript
SELECT COUNT(DISTINCT replacement_cost) FROM film;
```
---
3-film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```javascript
SELECT COUNT (*) FROM film
WHERE title LIKE 'T%' AND rating ='G';
```
---
4-country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
```javascript
SELECT COUNT(*) FROM country
WHERE country LIKE '_____';
```
---
5-city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?
```javascript
SELECT COUNT (*) FROM city
WHERE city ILIKE '%R';
```
---
## SQL Ödev 05 | ORDER BY, LIMIT ve OFFSET
1-film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
```javascript
SELECT title, length FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
```
---
2-film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.
```javascript
SELECT title, length FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
OFFSET 5
LIMIT 5;
```
---
3-customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```javascript
SELECT * FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
```
---
## SQL Ödev 06 | Aggregate Fonksiyonlar
1-film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
```javascript
SELECT AVG(rental_rate) FROM film;
```
> İki karaktere kadar yuvarlamak için:
```javascript
SELECT ROUND(AVG(rental_rate),2) FROM film;
```
---
2-film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?
```javascript
SELECT COUNT(*) FROM film
WHERE title LIKE 'C%';
```
---
3-film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
```javascript
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;
```
---
4-film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
```javascript
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150;
```
---
## SQL Ödev 07 | GROUP BY ve HAVING
1-film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
```javascript
SELECT rating FROM film
GROUP BY rating;
```
---
2-film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
```javascript
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
```
---
3-customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
```javascript
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
```
---
4-city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.
```javascript
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
```
---
## SQL Ödev 08 | Tablo Oluşturmak - Silmek ve Verileri Güncellemek - Silmek
1-test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
```javascript
CREATE TABLE employee (
	id INTEGER, 
	name VARCHAR(50), 
	birthday DATE, 
	email VARCHAR(100)
);
```
---
2-Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
```javascript
insert into employee (id, name, birthday, email) values (1, 'Daphna Dobing', null, 'ddobing0@cnn.com');
insert into employee (id, name, birthday, email) values (2, 'Kally Balazot', '1956-12-11', 'kbalazot1@techcrunch.com');
insert into employee (id, name, birthday, email) values (3, 'Mackenzie Schnieder', null, 'mschnieder2@pcworld.com');
insert into employee (id, name, birthday, email) values (4, 'Sophi Jamrowicz', '1974-06-04', 'sjamrowicz3@ezinearticles.com');
insert into employee (id, name, birthday, email) values (5, 'Tamra Pien', '1907-11-13', 'tpien4@blogspot.com');
insert into employee (id, name, birthday, email) values (6, 'Dorie Holt', '2093-05-24', 'dholt5@unc.edu');
insert into employee (id, name, birthday, email) values (7, 'Darcy Baigent', null, 'dbaigent6@g.co');
insert into employee (id, name, birthday, email) values (8, 'Kirstyn Fouracres', '2024-11-19', 'kfouracres7@reverbnation.com');
insert into employee (id, name, birthday, email) values (9, 'Lemmy Arnaudon', null, 'larnaudon8@oracle.com');
insert into employee (id, name, birthday, email) values (10, 'Pavlov Barthelet', '1942-05-27', 'pbarthelet9@typepad.com');
insert into employee (id, name, birthday, email) values (11, 'Francklin Viccars', '2077-03-05', 'fviccarsa@a8.net');
insert into employee (id, name, birthday, email) values (12, 'Humfried Vanderson', '2087-06-20', 'hvandersonb@nifty.com');
insert into employee (id, name, birthday, email) values (13, 'Jedd Spiers', '1906-03-30', 'jspiersc@plala.or.jp');
insert into employee (id, name, birthday, email) values (14, 'Brandtr Dubarry', null, 'bdubarryd@pcworld.com');
insert into employee (id, name, birthday, email) values (15, 'Tova Dettmar', '1943-04-06', 'tdettmare@ucoz.com');
insert into employee (id, name, birthday, email) values (16, 'Alexio Langton', '2082-04-28', 'alangtonf@wix.com');
insert into employee (id, name, birthday, email) values (17, 'Colet Symcox', '1906-11-23', 'csymcoxg@guardian.co.uk');
insert into employee (id, name, birthday, email) values (18, 'Bryana McAsgill', '2046-03-31', 'bmcasgillh@home.pl');
insert into employee (id, name, birthday, email) values (19, 'Daria Thompkins', '1911-10-09', 'dthompkinsi@vkontakte.ru');
insert into employee (id, name, birthday, email) values (20, 'Bertie Jorge', '1963-10-02', 'bjorgej@diigo.com');
insert into employee (id, name, birthday, email) values (21, 'Stevy Bowling', '2008-08-14', 'sbowlingk@cmu.edu');
insert into employee (id, name, birthday, email) values (22, 'Trumaine Artinstall', '2014-05-25', 'tartinstalll@addthis.com');
insert into employee (id, name, birthday, email) values (23, 'Jada Seller', '2065-10-21', 'jsellerm@opera.com');
insert into employee (id, name, birthday, email) values (24, 'Cory Endley', '1969-05-05', 'cendleyn@godaddy.com');
insert into employee (id, name, birthday, email) values (25, 'Diann Bohler', '1997-11-24', 'dbohlero@xing.com');
insert into employee (id, name, birthday, email) values (26, 'Pete Moreing', null, 'pmoreingp@reuters.com');
insert into employee (id, name, birthday, email) values (27, 'Jennee Rizzo', '2070-03-30', 'jrizzoq@sakura.ne.jp');
insert into employee (id, name, birthday, email) values (28, 'Godfrey Miguel', null, 'gmiguelr@cnbc.com');
insert into employee (id, name, birthday, email) values (29, 'Ned Davidovits', '1932-12-02', 'ndavidovitss@altervista.org');
insert into employee (id, name, birthday, email) values (30, 'Jocelyn Kiefer', null, 'jkiefert@devhub.com');
insert into employee (id, name, birthday, email) values (31, 'Shaughn McCarlie', '1952-04-23', 'smccarlieu@wikimedia.org');
insert into employee (id, name, birthday, email) values (32, 'Joel Bridden', null, 'jbriddenv@weibo.com');
insert into employee (id, name, birthday, email) values (33, 'Shea Clifforth', '1942-06-08', 'sclifforthw@desdev.cn');
insert into employee (id, name, birthday, email) values (34, 'Kellsie Mangam', '2079-04-09', 'kmangamx@netlog.com');
insert into employee (id, name, birthday, email) values (35, 'Francklyn Kenford', '1915-04-01', 'fkenfordy@ucla.edu');
insert into employee (id, name, birthday, email) values (36, 'Vevay Eccleshare', '1998-07-13', 'vecclesharez@opera.com');
insert into employee (id, name, birthday, email) values (37, 'Prentice Grabbam', null, 'pgrabbam10@facebook.com');
insert into employee (id, name, birthday, email) values (38, 'Malinda Sundin', '1961-06-11', 'msundin11@vinaora.com');
insert into employee (id, name, birthday, email) values (39, 'Lib Liptrod', '2052-02-21', 'lliptrod12@dell.com');
insert into employee (id, name, birthday, email) values (40, 'Erhard Cakebread', '2069-07-21', 'ecakebread13@jimdo.com');
insert into employee (id, name, birthday, email) values (41, 'Erhard Ghidelli', '1924-09-09', 'eghidelli14@flickr.com');
insert into employee (id, name, birthday, email) values (42, 'Leila Drains', '2044-04-24', 'ldrains15@multiply.com');
insert into employee (id, name, birthday, email) values (43, 'Sybilla Finley', null, 'sfinley16@sogou.com');
insert into employee (id, name, birthday, email) values (44, 'Tiffanie Mil', '2067-09-21', 'tmil17@state.tx.us');
insert into employee (id, name, birthday, email) values (45, 'Priscella Urquhart', '1984-03-28', 'purquhart18@1688.com');
insert into employee (id, name, birthday, email) values (46, 'Pate Bracco', '1913-09-23', 'pbracco19@chron.com');
insert into employee (id, name, birthday, email) values (47, 'Skell Guess', null, 'sguess1a@toplist.cz');
insert into employee (id, name, birthday, email) values (48, 'Helga O''Donnelly', '2014-10-16', 'hodonnelly1b@qq.com');
insert into employee (id, name, birthday, email) values (49, 'Emile Wisker', null, 'ewisker1c@netlog.com');
insert into employee (id, name, birthday, email) values (50, 'Nannie Adolf', '2080-07-01', 'nadolf1d@github.com');
```
---
3-Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
> id'si 1 olanın name, birthday ve emailini günceller.
```javascript
UPDATE employee
SET name = 'serafettin',
    birthday = '1983-01-01',
    email = 'sero@mail.com'
WHERE id= 1;
```
> ismi Daphna Dobing olanı, ismi XXXXXXXXXX olacak şekilde değiştirir.
```javascript
UPDATE employee
SET name = 'XXXXXXXXXX'
WHERE name = 'Daphna Dobing';
```
> ismi Kally Balazot olanın emailini bal@mail.com olarak değiştirir.
```javascript
UPDATE employee
SET email = 'bal@mail.com'
WHERE name = 'Kally Balazot';
```
> birthday, 2014-10-16 olanı, ismi YYYYYYYYYY olacak şekilde değiştirir.
```javascript
UPDATE employee
SET name = 'YYYYYYYYYY'
WHERE birthday = '2014-10-16';
```
> emaili hodonnelly1b@qq.com olanın birthdayini 1983-01-01 olarak değiştirir.
```javascript
UPDATE employee
SET birthday = '1983-01-01'
WHERE email = 'hodonnelly1b@qq.com';
```
---
4-Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
```javascript
DELETE FROM employee
WHERE name = 'Skell Guess';
```
```javascript
DELETE FROM employee
WHERE birthday = '2044-04-24';
```
```javascript
DELETE FROM employee
WHERE birthday >= '2010-01-01';
```
```javascript
DELETE FROM employee
WHERE name LIKE 'A%'
RETURNING *;
```
```javascript
DELETE FROM employee
WHERE id = 3 AND name LIKE 'M%'
RETURNING *;
```
---
## SQL Ödev 09 | INNER JOIN
1-city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```javascript
SELECT city, country FROM city
INNER JOIN country ON city.country_id = country.country_id;
```
---
2-customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```javascript
SELECT payment.payment_id, customer.first_name, customer.last_name FROM customer
INNER JOIN payment ON customer.customer_id = payment.customer_id;
```
---
3-customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```javascript
SELECT rental.rental_id, customer.first_name, customer.last_name
FROM customer
INNER JOIN rental ON customer.customer_id = rental.customer_id;
```
---
## SQL Ödev 10 | LEFT JOIN, RIGHT JOIN ve FULL JOIN
1-city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
```javascript
SELECT city.city, country.country FROM city
LEFT JOIN country ON city.country_id = country.country_id;
```
---
2-customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
```javascript
SELECT payment.payment_id, customer.first_name, customer.last_name FROM customer
RIGHT JOIN payment ON customer.customer_id = payment.customer_id;
```
---
3-customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
```javascript
SELECT rental.rental_id, customer.first_name, customer.last_name FROM customer
FULL JOIN rental ON rental.customer_id = customer.customer_id;
```
---
## SQL Ödev 11 | UNION, INTERSECT ve EXCEPT
1-actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
```javascript
SELECT first_name FROM actor
UNION
SELECT first_name FROM customer;
```
---
2-actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
```javascript
SELECT first_name FROM actor
INTERSECT
SELECT first_name FROM customer;
```
---
3-actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
```javascript
SELECT first_name FROM actor
EXCEPT
SELECT first_name FROM customer;
```
---
4-İlk 3 sorguyu tekrar eden veriler için de yapalım.
```javascript
SELECT first_name FROM actor
UNION ALL
SELECT first_name FROM customer;
```
```javascript
SELECT first_name FROM actor
INTERSECT ALL
SELECT first_name FROM customer;
```
```javascript
SELECT first_name FROM actor
EXCEPT ALL
SELECT first_name FROM customer;
```
---
## SQL Ödev 12 | Alt sorgular
1-film tablosunda film uzunluğu length sütununda gösterilmektedir. 
Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
```javascript
SELECT COUNT(*) FROM film
WHERE length >
(
	SELECT AVG(length) FROM film
);
```
---
2-film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
```javascript
SELECT rental_rate, COUNT(*) FROM film
WHERE rental_rate =
(
	SELECT MAX(rental_rate) FROM film
)
GROUP BY rental_rate;
```
---
3-film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine 
sahip filmleri sıralayınız.
```javascript
SELECT * FROM film
WHERE rental_rate =
(
	SELECT MIN(rental_rate) FROM film
)
AND replacement_cost =
(
	SELECT MIN(replacement_cost) FROM film
)
ORDER BY film_id;
```
---
4-payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
```javascript
SELECT customer_id, COUNT(*) AS alışveriş_sayısı
FROM payment
GROUP BY customer_id
ORDER BY alışveriş_sayısı DESC;
```
---
## SQL Tekrar Çalışması:
Örnek Çalışma: isminde en az 4 tane e veya E bulunan kaç tane film vardır?
```javascript
SELECT COUNT(*) FROM film
WHERE title ILIKE '%e%e%e%e%';
```
---
Örnek Çalışma: Önek Çalışma:kategori ismlerini ve kategori başına düşen film sayısını yazınız.(film tablosu ile kategori tablosu arasında doğrudan bir bağlantı olmadığı için bağlantıyı film_category tablosu üzerinden yapıyoruz.)
```javascript
SELECT COUNT(*), category.name FROM category
JOIN film_category On category.category_id = film_category.category_id
JOIN film ON film.film_id = film_category.film_id
GROUP BY category.name;
```
---
Örnek Çalışma: En çok film bulunan rating kategorisi hangisidir?
```javascript
SELECT rating, COUNT(*) FROM film
GROUP BY rating
ORDER BY count DESC
LIMIT 1;
```
---
Örnek Çalışma: film tablosunda 'K' karakteri ile başlayan en uzun ve replacement_cost en az olan 3 filmi sıralayınız.
```javascript
SELECT title, length, replacement_cost FROM film
WHERE title LIKE 'K%'
ORDER BY length DESC, replacement_cost ASC
LIMIT 3;
```
---
Örnek Çalışma: en çok alışveriş yapan müşterinin adı nedir?
```javascript
SELECT SUM(amount), customer.first_name, customer.last_name FROM payment
JOIN customer ON customer.customer_id = payment.customer_id
GROUP BY payment.customer_id, customer.first_name, customer.last_name
ORDER BY SUM(amount) DESC
LIMIT 1;
```
---





