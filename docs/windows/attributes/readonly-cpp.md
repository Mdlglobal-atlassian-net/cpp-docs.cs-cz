---
title: ReadOnly (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.readonly
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
ms.openlocfilehash: 415ad5e33de3132e055e53178e6e65d411f169f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214601"
---
# <a name="readonly-c"></a>readonly (C++)

Zakáže přiřazení datovému členu.

## <a name="syntax"></a>Syntaxe

```cpp
[readonly]
```

## <a name="remarks"></a>Poznámky

Atribut **jen pro čtení** C++ má stejné funkce jako atribut [ReadOnly](/windows/win32/Midl/readonly) MIDL.

Pokud chcete zakázat úpravu parametru metody, použijte atribut [in](in-cpp.md) .

## <a name="example"></a>Příklad

Následující kód ukazuje použití atributu **ReadOnly** :

```cpp
// cpp_attr_ref_readonly.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
#include "unknwn.h"
[module(name="ATLFIRELib")];

[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]
__interface IFireTabCtrl
{
   [readonly, id(1)] int i();
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy datového členu](data-member-attributes.md)
