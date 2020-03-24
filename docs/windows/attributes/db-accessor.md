---
title: db_accessor (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: 1e9725dad39974b828d87bd8b4cdeac623f4e12f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214861"
---
# <a name="db_accessor"></a>db_accessor

Skupiny `db_column` atributy, které se účastní vazby založené na `IAccessor`.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>Parametry

*počet*<br/>
Určuje číslo přistupujícího objektu (celočíselný index založený na nule). Je nutné zadat přístupová čísla ve vzestupném pořadí, pomocí celých čísel nebo definovaných hodnot.

*auto*<br/>
Logická hodnota, která určuje, zda je přistupující objekt automaticky načten (TRUE) nebo nenačten (FALSE).

## <a name="remarks"></a>Poznámky

**db_accessor** definuje podkladový přístupový objekt OLE DB pro následné `db_column` a `db_param` atributy v rámci stejné třídy nebo funkce. **db_accessor** lze použít na úrovni členů a používá se k seskupení `db_column` atributů, které se účastní OLE DB `IAccessor`vazbách. Používá se ve spojení s atributy `db_table` nebo `db_command`. Volání tohoto atributu je podobné volání [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) maker.

**db_accessor** generuje sadu řádků a váže ji k odpovídajícím mapám přistupujícímu objektu. Pokud nevoláte **db_accessor**, přistupující objekt 0 se automaticky vygeneruje a všechny vazby sloupce budou namapovány na tento přístupový blok.

**db_accessor** seskupuje vazby sloupců databáze do jednoho nebo více přístupových objektů. Diskuzi o scénářích, ve kterých potřebujete použít více přístupových objektů, najdete v tématu [použití více přístupových objektů pro sadu řádků](../../data/oledb/using-multiple-accessors-on-a-rowset.md). Viz také "podpora uživatelského záznamu pro více přístupových objektů" v [záznamech uživatelů](../../data/oledb/user-records.md).

Pokud poskytovatel atributu příjemce použije tento atribut pro třídu, kompilátor přejmenuje třídu na \_přistupující objekt *YourClassName*, kde *YourClassName* je název, který jste přiřadili třídě, a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_přístupového objektu *YourClassName*.  V Zobrazení tříd se zobrazí obě třídy.

## <a name="example"></a>Příklad

Následující příklad používá **db_accessor** k seskupení sloupců v tabulce Orders z databáze Northwind do dvou přístupových objektů. Přistupující objekt 0 je automatický přistupující objekt a přístupový objekt 1 není.

```cpp
// cpp_attr_ref_db_accessor.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>

[ db_command(L"SELECT LastName, FirstName FROM Orders") ]
class CEmployees {
public:
   [ db_accessor(0, TRUE) ];
   [ db_column("1") ] LONG m_OrderID;
   [ db_column("2") ] TCHAR m_CustomerID[6];
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;

   [ db_accessor(1, FALSE) ];
   [ db_column("8") ] CURRENCY m_Freight;
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Bloky atributů|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy příjemce technologie OLE DB](ole-db-consumer-attributes.md)
