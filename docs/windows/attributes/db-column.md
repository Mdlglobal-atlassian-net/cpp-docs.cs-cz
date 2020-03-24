---
title: db_column (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_column
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
ms.openlocfilehash: 4ce57443480e35e7a4c7b9e872e41777662ddc20
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167287"
---
# <a name="db_column"></a>db_column

Vytvoří vazby zadaného sloupce k proměnné v sadě řádků.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Parametry

*řadový*<br/>
Pořadové číslo sloupce (`DBCOLUMNINFO` ordinální) nebo název sloupce (řetězec ANSI nebo Unicode) odpovídající poli v sadě řádků, ke které se mají navazovat data. Pokud používáte čísla, můžete vynechat po sobě jdoucí pořadová čísla (například: 1, 2, 3, 5). Název může obsahovat mezery, pokud ho poskytovatel OLE DB, který používáte, podporuje. Můžete například použít některý z následujících formátů:

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*DbType*<br/>
Volitelné [Indikátor typu](/previous-versions/windows/desktop/ms711251(v=vs.85)) OLE DB pro položku sloupce

*číslic*<br/>
Volitelné Přesnost, která má být použita pro položku sloupce. Podrobnosti najdete v popisu prvku `bPrecision` [struktury DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) .

*kapacity*<br/>
Volitelné Měřítko, které má být použito pro položku sloupce. Podrobnosti najdete v tématu Popis `bScale`ho prvku [struktury DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) .

*stav*<br/>
Volitelné Členská proměnná použitá pro uložení stavu tohoto sloupce. Stav označuje, zda je hodnota sloupce datovou hodnotou nebo jinou hodnotou, například NULL. Možné hodnoty najdete v tématu [stav](/previous-versions/windows/desktop/ms722617(v=vs.85)) v *referenci programátora OLE DB*.

*časový*<br/>
Volitelné Členská proměnná, která se používá k uchování velikosti sloupce v bajtech.

## <a name="remarks"></a>Poznámky

**db_column** váže zadaný sloupec tabulky na proměnnou v sadě řádků. Omezuje data členů, která se mohou účastnit OLE DB vazby na základě `IAccessor`. Tento atribut nastaví mapu sloupce obvykle definovaný pomocí OLE DBch maker příjemců [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../../data/oledb/end-column-map.md)a [COLUMN_ENTRY](../../data/oledb/column-entry.md). Tyto změny manipulují se OLE DB [strukturou DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) pro svázání zadaného sloupce. Každý člen, který označíte pomocí atributu **db_column** , bude zabírat jednu položku v mapě sloupce ve formě položky sloupce. Proto zavoláte tento atribut, kde byste měli umístit mapu sloupce, to znamená do třídy Command nebo Table.

Použijte **db_column** ve spojení s atributy [db_table](db-table.md) nebo [db_command](db-command.md) .

Pokud poskytovatel atributu příjemce použije tento atribut pro třídu, kompilátor přejmenuje třídu na \_přistupující objekt *YourClassName*, kde *YourClassName* je název, který jste přiřadili třídě, a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_přístupového objektu *YourClassName*.  V Zobrazení tříd se zobrazí obě třídy.

Příklad tohoto atributu, který se používá v aplikaci, najdete v tématu s více [čteními](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="example"></a>Příklad

Tato ukázka váže sloupec v tabulce k **dlouhému** datovému členu a určuje pole stav a délka.

```cpp
// db_column_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   DBSTATUS m_dwProductIDStatus;
   DBLENGTH m_dwProductIDLength;

   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;
};
```

## <a name="example"></a>Příklad

Tato ukázka váže čtyři sloupce na **dlouhý**řetězec znaků, časové razítko a `DB_NUMERIC` celé číslo v tomto pořadí.

```cpp
// db_column_2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_command(L"Select * from Products") ]
class CProducts {
   [db_column("1")] LONG m_OrderID;
   [db_column("2")] TCHAR m_CustomerID[6];
   [db_column("4")] DB_NUMERIC m_OrderDate;
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**, člen, metoda|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy příjemce technologie OLE DB](ole-db-consumer-attributes.md)<br/>
[Atributy třídy](class-attributes.md)
