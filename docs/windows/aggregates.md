---
title: agregace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.aggregates
dev_langs:
- C++
helpviewer_keywords:
- aggregates attribute
- aggregation [C++]
- aggregate objects [C++], aggregates attribute
- aggregates [C++]
ms.assetid: 67a084c9-941f-474b-a029-9c93b38ebe9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bf6ca06ffbd3912ac3545bc3c014224412c01bc1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221167"
---
# <a name="aggregates"></a>aggregates

Označuje, že objekt agreguje objektu určeného parametrem identifikátor CLSID.

## <a name="syntax"></a>Syntaxe

```cpp
[ aggregates(
   clsid,
   variable_name
) ]
```

### <a name="parameters"></a>Parametry

*identifikátor CLSID*  
Určuje identifikátor CLSID agregovatelné objektu.

*variable_name*  
Název proměnné, která má být vložen. Tato proměnná obsahuje `IUnknown` objektu agregaci.

## <a name="remarks"></a>Poznámky

Při použití s objektem, **agregace** C++ atribut implementuje vnější obálky pro objekt agregaci (určená `clsid`).

Tento atribut vyžaduje, aby [coclass](../windows/coclass.md), [progid](../windows/progid.md), nebo [vi_progid –](../windows/vi-progid.md) atribut (nebo jiný atribut, který zahrnuje jednu z těchto) také použít u stejného elementu. Pokud se používá jakékoli jeden atribut, další dvě automaticky použity. Například pokud `progid` se použije, `vi_progid` a `coclass` jsou použita také.

### <a name="atl-projects"></a>Projekty knihovny ATL

Pokud tento atribut se používá v rámci projektu, který používá knihovny ATL, chování změny atributů. Nejprve se přidá následující položku do mapy modelu COM cílového objektu:

```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(_m_spAttrXXX, clsid)  
```

Druhý, [DECLARE_GET_CONTROLLING_UNKNOWN](../atl/reference/aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) – makro je taky přidaný.

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ano|
|**Vyžadované atributy**|Jeden nebo více z následujících akcí: `coclass`, `progid`, nebo `vi_progid`.|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[COM – atributy](../windows/com-attributes.md)  
[Atributy třídy](../windows/class-attributes.md)  
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Agregace](/windows/desktop/com/aggregation)  
[Agregovatelné](/windows/desktop/Midl/aggregatable)  
[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](../atl/reference/com-interface-entry-macros.md#com_interface_entry_autoaggregate_blind)  