---
title: duální (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dual
helpviewer_keywords:
- dual attribute
ms.assetid: 5d4a9069-d819-42cd-ba56-bbcda17157d9
ms.openlocfilehash: 8f02f6b69b31f10b41d5c920cfc2ad62dfa1cef2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023955"
---
# <a name="dual"></a>dual

Umístí rozhraní v souboru IDL jako duální rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
[dual]
```

## <a name="remarks"></a>Poznámky

Když **duální** C++ atribut předchází rozhraní, způsobí, že rozhraní být umístěny uvnitř bloku knihovny v souboru generovaného IDL.

## <a name="example"></a>Příklad

Následující kód je blok atribut, který používá **duální** před definice rozhraní:

```cpp
// cpp_attr_ref_dual.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), dual]

__interface IStatic : IDispatch
{
   HRESULT Func1(int i);
   [   propget,    id(1),    bindable,    displaybind,    defaultbind,    requestedit
   ]
   HRESULT P1([out, retval] long *nSize);
   [   propput,    id(1),    bindable,    displaybind,    defaultbind,    requestedit
   ]
   HRESULT P1([in] long nSize);
};

[cpp_quote("#include file.h")];
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**rozhraní**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|`dispinterface`|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy podle použití](attributes-by-usage.md)<br/>
[vlastní](custom-cpp.md)<br/>
[dispinterface](dispinterface.md)<br/>
[odkazy objektů](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)