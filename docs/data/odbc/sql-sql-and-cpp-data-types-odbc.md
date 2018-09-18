---
title: 'SQL: SQL a datové typy C++ (ODBC) | Dokumentace Microsoftu'
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
ms.openlocfilehash: c64abdee07a7fde3e92fb684a86a8e28e4a78ad7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029738"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: SQL a datové typy C++ (ODBC)

> [!NOTE]
>  Tyto informace platí pro třídy knihovny MFC rozhraní ODBC. Pokud pracujete s tříd DAO knihovny MFC, naleznete v tématu "Porovnání z Microsoft Jet databáze modul SQL a ANSI SQL" v nápovědě k DAO.  
  
Následující tabulka mapuje datové typy ANSI SQL datových typů jazyka C++. Informace o jazyce C uvedené v dodatku D o těchto argumentech *ODBC SDK* *referenční informace pro programátory* na disku CD knihovny MSDN. Průvodci spravovat většinu mapování datového typu pro vás. Pokud je velmi riskantní používat průvodce, můžete použít informace o mapování můžete napsat kód exchange pole ručně.  
  
### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Datové typy ANSI SQL mapované na datové typy C++  
  
|ANSI SQL datový typ|Datové typy jazyka C++|  
|------------------------|---------------------|  
|**CHAR**|`CString`|  
|**DECIMAL**|`CString` 1|  
|**SMALLINT**|**int**|  
|**REAL**|**float**|  
|**CELÉ ČÍSLO**|**long**|  
|**PLOVOUCÍ DESETINNOU ČÁRKOU**|**double**|  
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
|**ČAS**|`CTime`, `CString`|  
|**ČASOVÉ RAZÍTKO**|`CTime`, `CString`|  
  
1. ANSI **DESÍTKOVÉ** a **číselné** namapovat na `CString` protože **SQL_C_CHAR** je výchozí typ přenosu rozhraní ODBC.  
  
2. Znak data déle než 255 znaků je oříznutá. ve výchozím nastavení při mapování na `CString`. Zkrácení délky můžete rozšířit tak, že explicitně nastavíte *nMaxLength* argument `RFX_Text`.  
  
3. Binární data déle než 255 znaků je oříznutá. ve výchozím nastavení při mapování na `CByteArray`. Zkrácení délky můžete rozšířit tak, že explicitně nastavíte *nMaxLength* argument `RFX_Binary`.  
  
Pokud nepoužíváte knihovna kurzorů rozhraní ODBC, může dojít k potížím při pokusu o aktualizaci dvou nebo více polí dlouho proměnné délky, pomocí ovladače Microsoft SQL Server ODBC a databázové třídy MFC rozhraní ODBC. Typy rozhraní ODBC **SQL_LONGVARCHAR** a **SQL_LONGVARBINARY**, mapování na text a obrázek typy serveru SQL Server. A `CDBException` je vyvolána při aktualizaci dvou nebo více polí dlouho proměnné délky při volání stejné `CRecordset::Update`. Proto se neaktualizují více sloupců dlouhé současně s `CRecordset::Update`. Více dlouhých sloupců můžete aktualizovat současně s rozhraním ODBC API `SQLPutData`. Můžete také použít knihovna kurzorů rozhraní ODBC, ale to se nedoporučuje pro ovladače, jako jsou ovladače systému SQL Server, které podporují kurzory a není nutné knihovna kurzorů rozhraní.  
  
Pokud při použití knihovny kurzorů ODBC se databázové třídy MFC rozhraní ODBC a ovladači Microsoft SQL Server ODBC **ASSERT** může dojít k spolu s `CDBException` Pokud volání `CRecordset::Update` následuje volání `CRecordset::Requery`. Namísto toho zavolejte metodu `CRecordset::Close` a `CRecordset::Open` spíše než `CRecordset::Requery`. Jiným řešením je použití knihovny kurzorů ODBC, protože SQL Server a ovladač ODBC systému SQL Server poskytuje nativní podporu pro ukazatele nativně a není potřeba knihovna kurzorů rozhraní ODBC.  
  
## <a name="see-also"></a>Viz také  

[SQL](../../data/odbc/sql.md)<br/>
[SQL: Přímá volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)