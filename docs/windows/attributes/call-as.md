---
title: call_as (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: 755741faec6c0ba702d372ca8dee486edcb72ef3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167329"
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

Následující kód ukazuje, jak můžete použít **call_as** k namapování nevzdáleně funkce (`f1`) na vzdáleně funkčně (`Remf1`):

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

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[local](local-cpp.md)
