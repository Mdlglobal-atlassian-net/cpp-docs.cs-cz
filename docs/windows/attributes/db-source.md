---
title: db_source (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: 6346a8d6f60313dc17bbcbad062aa888857f0b67
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167274"
---
# <a name="db_source"></a>db_source

Vytvoří připojení ke zdroji dat.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>Parametry

*db_source*<br/>
Připojovací řetězec použitý k připojení ke zdroji dat. Formát připojovacího řetězce najdete v tématu [připojovací řetězce a datové odkazy](/previous-versions/windows/desktop/ms718376(v=vs.85)) v sadě MDAC (Microsoft Data Access Components).

*Jméno*<br/>
Volitelné Použijete-li **db_source** ve třídě, *název* je instancí objektu zdroje dat, u kterého je použit atribut **db_source** (viz příklad 1). Použijete-li **db_source** vložené v implementaci metody, *název* je proměnná (místní k metodě), kterou lze použít pro přístup ke zdroji dat (viz příklad 2). Tento *název* předáte do parametru *source_name* `db_command` k přidružení zdroje dat k příkazu.

*HRESULT*<br/>
Volitelné Identifikuje proměnnou, která dostane hodnotu HRESULT tohoto databázového příkazu. Pokud proměnná neexistuje, bude automaticky vložena atributem.

## <a name="remarks"></a>Poznámky

**db_source** vytvoří objekt [CDataSource](../../data/oledb/cdatasource-class.md) a objekt [CSession](../../data/oledb/csession-class.md) , který společně představuje připojení ke zdroji dat OLE DB spotřebitele.

Použijete-li **db_source** pro třídu, objekt `CSession` se stal členem třídy.

Při použití **db_source** v metodě se vložený kód provede v rámci rozsahu metody a objekt `CSession` je vytvořen jako místní proměnná.

**db_source** přidá vlastnosti zdroje dat do třídy nebo v rámci metody. Používá se ve spojení s `db_command` (který přebírá parametr *db_source* *názvu* db_source jako jeho parametr *source_name* ).

Pokud poskytovatel atributu příjemce použije tento atribut pro třídu, kompilátor přejmenuje třídu na \_přistupující objekt *YourClassName*, kde *YourClassName* je název, který jste přiřadili třídě, a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_přístupového objektu *YourClassName*.  V Zobrazení tříd se zobrazí obě třídy.

Příklad tohoto atributu, který se používá v aplikaci, najdete v tématu s více [čteními](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer).

## <a name="example"></a>Příklad

Tato ukázka volá **db_source** pro třídu pro vytvoření připojení ke zdroji dat `ds` pomocí databáze Northwind. `ds` je popisovač pro zdroj dat, který lze použít interně pro třídu `CMyCommand`.

```cpp
// db_source_1.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[
  db_source(L"my_connection_string", name="ds"),
  db_command(L"select * from Products")
]
class CMyCommand {};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**, člen, metoda, místní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy příjemce technologie OLE DB](ole-db-consumer-attributes.md)
