---
title: helpstringcontext – (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: a6df5b63291fbc54d6c12a116fccd8372e8ced9a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026107"
---
# <a name="helpstringcontext"></a>helpstringcontext

Určuje ID tématu nápovědy HLP nebo CHM souboru.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>Parametry

*contextID*<br/>
Identifikátor kontextu 32-bit nápovědy v **pomáhají** souboru.

## <a name="remarks"></a>Poznámky

**Helpstringcontext –** C++ atribut má stejné funkce jako [helpstringcontext –](/windows/desktop/Midl/helpstringcontext) ODL – atribut.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_helpstringcontext.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[   object, helpstring("help string"), helpstringcontext(1), uuid="11111111-1111-1111-1111-111111111111"
]
__interface IMyI
{
   HRESULT xx();
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **rozhraní**, rozhraní – metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[module](module-cpp.md)