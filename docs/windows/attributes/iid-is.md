---
title: iid_is – (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.iid_is
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
ms.openlocfilehash: 176ab83bfae18ff7f43fe0860591f2d1ac50d7eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535327"
---
# <a name="iidis"></a>iid_is

Určuje identifikátor IID rozhraní modelu COM, který ukazuje ukazatel rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
[ iid_is("expression") ]
```

### <a name="parameters"></a>Parametry

*Výraz*<br/>
Výraz jazyka C, který určuje IID rozhraní modelu COM na které odkazuje ukazatel rozhraní.

## <a name="remarks"></a>Poznámky

**Iid_is –** C++ atribut má stejné funkce jako [iid_is –](/windows/desktop/Midl/iid-is) atribut MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje použití **iid_is –**:

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Rozhraní parametr, datový člen|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)