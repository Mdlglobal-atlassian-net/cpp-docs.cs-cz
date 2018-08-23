---
title: případ (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.case
dev_langs:
- C++
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 109ca7b833791aa982e17335801e8fe1fc538987
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606633"
---
# <a name="case-c"></a>case (C++)

Použít s [switch_type –](../windows/switch-type.md) atribut **sjednocení**.

## <a name="syntax"></a>Syntaxe

```cpp
[ case(
   value
) ]
```

#### <a name="parameters"></a>Parametry

*value*  
Možná vstupní hodnota pro kterou chcete poskytnout zpracování. Typ **hodnotu** může být jedna z následujících typů:

- `int`

- `char`

- `boolean`

- `enum`

nebo identifikátor takového typu.

## <a name="remarks"></a>Poznámky

**Případ** C++ atribut má stejné funkce jako **případ** atribut MIDL. Tento atribut se používá pouze pro [switch_type –](../windows/switch-type.md) atribut.

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

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Atributy třídy](../windows/class-attributes.md)  