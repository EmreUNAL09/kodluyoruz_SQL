# Kodluyoruz_SQL
Patika SQL
## SQL Ödev 01 | WHERE ve Mantıksal Operatörler 
1- film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

SELECT title, description FROM film;

2-film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

SELECT * FROM film
WHERE length > 60 AND length < 75;



