---
title: switch_type (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_type
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
ms.openlocfilehash: c3a4187c629238fa464a607c0b653f857fa44b6a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513960"
---
# <a name="switch_type"></a>switch_type

Určuje typ proměnné používané jako Discriminant sjednocení.

## <a name="syntax"></a>Syntaxe

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Parametry

*type*<br/>
Typ přepínače může být celé číslo, znak, logická hodnota nebo Výčtový typ.

## <a name="remarks"></a>Poznámky

Atribut **switch_type** C++ má stejné funkce jako atribut [switch_type](/windows/win32/Midl/switch-type) MIDL.

C++atributy nepodporují [zapouzdřené sjednocení](/windows/win32/Midl/encapsulated-unions). [](/windows/win32/Midl/nonencapsulated-unions) Nezapouzdřené sjednocení jsou podporovány pouze v následujícím tvaru:

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>Příklad

Podívejte se na příklad použití **switch_type**pomocí ukázkového [případu](case-cpp.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**definic**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[export](export.md)