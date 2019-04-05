---
title: db_column (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_column
helpviewer_keywords:
- db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
ms.openlocfilehash: e0e2c873452884275e97663ae2d9d6df2f790ffd
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024839"
---
# <a name="dbcolumn"></a>db_column

Připojí zadaný sloupec proměnné v dané sadě řádků.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_column(ordinal, dbtype, precision, scale, status, length) ]
```

#### <a name="parameters"></a>Parametry

*Pořadí*<br/>
Číslo pořadí sloupce (`DBCOLUMNINFO` pořadovém místě) nebo názvem sloupce (řetězec ANSI nebo Unicode) odpovídající pole v dané sadě řádků, ke kterému chcete svázat data. Pokud používáte čísla, můžete přeskočit po sobě jdoucích řadové číslovky (například: 1, 2, 3, 5). Název může obsahovat mezery, pokud podporuje zprostředkovatel OLE DB, který používáte. Například můžete použít některou z následujících formátů:

```cpp
[db_column("2")] TCHAR szCity[30];
[db_column(L"city_name")] TCHAR szCity[30];
```

*Hodnota DbType*<br/>
(Volitelné) OLE DB [indikátor typu](/previous-versions/windows/desktop/ms711251(v=vs.85)) pro vstupní sloupec.

*přesnost*<br/>
(Volitelné) Přesnost, který má být použit pro vstupní sloupec. Podrobnosti najdete v tématu Popis `bPrecision` elementu [DBBINDING struktura](/previous-versions/windows/desktop/ms716845(v=vs.85))

*měřítko*<br/>
(Volitelné) Škálování, která má být použit pro vstupní sloupec. Podrobnosti najdete v tématu Popis `bScale` elementu [DBBINDING struktura](/previous-versions/windows/desktop/ms716845(v=vs.85))

*stav*<br/>
(Volitelné) Členské proměnné používané pro udržení stavu daného sloupce. Stav označuje, zda je hodnota sloupce datovou hodnotu nebo jinou hodnotu, jako je NULL. Možné hodnoty najdete v části [stav](/previous-versions/windows/desktop/ms722617(v=vs.85)) v *OLE DB referenční informace pro programátory*.

*length*<br/>
(Volitelné) Členské proměnné používané pro udržení velikost sloupce v bajtech.

## <a name="remarks"></a>Poznámky

**db_column** váže sloupec tabulky zadané proměnné v dané sadě řádků. Vymezuje členská data, která se může účastnit OLE DB `IAccessor`– na základě vazby. Tento atribut nastaví mapy sloupce obvykle definovány pomocí makra příjemce technologie OLE DB [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../../data/oledb/end-column-map.md), a [COLUMN_ENTRY](../../data/oledb/column-entry.md). Tyto manipulovat s OLE DB [struktura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) svázat zadaný sloupec. Každý člen můžete označit **db_column** atribut budou zaměstnávat jedna položka v mapě sloupců ve formuláři položky sloupce. Proto volání tento atribut kde vložíte mapy sloupce, tedy ve třídě příkazu nebo tabulky.

Použití **db_column** ve spojení s buď [db_table](db-table.md) nebo [db_command](db-command.md) atributy.

Když příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor bude přejmenujte třídu na \_ *YourClassName*přístupový objekt, kde *YourClassName* je název, který jste zadali třídy a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd zobrazí se obě třídy.

Pro příklady tohoto atributu použijí v aplikaci, najdete v ukázkách [AtlAgent](https://github.com/Microsoft/VCSamples), a [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="example"></a>Příklad

Tato ukázka vytvoří vazbu sloupec v tabulce **dlouhé** datový člen a určuje pole Stav a délka.

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

Tato ukázka vytvoří vazbu čtyři sloupce **dlouhé**, řetězec znaků, časové razítko a `DB_NUMERIC` celé číslo, v uvedeném pořadí.

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **struktura**, člen, – metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádný|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[Atributy příjemce technologie OLE DB](ole-db-consumer-attributes.md)<br/>
[Atributy třídy](class-attributes.md)
