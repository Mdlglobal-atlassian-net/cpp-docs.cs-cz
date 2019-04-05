---
title: db_source (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_source
helpviewer_keywords:
- db_source attribute
ms.assetid: 0ec8bbf7-ade2-4899-bf4c-8608b92779bc
ms.openlocfilehash: 884cab78d64c20bef00958f0cc0319281fd69921
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026328"
---
# <a name="dbsource"></a>db_source

Vytvoří připojení ke zdroji dat.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_source(db_source, name, hresult) ]
```

### <a name="parameters"></a>Parametry

*db_source*<br/>
Připojovací řetězec použitý pro připojení ke zdroji dat. Formát připojovacího řetězce, naleznete v tématu [připojovací řetězce a propojení dat](/previous-versions/windows/desktop/ms718376(v=vs.85)) v Microsoft Data Access Components (MDAC) SDK.

*name*<br/>
(Volitelné) Při použití **db_source** na třídu, *název* je instance objektu zdroje dat, který má **db_source** byt aplikovaný atribut (viz Příklad 1). Při použití **db_source** vložené v implementaci metody, *název* je proměnná (místní počítač do metody), který slouží pro přístup k datům zdroje (viz příklad 2). To předat *název* k *source_name* parametr `db_command` ke zdroji dat pomocí příkazu.

*Hodnota HRESULT*<br/>
(Volitelné) Určuje proměnné, která se zobrazí hodnota HRESULT tohoto databázového příkazu. Pokud proměnná neexistuje, ji budou automaticky vloženy atribut.

## <a name="remarks"></a>Poznámky

**db_source** vytvoří [CDataSource](../../data/oledb/cdatasource-class.md) a [CSession](../../data/oledb/csession-class.md) objekt, což dohromady představují připojení ke zdroji dat příjemce technologie OLE DB.

Při použití **db_source** na třídu, `CSession` objekt se stane členem třídy.

Při použití **db_source** v metodě, se spustí vloženého kódu v rámci oboru metody a `CSession` jako místní proměnná je vytvořen objekt.

**db_source** přidá vlastnosti zdroje dat pro třídu nebo v rámci metody. Používá se ve spojení s `db_command` (které trvá *db_source* *název* parametr jako jeho *source_name* parametr).

Když příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor bude přejmenujte třídu na \_ *YourClassName*přístupový objekt, kde *YourClassName* je název, který jste zadali třídy a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd zobrazí se obě třídy.

Příklad tohoto atributu použijí v aplikaci, najdete v ukázkách [AtlAgent](https://github.com/Microsoft/VCSamples) a [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="example"></a>Příklad

Tato ukázka volá **db_source** třídy pro vytvoření připojení ke zdroji dat `ds` pomocí databáze Northwind. `ds` je obslužnou rutinu pro zdroj dat, který je možné interně na `CMyCommand` třídy.

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **struktura**, člen, metoda, místní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádný|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[Atributy příjemce technologie OLE DB](ole-db-consumer-attributes.md)
