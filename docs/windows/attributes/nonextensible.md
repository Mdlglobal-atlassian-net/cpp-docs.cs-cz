---
title: nerozšiřitelnýC++ (atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: 2a1cd4d685e2fd141c6e11feaea488f44a884c80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214658"
---
# <a name="nonextensible"></a>nonextensible

Určuje, že implementace `IDispatch` zahrnuje pouze vlastnosti a metody uvedené v popisu rozhraní a nelze je rozšířit o další členy v době běhu.

## <a name="syntax"></a>Syntaxe

```cpp
[nonextensible]
```

## <a name="remarks"></a>Poznámky

**Nerozšiřitelný** C++ atribut má stejné funkce jako [nerozšiřitelný](/windows/win32/Midl/nonextensible) atribut MIDL.

Použití **nerozšiřitelného** také vyžaduje atribut [oleautomation](oleautomation.md) .

## <a name="example"></a>Příklad

Následující kód ukazuje jedno použití **nerozšiřitelného** atributu:

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
|**Požadované atributy**|`dual` a `oleautomation`nebo `dispinterface`|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)
