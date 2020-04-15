---
title: 'SQL: SQL a datové typy C++ (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: cffe44b832ac1eb28d368072b8f0e92ea9f57feb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374480"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: SQL a datové typy C++ (ODBC)

> [!NOTE]
> Tyto informace platí pro třídy Knihovny MFC ODBC. Pokud pracujete s třídami MFC DAO, přečtěte si téma "Porovnání Microsoft Jet Database Engine SQL a ANSI SQL" v nápovědě DAO.

Následující tabulka mapuje datové typy ANSI SQL na datové typy jazyka C++. Tím se rozšiřují informace o jazyce C uvedené v dodatku D *reference programátora* *ODBC SDK* na disku CD-ROM knihovny MSDN. Průvodci spravují většinu mapování datových typů za vás. Pokud nepoužijete průvodce, můžete použít informace o mapování, které vám pomohou napsat kód výměny polí ručně.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Datové typy ANSI SQL mapované na datové typy jazyka C++

|Datový typ ANSI SQL|Datový typ C++|
|------------------------|---------------------|
|**Char**|`CString`|
|**Desetinných**|`CString`1|
|**Smallint**|**int**|
|**Skutečné**|**float**|
|**Celé číslo**|**long**|
|**Float**|**double**|
|**Dvojité**|**double**|
|**Číselné**|`CString`1|
|**Varchar**|`CString`|
|**LONGVARCHAR (ALE)**|`CLongBinary`, `CString` 2.|
|**Bit**|**Bool**|
|**Tinyint**|**Bajt**|
|**Bigint**|`CString`1|
|**Binární**|`CByteArray`|
|**Varbinary**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3.|
|**Datum**|`CTime`, `CString`|
|**ČAS**|`CTime`, `CString`|
|**Časové razítko**|`CTime`, `CString`|

1. ANSI **DECIMAL** a `CString` **NUMERICKÁ** mapa, protože **SQL_C_CHAR** je výchozí typ přenosu ROZHRANÍ ODBC.

2. Data znaků nad 255 znaků jsou ve výchozím `CString`nastavení zkrácena při mapování na . Délku zkrácení můžete prodloužit explicitním nastavením argumentu *nMaxLength* . `RFX_Text`

3. Binární data nad 255 znaků jsou ve výchozím `CByteArray`nastavení zkrácena, když jsou mapována na . Délku zkrácení můžete prodloužit explicitním nastavením argumentu *nMaxLength* . `RFX_Binary`

Pokud nepoužíváte knihovnu kurzorů ROZHRANÍ ODBC, může dojít k potížím při pokusu o aktualizaci dvou nebo více dlouhých polí s proměnnou délkou pomocí ovladače MICROSOFT SQL Server ODBC a tříd y databáze Knihovny MFC ODBC. Typy ODBC, **SQL_LONGVARCHAR** a **SQL_LONGVARBINARY**, mapovat na text a obrázek typy SQL Server. A `CDBException` je vyvolána, pokud aktualizujete dvě nebo více dlouhých polí proměnné délky při stejném volání . `CRecordset::Update` Proto neaktualizujte více dlouhých `CRecordset::Update`sloupců současně s . Pomocí rozhraní ODBC API `SQLPutData`můžete aktualizovat více dlouhých sloupců současně . Můžete také použít knihovnu kurzorů ROZHRANÍ ODBC, ale to se nedoporučuje pro ovladače, jako je ovladač serveru SQL Server, které podporují kurzory a nepotřebují knihovnu kurzorů.

Pokud používáte knihovnu kurzorů ROZHRANÍ ODBC s třídami databáze Knihovny MFC ODBC a ovladačem `CRecordset::Update` ODBC serveru `CRecordset::Requery`Microsoft SQL Server, může dojít k **assert** spolu s `CDBException` voláním, které následuje po volání . Místo toho `CRecordset::Close` `CRecordset::Open` volejte `CRecordset::Requery`a spíše než . Jiné řešení není použití knihovny kurzorů ROZHRANÍ ODBC, protože SQL Server a ovladač SQL Server ODBC poskytují nativní podporu pro kurzory nativně a knihovna kurzorů ROZHRANÍ ODBC není potřeba.

## <a name="see-also"></a>Viz také

[SQL](../../data/odbc/sql.md)<br/>
[SQL: Přímá volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
