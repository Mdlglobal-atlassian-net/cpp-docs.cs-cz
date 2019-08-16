---
title: String (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: 978f1f546c0df8de4ff167ddf5ddf724feb31b6e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514016"
---
# <a name="string-c"></a>string (C++)

Označuje, že jednorozměrné pole **char**, **wchar_t**, `byte` (nebo ekvivalentní) nebo ukazatel na takové pole musí být považováno za řetězec.

## <a name="syntax"></a>Syntaxe

```cpp
[string]
```

## <a name="remarks"></a>Poznámky

**Řetězcový** C++ atribut má stejné funkce jako atribut [String](/windows/win32/Midl/string) MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak použít **řetězec** v rozhraní a na typedef:

```cpp
// cpp_attr_ref_string.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export, string] typedef char a[21];
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   [id(1)] HRESULT Method3([in, string] char *pC);
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Pole nebo ukazatel na pole, parametr rozhraní, metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy pole](array-attributes.md)<br/>
[export](export.md)