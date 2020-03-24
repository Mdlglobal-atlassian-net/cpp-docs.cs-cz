---
title: db_table (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: 2b3be55a4ea118ef3441d3ea93f63e19ebdb3d79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167248"
---
# <a name="db_table"></a>db_table

Otevře tabulku OLE DB.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

### <a name="parameters"></a>Parametry

*db_table*<br/>
Řetězec určující název tabulky databáze (například "Products").

*Jméno*<br/>
Volitelné Název popisovače, který používáte pro práci s tabulkou. Tento parametr je nutné zadat, pokud chcete vrátit více než jeden řádek výsledků. **db_table** vygeneruje proměnnou se zadaným *názvem* , kterou lze použít k procházení sady řádků nebo provádění více dotazů na akce.

*source_name*<br/>
Volitelné `CSession` proměnnou nebo instanci třídy, pro kterou je použit atribut `db_source`, na kterém se příkaz spustí. Viz [db_source](db-source.md).

*HRESULT*<br/>
Volitelné Identifikuje proměnnou, která dostane hodnotu HRESULT tohoto databázového příkazu. Pokud proměnná neexistuje, bude automaticky vložena atributem.

## <a name="remarks"></a>Poznámky

**db_table** vytvoří objekt [CTable](../../data/oledb/ctable-class.md) , který je používán příjemcem OLE DB k otevření tabulky. Tento atribut lze použít pouze na úrovni třídy; Nemůžete ho použít jako vložený. Pomocí `db_column` navazovat sloupce tabulky na proměnné; Použijte `db_param` k vymezení (nastavení typu parametru a tak dále) parametrů.

Pokud poskytovatel atributu příjemce použije tento atribut pro třídu, kompilátor přejmenuje třídu na \_přistupující objekt *YourClassName*, kde *YourClassName* je název, který jste přiřadili třídě, a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_přístupového objektu *YourClassName*.  V Zobrazení tříd se zobrazí obě třídy.

## <a name="example"></a>Příklad

Následující příklad otevře tabulku Products pro použití v `CProducts`.

```cpp
// db_table.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_table(L"dbo.Products") ]
class CProducts {
   [ db_column("1") ] LONG m_ProductID;
};
```

Příklad tohoto atributu, který se používá v aplikaci, najdete v tématu s více [čteními](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy příjemce technologie OLE DB](ole-db-consumer-attributes.md)
