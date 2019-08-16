---
title: helpstringdll (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringdll
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
ms.openlocfilehash: 8d6dddef666f074a57f54b8c9447847ff56d26fd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501479"
---
# <a name="helpstringdll"></a>helpstringdll

Určuje název knihovny DLL, která se má použít k provedení vyhledávání řetězců v dokumentu (lokalizace).

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstringdll("string") ]
```

### <a name="parameters"></a>Parametry

*string*<br/>
Knihovna DLL, která se má použít k provedení vyhledávání řetězce dokumentu

## <a name="remarks"></a>Poznámky

Atribut **helpstringdll** C++ má stejné funkce jako atribut [helpstringdll](/windows/win32/Midl/helpstringdll) MIDL.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **rozhraní**, metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)