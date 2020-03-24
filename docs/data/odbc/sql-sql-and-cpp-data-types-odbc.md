---
title: 'SQL: SQL a datové typy C++ (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 1c1ce908b5c8d345906d49adc79e322225ed49f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212612"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: SQL a datové typy C++ (ODBC)

> [!NOTE]
>  Tyto informace se vztahují na třídy knihovny MFC rozhraní ODBC. Pokud pracujete s třídami knihovny MFC DAO, přečtěte si téma "porovnání databáze Microsoft Jet Database Engine SQL a ANSI SQL" v nápovědě rozhraní DAO.

Následující tabulka mapuje datové typy ANSI SQL na C++ datové typy. Tím se rozšiřují informace o jazyce C uvedené v příloze D *Referenční příručce programátora* *sady ODBC SDK* na disku CD knihovny MSDN. Průvodci spravují většinu mapování datových typů za vás. Pokud Průvodce nepoužíváte, můžete použít informace o mapování, které vám pomohou psát kód výměny pole ručně.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Datové typy ANSI SQL mapované na C++ datové typy

|ANSI – datový typ SQL|C++datový typ|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**NOTACI**|`CString` 1|
|**SMALLINT**|**int**|
|**NEMOVITOSTÍ**|**float**|
|**ČÍSLA**|**long**|
|**Plovák**|**double**|
|**KLEPAT**|**double**|
|**ČÍSELNÉ**|`CString` 1|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary``CString` 2|
|**40BITOVÉHO**|**LOGICK**|
|**TINYINT**|**BYTOVÉ**|
|**BIGINT**|`CString` 1|
|**TVARU**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary``CByteArray` 3|
|**DATE** (Datum)|`CTime`, `CString`|
|**ČAS**|`CTime`, `CString`|
|**ČASOVÉ razítko**|`CTime`, `CString`|

1. **Desítková** a **Číselná** mapa ANSI pro `CString`, protože **SQL_C_CHAR** je výchozí typ přenosu ODBC.

2. Data znaků přesahující 255 znaků se při mapování na `CString`ve výchozím nastavení zkrátí. Délku zkrácení můžete zvětšit explicitním nastavením argumentu *nMaxLength* `RFX_Text`.

3. Binární data přesahující 255 znaků se při mapování na `CByteArray`ve výchozím nastavení zkrátí. Délku zkrácení můžete zvětšit explicitním nastavením argumentu *nMaxLength* `RFX_Binary`.

Pokud nepoužíváte knihovnu kurzorů rozhraní ODBC, může dojít k potížím při pokusu o aktualizaci dvou nebo více polí s proměnlivou délkou pomocí Microsoft SQL Server ovladače rozhraní ODBC a databázových tříd knihovny MFC rozhraní ODBC. Typy rozhraní ODBC, **SQL_LONGVARCHAR** a **SQL_LONGVARBINARY**, se mapují na typy textu a obrázků SQL Server. `CDBException` je vyvolána, pokud provedete aktualizaci dvou nebo více polí s proměnnou délkou na stejném volání `CRecordset::Update`. Proto neaktualizujte více dlouhých sloupců současně pomocí `CRecordset::Update`. Pomocí `SQLPutData`rozhraní ODBC API můžete aktualizovat víc dlouhých sloupců současně. Můžete také použít knihovnu kurzorů ODBC, ale nedoporučuje se pro ovladače, jako je například ovladač SQL Server, který podporuje kurzory a nepotřebujete knihovnu kurzorů.

Pokud používáte knihovnu kurzorů ODBC s databázovými třídami MFC rozhraní ODBC a ovladačem Microsoft SQL Server ODBC, může dojít k **vyhodnocení** společně s `CDBException`, pokud volání `CRecordset::Update` sleduje volání `CRecordset::Requery`. Místo toho zavolejte `CRecordset::Close` a `CRecordset::Open` místo `CRecordset::Requery`. Dalším řešením není použití knihovny kurzorů ODBC, protože SQL Server a ovladač SQL Server ODBC poskytují nativní podporu pro kurzory nativně a knihovna kurzorů rozhraní ODBC není potřeba.

## <a name="see-also"></a>Viz také

[SQL](../../data/odbc/sql.md)<br/>
[SQL: Přímá volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
