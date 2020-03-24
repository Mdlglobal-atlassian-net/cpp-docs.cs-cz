---
title: Case (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: da72fff3bb600b5db2fba0ecdfe9c6a768836f3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167331"
---
# <a name="case-c"></a>case (C++)

Používá se s atributem [switch_type](switch-type.md) ve **sjednocení**.

## <a name="syntax"></a>Syntaxe

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>Parametry

*value*<br/>
Možná vstupní hodnota, pro kterou chcete poskytnout zpracování. Typ **hodnoty** může být jeden z následujících typů:

- `int`

- `char`

- `boolean`

- `enum`

nebo identifikátor takového typu.

## <a name="remarks"></a>Poznámky

Atribut **case** C++ má stejné funkce jako atribut **case** MIDL. Tento atribut se používá pouze s atributem [switch_type](switch-type.md) .

## <a name="example"></a>Příklad

Následující kód ukazuje použití atributu **case** :

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

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Člen **třídy** nebo **struktury**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy třídy](class-attributes.md)
