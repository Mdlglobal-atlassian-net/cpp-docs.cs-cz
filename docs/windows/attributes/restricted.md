---
title: omezenoC++ (atribut com)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 01dabcd15eb1a14734c16b9e54c0ab2e030d0479
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514060"
---
# <a name="restricted"></a>restricted

Určuje, že člen modulu, rozhraní nebo odesílajícího rozhraní nelze volat libovolně.

## <a name="syntax"></a>Syntaxe

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>Parametry

*Interfaces*<br/>
Jedno nebo více rozhraní, která nesmí být volána libovolně v objektu COM. Tento parametr je platný pouze při použití pro třídu.

## <a name="remarks"></a>Poznámky

Atribut **s omezením** C++ má stejné funkce jako atribut [s omezením](/windows/win32/Midl/restricted) MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak použít atribut **s omezením** :

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Metoda rozhraní, **rozhraní**, **Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|**Coclass – třída** (při použití u **třídy** nebo **struktury**)|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy metody](method-attributes.md)