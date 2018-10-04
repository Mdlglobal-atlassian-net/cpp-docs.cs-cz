---
title: db_accessor (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_accessor
dev_langs:
- C++
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 60cfe67acb2841c3cf5bf3cc371b0f70c7fcf72b
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789370"
---
# <a name="dbaccessor"></a>db_accessor

Skupiny `db_column` atributy, které jsou součástí `IAccessor`– na základě vazby.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>Parametry

*počet*<br/>
Určuje, kolik přístupového objektu (založený na nule celočíselný index). Je nutné zadat přístupový objekt čísla ve vzestupném pořadí podle celých čísel nebo definované hodnoty.

*auto*<br/>
Logická hodnota určující, zda přistupujícím objektu je automaticky načte (TRUE) nebo nebyla načtena (FALSE).

## <a name="remarks"></a>Poznámky

**db_accessor** definuje základní přístupový objekt OLE DB pro následné `db_column` a `db_param` atributů v rámci stejné třídy nebo funkce. **db_accessor** je použitelný na úrovni člena a používá se ke skupině `db_column` atributy, které jsou součástí technologie OLE DB `IAccessor`– na základě vazby. Používá se ve spojení s buď `db_table` nebo `db_command` atributy. Volání tohoto atributu je podobná volání [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

**db_accessor** generuje sadu řádků a sváže s odpovídající přístupového objektu map. Pokud není volána **db_accessor**, bude vygenerována automaticky přistupujícího objektu 0 a všechny vazby sloupce se namapují na tento blok přistupující objekt.

**db_accessor** skupiny databáze vazeb sloupců do jednoho nebo více přístupových objektů. Informace o scénářích, ve kterých je potřeba použít několik přístupových objektů, naleznete v tématu [použití více přístupových objektů pro sadu řádků](../../data/oledb/using-multiple-accessors-on-a-rowset.md). Viz také "Uživatel záznam podporu pro několik přístupových objektů" v [uživatelských záznamů](../../data/oledb/user-records.md).

Když příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor bude přejmenujte třídu na \_ *YourClassName*přístupový objekt, kde *YourClassName* je název, který jste zadali třídy a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd zobrazí se obě třídy.

## <a name="example"></a>Příklad

Následující příklad používá **db_accessor** do skupiny sloupců v tabulce objednávky z databáze Northwind do dvou přístupových objektů. Přistupující objekt 0 je automatické přistupující objekt a přístupového objektu 1 není.

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Bloky atributů|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy příjemce technologie OLE DB](ole-db-consumer-attributes.md)  