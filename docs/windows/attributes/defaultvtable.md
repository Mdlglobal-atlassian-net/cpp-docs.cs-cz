---
title: defaultvtable (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultvtable
helpviewer_keywords:
- defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
ms.openlocfilehash: 813fb9dd4edf2f6e522e7310ba1e8bfcd55ed2b9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028344"
---
# <a name="defaultvtable"></a>defaultvtable

Definuje rozhraní jako výchozího rozhraní vtable pro objekt modelu COM.

## <a name="syntax"></a>Syntaxe

```cpp
[ defaultvtable(interface) ]
```

### <a name="parameters"></a>Parametry

*rozhraní*<br/>
Určené rozhraní, které mají mít výchozí vtable pro objekt modelu COM.

## <a name="remarks"></a>Poznámky

**Defaultvtable** C++ atribut má stejné funkce jako [defaultvtable](/windows/desktop/Midl/defaultvtable) atribut MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje na třídu, která použít atributy **defaultvtable** k určení výchozího rozhraní:

```cpp
// cpp_attr_ref_defaultvtable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI1 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface IMyI2 {
   HRESULT x();
};

[object, uuid("00000000-0000-0000-0000-000000000003")]
__interface IMyI3 {
   HRESULT x();
};

[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),
uuid("00000000-0000-0000-0000-000000000004")]
class CMyC3 : public IMyI3 {};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|**coclass**|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)