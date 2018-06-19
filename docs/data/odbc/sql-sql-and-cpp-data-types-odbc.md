---
title: 'SQL: SQL a datové typy C++ (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6a137c4f648f518420d06f5cbd98ea189a030aee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095405"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: SQL a datové typy C++ (ODBC)
> [!NOTE]
>  Tyto informace platí pro třídy MFC rozhraní ODBC. Pokud pracujete s tříd MFC rozhraní DAO, naleznete v tématu "Porovnání z Microsoft Jet databáze stroj SQL a ANSI SQL" v nápovědě rozhraní DAO.  
  
 Následující tabulka mapuje ANSI SQL datové typy C++ datové typy. Rozšiřuje C jazyk informace uvedené v dodatku D *ODBC SDK* *referenční informace pro programátory* na disku CD knihovny MSDN. Průvodci spravovat většinu mapování datového typu pro vás. Pokud použijete průvodce, můžete informace o mapování můžete napsat kód exchange pole ručně.  
  
### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>ANSI SQL datové typy namapované na datové typy C++  
  
|ANSI SQL datový typ|C++ – datový typ|  
|------------------------|---------------------|  
|**CHAR –**|`CString`|  
|**DECIMAL**|`CString` 1|  
|**SMALLINT**|`int`|  
|`REAL`|**float**|  
|**CELÉ ČÍSLO**|**long**|  
|**PLOVOUCÍ DESETINNÁ ČÁRKA**|**double**|  
|**DOUBLE**|**double**|  
|**ČÍSELNÉ**|`CString` 1|  
|**VARCHAR**|`CString`|  
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|  
|**BIT**|**BOOL**|  
|**TINYINT**|**BAJTŮ**|  
|**BIGINT**|`CString` 1|  
|**BINÁRNÍ**|`CByteArray`|  
|**VARBINARY**|`CByteArray`|  
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|  
|**DATUM**|`CTime`, `CString`|  
|**ČAS**|**CTime –, CString**|  
|**ČASOVÉ RAZÍTKO**|**CTime –, CString**|  
  
 1. ANSI **DECIMAL** a **číselné** mapovat `CString` protože **SQL_C_CHAR** je výchozí typ přenosu rozhraní ODBC.  
  
 2. Textová data větší než 255 znaků se zkrátí ve výchozím nastavení při mapování na `CString`. Zkrácení délky můžete rozšířit explicitně nastavením `nMaxLength` argument `RFX_Text`.  
  
 3. Binární data větší než 255 znaků se zkrátí ve výchozím nastavení při mapování na `CByteArray`. Zkrácení délky můžete rozšířit explicitně nastavením `nMaxLength` argument `RFX_Binary`.  
  
 Pokud nepoužíváte knihovny kurzorů ODBC, může dojít k potížím při pokusu o aktualizaci dvou nebo více polí dlouho proměnné délky pomocí ovladače Microsoft SQL Server ODBC a databázové třídy MFC rozhraní ODBC. Typy rozhraní ODBC **SQL_LONGVARCHAR** a **SQL_LONGVARBINARY**, mapování na text nebo obrázky typy systému SQL Server. A `CDBException` je vyvolána při aktualizaci dvou nebo více polí dlouho proměnné délky na stejné volání `CRecordset::Update`. Proto nelze aktualizovat více dlouhých sloupců současně s `CRecordset::Update`. Můžete aktualizovat více dlouhých sloupců současně pomocí rozhraní API ODBC **SQLPutData**. Můžete taky knihovny kurzorů ODBC, ale to není doporučeno pro ovladače, jako je ovladač systému SQL Server, které podporují kurzory a není nutné knihovna kurzorů.  
  
 Pokud používáte knihovny kurzorů ODBC s databázové třídy MFC rozhraní ODBC a ovladač Microsoft SQL Server ODBC, **ASSERT** může dojít k spolu s `CDBException` Pokud volání `CRecordset::Update` a následně `CRecordset::Requery`. Místo toho volat `CRecordset::Close` a `CRecordset::Open` místo `CRecordset::Requery`. Jiné řešení je nepoužívat knihovny kurzorů ODBC, protože SQL Server a ovladač ODBC systému SQL Server poskytuje nativní podporu pro kurzory nativně a není potřeba knihovny kurzorů ODBC.  
  
## <a name="see-also"></a>Viz také  
 [SQL](../../data/odbc/sql.md)   
 [SQL: Přímá volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)