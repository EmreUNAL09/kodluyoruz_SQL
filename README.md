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
insert into employee (id, name, birthday, email) values (1, 'Gilbertine Eastbrook', '1935-09-12', 'geastbrook0@reddit.com');
insert into employee (id, name, birthday, email) values (2, 'Farand Bertelmot', '1967-03-14', 'fbertelmot1@icq.com');
insert into employee (id, name, birthday, email) values (3, 'Geraldine Shemmans', '1936-09-03', 'gshemmans2@ocn.ne.jp');
insert into employee (id, name, birthday, email) values (4, 'Marianna Bruggen', null, 'mbruggen3@psu.edu');
insert into employee (id, name, birthday, email) values (5, 'Glynnis Willavoys', '1935-10-31', 'gwillavoys4@chronoengine.com');
insert into employee (id, name, birthday, email) values (6, 'Krissie Murrell', '2053-03-31', 'kmurrell5@stanford.edu');
insert into employee (id, name, birthday, email) values (7, 'Tabbatha Gatenby', '1955-03-27', 'tgatenby6@sciencedaily.com');
insert into employee (id, name, birthday, email) values (8, 'Ivett Bullivant', '2041-09-16', 'ibullivant7@mapquest.com');
insert into employee (id, name, birthday, email) values (9, 'Hillary Collerd', '2032-07-08', 'hcollerd8@blogger.com');
insert into employee (id, name, birthday, email) values (10, 'Jerrine Dayne', '2006-03-14', 'jdayne9@loc.gov');
insert into employee (id, name, birthday, email) values (11, 'Mozes Feathers', '2011-05-19', 'mfeathersa@uol.com.br');
insert into employee (id, name, birthday, email) values (12, 'Abra Menhenitt', '2015-05-06', 'amenhenittb@samsung.com');
insert into employee (id, name, birthday, email) values (13, 'Lona Paddingdon', '1963-01-25', 'lpaddingdonc@baidu.com');
insert into employee (id, name, birthday, email) values (14, 'Stepha Chilley', '1954-03-24', 'schilleyd@yellowpages.com');
insert into employee (id, name, birthday, email) values (15, 'Magdaia Loveredge', '1997-02-25', 'mloveredgee@twitter.com');
insert into employee (id, name, birthday, email) values (16, 'Emmery Tinghill', '2094-05-01', 'etinghillf@soup.io');
insert into employee (id, name, birthday, email) values (17, 'Jobyna Blackwell', null, 'jblackwellg@ehow.com');
insert into employee (id, name, birthday, email) values (18, 'Courtnay Cuss', '1988-04-07', 'ccussh@timesonline.co.uk');
insert into employee (id, name, birthday, email) values (19, 'Ethelda Zoephel', null, 'ezoepheli@nsw.gov.au');
insert into employee (id, name, birthday, email) values (20, 'Arnold Marson', '1949-06-25', 'amarsonj@webeden.co.uk');
insert into employee (id, name, birthday, email) values (21, 'Alvina Rodolphe', '2045-01-26', 'arodolphek@meetup.com');
insert into employee (id, name, birthday, email) values (22, 'Ezra De la Barre', '1981-10-11', 'edel@marriott.com');
insert into employee (id, name, birthday, email) values (23, 'Murial Mingotti', '2079-10-24', 'mmingottim@ted.com');
insert into employee (id, name, birthday, email) values (24, 'Jarad Sarrell', '2027-04-12', 'jsarrelln@liveinternet.ru');
insert into employee (id, name, birthday, email) values (25, 'Brunhilde Geeson', '2026-03-09', 'bgeesono@surveymonkey.com');
insert into employee (id, name, birthday, email) values (26, 'Juliann Goodbanne', null, 'jgoodbannep@dropbox.com');
insert into employee (id, name, birthday, email) values (27, 'Robena Okenfold', null, 'rokenfoldq@live.com');
insert into employee (id, name, birthday, email) values (28, 'Clarette Frankiewicz', null, 'cfrankiewiczr@sbwire.com');
insert into employee (id, name, birthday, email) values (29, 'Andeee Ajam', null, 'aajams@odnoklassniki.ru');
insert into employee (id, name, birthday, email) values (30, 'Marita Blakely', null, 'mblakelyt@unc.edu');
insert into employee (id, name, birthday, email) values (31, 'Bordy Scare', '2023-08-18', 'bscareu@posterous.com');
insert into employee (id, name, birthday, email) values (32, 'Dukie Buxy', '2083-04-17', 'dbuxyv@google.com.au');
insert into employee (id, name, birthday, email) values (33, 'Juditha Finlan', '1965-12-18', 'jfinlanw@disqus.com');
insert into employee (id, name, birthday, email) values (34, 'Sherwynd Peche', null, 'spechex@wired.com');
insert into employee (id, name, birthday, email) values (35, 'Talia Siveter', '1945-11-06', 'tsivetery@mit.edu');
insert into employee (id, name, birthday, email) values (36, 'Maryl Epgrave', '2070-03-29', 'mepgravez@webmd.com');
insert into employee (id, name, birthday, email) values (37, 'Quincey Penner', '1974-11-04', 'qpenner10@uiuc.edu');
insert into employee (id, name, birthday, email) values (38, 'Sukey Pollie', '1944-09-30', 'spollie11@unicef.org');
insert into employee (id, name, birthday, email) values (39, 'Kenton Orbell', '2019-04-05', 'korbell12@sohu.com');
insert into employee (id, name, birthday, email) values (40, 'Elli Shama', '2087-04-30', 'eshama13@businessweek.com');
insert into employee (id, name, birthday, email) values (41, 'Aurelea Ledington', null, 'aledington14@google.com.au');
insert into employee (id, name, birthday, email) values (42, 'Mellisa Benge', '1935-10-31', 'mbenge15@google.pl');
insert into employee (id, name, birthday, email) values (43, 'Siana Paolotto', '1919-05-07', 'spaolotto16@uol.com.br');
insert into employee (id, name, birthday, email) values (44, 'Rodge Blumire', '1925-05-13', 'rblumire17@uol.com.br');
insert into employee (id, name, birthday, email) values (45, 'Ariella Primrose', null, 'aprimrose18@addtoany.com');
insert into employee (id, name, birthday, email) values (46, 'Nike Vinall', '1903-03-30', 'nvinall19@instagram.com');
insert into employee (id, name, birthday, email) values (47, 'Kerry Davidy', null, 'kdavidy1a@economist.com');
insert into employee (id, name, birthday, email) values (48, 'Bride Stearndale', '2081-04-04', 'bstearndale1b@nydailynews.com');
insert into employee (id, name, birthday, email) values (49, 'Tedra Woollhead', '2097-05-14', 'twoollhead1c@4shared.com');
insert into employee (id, name, birthday, email) values (50, 'Alejandra Trye', '1971-03-29', 'atrye1d@soup.io');
```
---
3-Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
```javascript

```
---
4-Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
```javascript

```
---
