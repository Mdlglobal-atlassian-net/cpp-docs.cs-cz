---
title: nonextensible – (atribut COM jazyka C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: ed396b3d55e16cf195949c713ab574812b796a1a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407572"
---
# <a name="nonextensible"></a>nonextensible

Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nejde prodloužit s další členy v době běhu.

## <a name="syntax"></a>Syntaxe

```cpp
[nonextensible]
```

## <a name="remarks"></a>Poznámky

**Nerozšiřitelnou kategorii** C++ atribut má stejné funkce jako [nerozšiřitelnou kategorii](/windows/desktop/Midl/nonextensible) atribut MIDL.

Použití **nerozšiřitelnou kategorii** také vyžaduje [oleautomation](oleautomation.md) atribut.

## <a name="example"></a>Příklad

Následující kód ukazuje jedno použití **nerozšiřitelnou kategorii** atribut:

```cpp
// cpp_attr_ref_nonextensible.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export] typedef long HRESULT;

[dual, nonextensible, ms_union, oleautomation,
uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   HRESULT procedure (int i);
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**interface**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|`dual` a `oleautomation`, nebo `dispinterface`|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)