---
title: helpstringdll – (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringdll
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
ms.openlocfilehash: 17e70a54024b8e5a3ab29e2420f60fbf3eec08a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677237"
---
# <a name="helpstringdll"></a>helpstringdll

Určuje název knihovny DLL použít k provádění vyhledání řetězce dokumentu (lokalizace).

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstringdll("string") ]
```

### <a name="parameters"></a>Parametry

*string*<br/>
Knihovny DLL použít k provádění vyhledání řetězce dokumentu.

## <a name="remarks"></a>Poznámky

**Helpstringdll –** C++ atribut má stejné funkce jako [helpstringdll –](/windows/desktop/Midl/helpstringdll) atribut MIDL.

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **rozhraní**, rozhraní – metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)