---
title: s omezeným přístupem (atribut COM jazyka C++)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 86f40fa49daf88668e37bef07f0db33d01cf1942
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407351"
---
# <a name="restricted"></a>restricted

Určuje, že modul, rozhraní nebo dispinterface nejde volat libovolně.

## <a name="syntax"></a>Syntaxe

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>Parametry

*interfaces*<br/>
Jedno nebo více rozhraní, které nelze volat libovolně pro objekt modelu COM. Tento parametr platí pouze při použití na třídu.

## <a name="remarks"></a>Poznámky

**s omezeným přístupem** C++ atribut má stejné funkce jako [s omezeným přístupem](/windows/desktop/Midl/restricted) atribut MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje způsob použití **s omezeným přístupem** atribut:

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Metody rozhraní **rozhraní**, **třídy**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|**coclass** (při použití u **třídy** nebo **struktura**)|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy metody](method-attributes.md)