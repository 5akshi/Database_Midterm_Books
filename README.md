# Database_Midterm_Books


## Blocks of code

```
###Power Writers
SELECT authorId, authorName
FROM Authors
WHERE (SELECT COUNT(*) FROM Books WHERE Books.authorId = Authors.authorId AND publicationDate >= CURRENT_DATE - INTERVAL '6 years') >=1;


###Loyal Customers
SELECT 'Most Loyal Customers are:';

SELECT customerid, customername, totalamountspent
FROM Customers
WHERE totalamountspent >= 2500 AND registrationdate >= CURRENT_DATE - INTERVAL '5 year'
Order by 3 desc;


###Well Reviewed Books
SELECT 'Top 5 most popular books are:';

SELECT bookid, booktitle, bookaveragerating
FROM Books
WHERE bookaveragerating > (SELECT AVG(bookaveragerating) FROM Books)
order by 3 desc
Limit 5;


###Most Popular Genre by Sales
SELECT 'The highest selling book genre is: '|| bookgenre as Book_Genre,count(1)
FROM Books
JOIN Purchases ON Books.bookid = Purchases.bookid
GROUP BY bookgenre
ORDER BY SUM(bookprice) DESC 
LIMIT 1;

###10 Most Recent Reviews
SELECT 'Most recent 10 revuews are:';

SELECT reviewid, customerid, bookid, reviewrating, reviewcomment, reviewdate
FROM Reviews
ORDER BY reviewdate DESC
LIMIT 10;
}
```
