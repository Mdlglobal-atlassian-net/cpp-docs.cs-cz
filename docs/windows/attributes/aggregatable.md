---
title: Aggregatable (C++ COM – atribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregatable
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
ms.openlocfilehash: 8d5ceb46a124db8c0082495d48e6ee0e21655422
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390994"
---
# <a name="aggregatable"></a>aggregatable

Označuje, že třída podporuje agregaci.

## <a name="syntax"></a>Syntaxe

```cpp
[ aggregatable(value) ]
```

### <a name="parameters"></a>Parametry

*value*<br/>
(Volitelné) Parametr označuje, kdy se dají agregovat objektu COM:

- `never` Objekt COM nemůže být agregován.

- `allowed` Objekt modelu COM lze vytvořit přímo, nebo se dají agregovat. Toto nastavení je výchozí.

- `always` Objekt modelu COM nelze vytvořit přímo a pouze se dají agregovat. Při volání `CoCreateInstance` pro tento objekt, je nutné zadat objekt agregovat `IUnknown` rozhraní (řízení `IUnknown`).

## <a name="remarks"></a>Poznámky

**Agregovatelné** C++ atribut má stejné funkce jako [agregovatelné](/windows/desktop/Midl/aggregatable) atribut MIDL. To znamená, že kompilátor předá **agregovatelné** atribut prostřednictvím souboru generovaného IDL.

Tento atribut vyžaduje, aby [coclass](coclass.md), [progid](progid.md), nebo [vi_progid –](vi-progid.md) atribut (nebo jiný atribut, který zahrnuje jednu z těchto) také použít u stejného elementu. Pokud se používá jakékoli jeden atribut, další dvě automaticky použity. Například pokud `progid` se použije, `vi_progid` a `coclass` jsou použita také.

### <a name="atl-projects"></a>Projekty knihovny ATL

Pokud tento atribut se používá v rámci projektu, který používá knihovny ATL, chování změny atributů. Kromě výše popsaným chování atribut přidá také jednu z následujících makra do cílové třídy:

|Hodnota parametru|Vložené: – makro|
|---------------------|--------------------|
|`Never`|[DECLARE_NOT_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|
|`Allowed`|[DECLARE_POLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|
|`Always`|[DECLARE_ONLY_AGGREGATABLE](../../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_aggregatable.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="MyModule")];

[ coclass, aggregatable(allowed),
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]
class CMyClass {};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Jeden nebo více z následujících akcí: `coclass`, `progid`, nebo `vi_progid`.|
|**Neplatné atributy**|Žádný|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Agregace](/windows/desktop/com/aggregation)