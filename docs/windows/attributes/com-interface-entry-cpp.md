---
title: COM_INTERFACE_ENTRY (C++ atributů COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: 65d174679f851613e064568b071cfcbdad8f0f06
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030404"
---
# <a name="cominterfaceentry-c"></a>com_interface_entry (C++)

Přidá položku do rozhraní do mapy modelu COM cílové třídy.

## <a name="syntax"></a>Syntaxe

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>Parametry

*com_interface_entry*<br/>
Řetězec obsahující vlastní text položky. Seznam možných hodnot najdete v tématu [makra COM_INTERFACE_ENTRY](../../atl/reference/com-interface-entry-macros.md).

## <a name="remarks"></a>Poznámky

**Com_interface_entry** C++ atribut vloží nekrácený obsah řetězce znaků do objektu map rozhraní COM cílového objektu. Pokud se atribut používá jednou k cílovému objektu svého, položka je vložen do začátku existující mapování rozhraní. Pokud se atribut používá opakovaně stejný cílový objekt, položky jsou vloženy na začátku mapování rozhraní v pořadí, ve kterém jsou přijímány.

Tento atribut vyžaduje, aby [coclass](coclass.md), [progid](progid.md), nebo [vi_progid –](vi-progid.md) atribut (nebo jiný atribut, který zahrnuje jednu z těchto) také použít u stejného elementu. Pokud se používá jakékoli jeden atribut, další dvě automaticky použity. Například pokud `progid` se použije, `vi_progid` a `coclass` jsou použita také.

Protože první použití **com_interface_entry** způsobí, že nové rozhraní má být vložen na začátek mapu rozhraní, musí být jedna z následujících typů COM_INTERFACE_ENTRY:

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

Další použití **com_interface_entry** atribut můžete používat všechny podporované typy COM_INTERFACE_ENTRY.

Toto omezení je nezbytné, protože ATL použije první položku v mapě rozhraní jako identita `IUnknown`; proto položka musí být platné rozhraní. Například následující ukázka kódu je neplatný, protože první položka v mapě rozhraní neurčuje skutečné rozhraní modelu COM.

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>Příklad

Následující kód přidá dvě položky do existující mapování rozhraní modelu COM z `CMyBaseClass`. Standardní rozhraní je první a druhý skryje `IDebugTest` rozhraní.

```cpp
// cpp_attr_ref_com_interface_entry.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name ="ldld")];

[ object,
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]
__interface IDebugTest{};

[ object,
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]
__interface IMyClass{};

[ coclass,
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")
]

class CMyClass: public IMyClass, public IDebugTest
{
};
```

Výsledný objekt mapy modelu COM pro `CMyBaseClass` vypadá takto:

```cpp
BEGIN_COM_MAP(CMyClass)
    COM_INTERFACE_ENTRY (IMyClass)
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)
    COM_INTERFACE_ENTRY(IMyClass)
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)
    COM_INTERFACE_ENTRY(IDebugTest)
    COM_INTERFACE_ENTRY(IProvideClassInfo)
END_COM_MAP()
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ano|
|**Vyžadované atributy**|Jeden nebo více z následujících akcí: `coclass`, `progid`, nebo `vi_progid`.|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[COM – atributy](com-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)