---
title: jen pro čtení (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.readonly
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
ms.openlocfilehash: 7eea071b62130c65fbb46ebc8827fc2b428c4c0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407338"
---
# <a name="readonly-c"></a>readonly (C++)

Zakáže přiřazení na datový člen.

## <a name="syntax"></a>Syntaxe

```cpp
[readonly]
```

## <a name="remarks"></a>Poznámky

**Jen pro čtení** C++ atribut má stejné funkce jako [jen pro čtení](/windows/desktop/Midl/readonly) atribut MIDL.

Pokud chcete zakázat úpravy parametru metody, použijte [v](in-cpp.md) atribut.

## <a name="example"></a>Příklad

Následující kód ukazuje použití **jen pro čtení** atribut:

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Metoda rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádný|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy datového členu](data-member-attributes.md)