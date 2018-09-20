---
title: iid_is – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.iid_is
dev_langs:
- C++
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f1616168829d488a0b0a899f1dd09f9b02700ee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389340"
---
# <a name="iidis"></a>iid_is

Určuje identifikátor IID rozhraní modelu COM, který ukazuje ukazatel rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
[ iid_is(
   "expression"
) ]
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

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)<br/>
[Atributy parametru](../windows/parameter-attributes.md)  