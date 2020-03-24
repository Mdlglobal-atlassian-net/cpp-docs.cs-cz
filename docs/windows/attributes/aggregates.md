---
title: agregace (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.aggregates
helpviewer_keywords:
- aggregates attribute
- aggregation [C++]
- aggregate objects [C++], aggregates attribute
- aggregates [C++]
ms.assetid: 67a084c9-941f-474b-a029-9c93b38ebe9a
ms.openlocfilehash: 08e623d84553f9fcf556c9cf480c1816c7300460
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168496"
---
# <a name="aggregates"></a>aggregates

Označuje, že objekt agreguje objekt určený identifikátorem CLSID.

## <a name="syntax"></a>Syntaxe

```cpp
[ aggregates(clsid, variable_name) ]
```

### <a name="parameters"></a>Parametry

*CLSID*<br/>
Určuje identifikátor CLSID agregovatelné objektu.

*variable_name*<br/>
Název proměnné, která má být vložena. Tato proměnná obsahuje `IUnknown` objektu, který se agreguje.

## <a name="remarks"></a>Poznámky

Při použití na objekt, **agreguje** C++ atribut implementuje vnější obálku pro objekt, který je agregován (určený pomocí `clsid`).

Tento atribut vyžaduje, aby atribut [Coclass](coclass.md), [ProgID](progid.md)nebo [vi_progid](vi-progid.md) (nebo jiný atribut, který implikuje jednu z nich) byl také použit pro stejný prvek. Je-li použit libovolný atribut, budou automaticky použity ostatní dva. Například pokud je použita `progid`, jsou použita také `vi_progid` a `coclass`.

### <a name="atl-projects"></a>Projekty ATL

Pokud se tento atribut používá v rámci projektu, který používá ATL, chování atributu se změní. Nejprve se do mapy modelu COM cílového objektu přidá následující položka:

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(_m_spAttrXXX, clsid)
```

Za druhé je také přidáno makro [DECLARE_GET_CONTROLLING_UNKNOWN](../../atl/reference/aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) .

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_aggregates.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

// requires 'aggregatable.dll'
// see aggregatable attribute to create 'aggregatable.dll'
class DECLSPEC_UUID("1a8369cc-1c91-42c4-befa-5a5d8c9d2529") CMyClass;

[module (name="MYObject")];
[object, uuid("ab006d85-e754-47c5-9ef4-2744ff32a20c")]
__interface IObject
{
};

[ coclass, aggregates(__uuidof(CMyClass)),
  uuid("91cb2c06-8931-432a-baac-206e55c4edfb")]
struct CObject : IObject
{
   int i;
};
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
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Agregace](/windows/win32/com/aggregation)<br/>
[Agregovatelné](/windows/win32/Midl/aggregatable)<br/>
[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](../../atl/reference/com-interface-entry-macros.md#com_interface_entry_autoaggregate_blind)
