---
title: call_as (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: f36cf8d1be589cc614a6def583b00af00aabdb61
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501797"
---
# <a name="call_as"></a>call_as

Povoluje mapování [lokální](local-cpp.md) funkce na vzdálenou funkci, aby při volání vzdálené funkce byla vyvolána místní funkce.

## <a name="syntax"></a>Syntaxe

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>Parametry

*slouží*<br/>
Místní funkce, kterou chcete volat při vyvolání vzdálené funkce.

## <a name="remarks"></a>Poznámky

Atribut **call_as** C++ má stejné funkce jako atribut [call_as](/windows/win32/Midl/call-as) MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak můžete použít **call_as** k namapování nevzdáleně spustitelné funkce (`f1`) na funkci vzdáleně (`Remf1`):

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

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[local](local-cpp.md)