---
title: nerozšiřitelnýC++ (atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: f2947e223d068ea6cc92a41abe19cb7f920112b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514395"
---
# <a name="nonextensible"></a>nonextensible

Určuje, že `IDispatch` implementace zahrnuje pouze vlastnosti a metody uvedené v popisu rozhraní a nelze je rozšířit o další členy za běhu.

## <a name="syntax"></a>Syntaxe

```cpp
[nonextensible]
```

## <a name="remarks"></a>Poznámky

Nerozšiřitelný C++ atribut má stejné funkce jako nerozšiřitelný atribut MIDL. [](/windows/win32/Midl/nonextensible)

Použití nerozšiřitelného také vyžaduje atribut [oleautomation](oleautomation.md) .

## <a name="example"></a>Příklad

Následující kód ukazuje jedno použití nerozšiřitelného atributu:

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

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**interface**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|`dual`a `oleautomation`, nebo`dispinterface`|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)