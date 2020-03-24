---
title: com_interface_entry (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: d7b378baedd3f8c2720c7ab17698e8b416304061
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168301"
---
# <a name="com_interface_entry-c"></a>com_interface_entry (C++)

Přidá položku rozhraní do mapy modelu COM cílové třídy.

## <a name="syntax"></a>Syntaxe

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>Parametry

*com_interface_entry*<br/>
Řetězec obsahující skutečný text položky. Seznam možných hodnot naleznete v tématu [COM_INTERFACE_ENTRY maker](../../atl/reference/com-interface-entry-macros.md).

## <a name="remarks"></a>Poznámky

Atribut **COM_INTERFACE_ENTRY** C++ vloží do mapování rozhraní modelu COM cílového objektu nezkrácený obsah řetězce znaků. Pokud je atribut použit pouze jednou pro cílový objekt, položka je vložena do začátku existující mapy rozhraní. Pokud je atribut použit opakovaně u stejného cílového objektu, položky jsou vloženy na začátek mapy rozhraní v pořadí, v jakém byly přijaty.

Tento atribut vyžaduje, aby atribut [Coclass](coclass.md), [ProgID](progid.md)nebo [vi_progid](vi-progid.md) (nebo jiný atribut, který implikuje jednu z nich) byl také použit pro stejný prvek. Je-li použit libovolný atribut, budou automaticky použity ostatní dva. Například pokud je použita `progid`, jsou použita také `vi_progid` a `coclass`.

Vzhledem k tomu, že první použití **COM_INTERFACE_ENTRY** způsobí vložení nového rozhraní na začátek mapy rozhraní, musí být jedním z následujících typů COM_INTERFACE_ENTRY:

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

Další použití atributu **COM_INTERFACE_ENTRY** může používat všechny podporované typy COM_INTERFACE_ENTRY.

Toto omezení je nezbytné, protože knihovna ATL používá první položku v mapě rozhraní jako `IUnknown`identity. Proto musí být položka platné rozhraní. Například následující příklad kódu je neplatný, protože první položka v mapě rozhraní neurčuje skutečné rozhraní COM.

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>Příklad

Následující kód přidá dvě položky do existující mapy rozhraní modelu COM `CMyBaseClass`. První je standardní rozhraní a druhý skrývá `IDebugTest` rozhraní.

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

Výsledná mapa objektů modelu COM pro `CMyBaseClass` je následující:

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

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ano|
|**Požadované atributy**|Jednu nebo více následujících možností: `coclass`, `progid`nebo `vi_progid`.|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[COM – atributy](com-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)
