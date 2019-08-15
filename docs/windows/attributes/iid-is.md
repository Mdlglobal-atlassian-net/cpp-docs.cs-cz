---
title: iid_is (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: 8bfa20f55afd85019795fdd40548158c2f49e126
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514668"
---
# <a name="iid_is"></a>iid_is

Určuje IID rozhraní modelu COM, na které odkazoval ukazatel rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>Parametry

*vyjádření*<br/>
Výraz jazyka C, který určuje IID rozhraní modelu COM, na které ukazuje ukazatel rozhraní.

## <a name="remarks"></a>Poznámky

Atribut **iid_is** C++ má stejné funkce jako atribut [iid_is](/windows/win32/Midl/iid-is) MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje použití **iid_is**:

```cpp
// cpp_attr_ref_iid_is.cpp
// compile with: /LD
#include "wtypes.h"
#include "unknwn.h"
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl : IDispatch
{
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]
   IUnknown ** ppvObject);
};

[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Parametr rozhraní, datový člen|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)