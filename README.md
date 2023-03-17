# SQL-w-120-min
Zadania *SQL w 120 min*

```SQL
/* Zadania SQL w 120 min - https://www.kursysql.pl/sql-w-120-minut/zadania/ */
/* AdventureWorks sample databases - https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16&tabs=ssms */


USE AdventureWorks2014

/* Zad. 1. Wyswietl wszystkie produkty (tabela Production.Product) koloru czarnego, posortowane malejaco wg ceny (ListPrice). */

SELECT [Production].[Product].[Name]
FROM [Production].[Product]
WHERE [Production].[Product].[Color] = 'BLACK'
ORDER BY [Production].[Product].[ListPrice];


/* Zad. 2. Wyswietl wszystkie produkty koloru czerwonego i niebieskiego, ktorych nazwa zaczyna sie na 'L', posortowane wg rozmiaru malejaco i ceny rosnaco. */

SELECT [Production].[Product].[Name], [Production].[Product].[Color]
FROM [Production].[Product]
WHERE [Production].[Product].[Color] IN ('RED', 'BLUE') AND [Production].[Product].[Name] LIKE 'L%'
ORDER BY [Production].[Product].[Size] DESC, [Production].[Product].[ListPrice];


/* Zad. 3. Wyswietl wiersze z tabeli Sales.SalesTerritory, przypisane do Europy, posortowane wg nazwy kraju. */

SELECT *
FROM [Sales].[SalesTerritory]
WHERE [Sales].[SalesTerritory].[Group] = 'EUROPE'
ORDER BY [Sales].[SalesTerritory].[Name];


/* Zad. 4. Wyswietl wiersze z tabeli Sales.SalesTerrytory, posortowane wg grupy regionow (kontynentow) malejaco i nazwy kraju rosnaco. */

SELECT *
FROM [Sales].[SalesTerritory]
ORDER BY [Sales].[SalesTerritory].[GROUP] DESC, [Sales].[SalesTerritory].[Name];


/* Zad. 5. Wyswietl zamowienia przypisane do obszarow o identyfikatorach 7, 8, 9. */

SELECT *
FROM [Sales].[SalesOrderHeader]
WHERE [Sales].[SalesOrderHeader].[TerritoryID] IN (7, 8, 9);


/* Zad. 6. Wyswietl 10 ostatnich zamowien przypisanych do obszarow o identyfikatorach 7, 8, 9 o wartosci
		   (kolumna SubTotal) mniejszej niz 100, posortowanych wg daty. */

SELECT TOP (10)
[SalesOrderID],[RevisionNumber],[OrderDate],[DueDate],[ShipDate],[Status],[OnlineOrderFlag],[SalesOrderNumber] ,[PurchaseOrderNumber],[SalesPersonID],[TerritoryID],[BillToAddressID] ,[ShipToAddressID] ,[CreditCardID],[CreditCardApprovalCode],[CurrencyRateID],[SubTotal],[TaxAmt],[Freight],[TotalDue],[Comment],[rowguid],[ModifiedDate]
FROM [Sales].[SalesOrderHeader]
WHERE [Sales].[SalesOrderHeader].[TerritoryID] IN (7, 8, 9) AND [Sales].[SalesOrderHeader].[SubTotal] < 10
ORDER BY [Sales].[SalesOrderHeader].[OrderDate];


/* Zad. 7. Wyswietl 10 zamowien na najwyzsza kwote, przypisanych do obszaru 7. */

SELECT TOP (10)
[SalesOrderID],[RevisionNumber],[OrderDate],[DueDate],[ShipDate],[Status],[OnlineOrderFlag],[SalesOrderNumber] ,[PurchaseOrderNumber],[SalesPersonID],[TerritoryID],[BillToAddressID] ,[ShipToAddressID] ,[CreditCardID],[CreditCardApprovalCode],[CurrencyRateID],[SubTotal],[TaxAmt],[Freight],[TotalDue],[Comment],[rowguid],[ModifiedDate]
FROM [Sales].[SalesOrderHeader]
WHERE [Sales].[SalesOrderHeader].[TerritoryID] = 7
ORDER BY [Sales].[SalesOrderHeader].[TotalDue];


/* Zad. 8. Wyswietl zamowienia przypisane do obszaru 7, bez przypisanego numeru karty kredytowej (kolumna CreditCardID). */

SELECT *
FROM [Sales].[SalesOrderHeader]
WHERE [Sales].[SalesOrderHeader].[TerritoryID] = 7 AND [Sales].[SalesOrderHeader].[CreditCardID] IS NULL;


/* Zad. 9. Wyswietl zamowienia przypisane do obszaru 7, z przypisanym numerem karty kredytowej. */

SELECT *
FROM [Sales].[SalesOrderHeader]
WHERE [Sales].[SalesOrderHeader].[TerritoryID] = 7 AND [Sales].[SalesOrderHeader].[CreditCardID] IS NOT NULL;


/* Zad. 10. Wyswietl zamowienia z roku 2011, posortuj wg daty zamowienia. */

SELECT *
FROM [Sales].[SalesOrderHeader]
WHERE [Sales].[SalesOrderHeader].[OrderDate] BETWEEN '2011-01-01' AND '2011-12-31'
ORDER BY [Sales].[SalesOrderHeader].[OrderDate];

```
