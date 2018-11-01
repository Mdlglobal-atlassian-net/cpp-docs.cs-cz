---
title: případ (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: 1ed107b78ea5638d93a773e19de13b4c1fe1036c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648406"
---
# <a name="case-c"></a>case (C++)

Použít s [switch_type –](switch-type.md) atribut **sjednocení**.

## <a name="syntax"></a>Syntaxe

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>Parametry

*value*<br/>
Možná vstupní hodnota pro kterou chcete poskytnout zpracování. Typ **hodnotu** může být jedna z následujících typů:

- `int`

- `char`

- `boolean`

- `enum`

nebo identifikátor takového typu.

## <a name="remarks"></a>Poznámky

**Případ** C++ atribut má stejné funkce jako **případ** atribut MIDL. Tento atribut se používá pouze pro [switch_type –](switch-type.md) atribut.

## <a name="example"></a>Příklad

Následující kód ukazuje použití **případ** atribut:

```cpp
// cpp_attr_ref_case.cpp
// compile with: /LD
#include <unknwn.h>
[export]
struct SizedValue2 {
   [switch_type(char), switch_is(kind)] union {
      [case(1), string]
          wchar_t* wval;
      [default, string]
          char* val;
   };
    char kind;
};
[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Člen **třídy** nebo **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy třídy](class-attributes.md)