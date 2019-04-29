---
title: switch_type – (C++ atributů COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_type
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
ms.openlocfilehash: b461769d3d988efae0be7380e1e0112e3f3cf801
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407117"
---
# <a name="switchtype"></a>switch_type

Určuje typ proměnné použité jako sjednocení discriminant.

## <a name="syntax"></a>Syntaxe

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Parametry

*type*<br/>
Typ přepínače může být typ integer, znak, logická hodnota nebo výčet.

## <a name="remarks"></a>Poznámky

**Switch_type –** C++ atribut má stejné funkce jako [switch_type –](/windows/desktop/Midl/switch-type) atribut MIDL.

Atributy C++ nepodporuje [zapouzdřené sjednocení](/windows/desktop/Midl/encapsulated-unions). [Nonencapsulated sjednocení](/windows/desktop/Midl/nonencapsulated-unions) jsou podporovány pouze v následujícím tvaru:

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

Najdete v článku [případ](case-cpp.md) příklad ukázkový používání **switch_type –**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Definice TypeDef**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádný|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[export](export.md)