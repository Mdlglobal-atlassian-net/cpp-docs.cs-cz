---
title: řetězec (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.string
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
ms.openlocfilehash: e1b528fb922a15655de403c6099ee1d36e2fb3de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407273"
---
# <a name="string-c"></a>string (C++)

Označuje, že jednorozměrné pole **char**, **wchar_t**, `byte` (nebo obdobných) pole nebo ukazatel na takové pole musí být považované za řetězec.

## <a name="syntax"></a>Syntaxe

```cpp
[string]
```

## <a name="remarks"></a>Poznámky

**Řetězec** C++ atribut má stejné funkce jako [řetězec](/windows/desktop/Midl/string) atribut MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak používat **řetězec** na rozhraní a definice typu:

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Pole nebo ukazatel pole, rozhraní parametrů, metody rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy pole](array-attributes.md)<br/>
[export](export.md)