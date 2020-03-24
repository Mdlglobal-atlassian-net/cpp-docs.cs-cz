---
title: agregovatelné (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregatable
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
ms.openlocfilehash: d929543f699dcd20471ff9a9b45f54119f82a40a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168522"
---
# <a name="aggregatable"></a>aggregatable

Označuje, že třída podporuje agregaci.

## <a name="syntax"></a>Syntaxe

```cpp
[ aggregatable(value) ]
```

### <a name="parameters"></a>Parametry

*value*<br/>
Volitelné Parametr, který určuje, kdy může být objekt modelu COM agregován:

- `never` objekt COM nelze agregovat.

- `allowed` objekt COM lze vytvořit přímo nebo jej lze agregovat. Toto nastavení je výchozí.

- `always` objekt COM nelze vytvořit přímo a lze jej agregovat pouze. Když zavoláte `CoCreateInstance` pro tento objekt, je nutné zadat rozhraní agregace `IUnknown` objektu (řízení `IUnknown`).

## <a name="remarks"></a>Poznámky

**Agregovatelné** C++ atributy mají stejné funkce jako [agregovatelné](/windows/win32/Midl/aggregatable) atributy MIDL. To znamená, že kompilátor projde **agregovatelné** atributy až do generovaného souboru IDL.

Tento atribut vyžaduje, aby atribut [Coclass](coclass.md), [ProgID](progid.md)nebo [vi_progid](vi-progid.md) (nebo jiný atribut, který implikuje jednu z nich) byl také použit pro stejný prvek. Je-li použit libovolný atribut, budou automaticky použity ostatní dva. Například pokud je použita `progid`, jsou použita také `vi_progid` a `coclass`.

### <a name="atl-projects"></a>Projekty ATL

Pokud se tento atribut používá v rámci projektu, který používá ATL, chování atributu se změní. Kromě dříve popsaného chování atribut také přidá do cílové třídy jedno z následujících maker:

|Hodnota parametru|Vložené makro|
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

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Jednu nebo více následujících možností: `coclass`, `progid`nebo `vi_progid`.|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Agregace](/windows/win32/com/aggregation)
