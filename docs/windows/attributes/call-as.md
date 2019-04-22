---
title: call_as (C++ atributů COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: a0051cdca6673800b37d5733c0b849da24010fcb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023916"
---
# <a name="callas"></a>call_as

Umožňuje [místní](local-cpp.md) funkce mají být namapovány na vzdálenou funkci tak, aby při vzdálené funkce je volána, je vyvolána lokální funkce.

## <a name="syntax"></a>Syntaxe

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>Parametry

*– funkce*<br/>
Lokální funkce, kterou chcete volat při vyvolání vzdálenou funkci.

## <a name="remarks"></a>Poznámky

**Call_as** C++ atribut má stejné funkce jako [call_as](/windows/desktop/Midl/call-as) atribut MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak můžete **call_as** mapovat funkci nonremotable (`f1`) na funkci lze používat vzdáleně (`Remf1`):

```cpp
// cpp_attr_ref_call_as.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMInterface {
   [local] HRESULT f1 ( int i );
   [call_as(f1)] HRESULT Remf1 ( int i );
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Metoda rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádný|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[local](local-cpp.md)