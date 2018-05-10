---
title: agreguje | Microsoft Docs
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
ms.openlocfilehash: 19dea3b078f894931002d186b20c1ffb85bb763b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="aggregates"></a>aggregates
Označuje, že objekt agreguje objektu určeného identifikátor CLSID.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ aggregates(  
   clsid,  
   variable_name  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `clsid`  
 Určuje identifikátor CLSID agregovatelné objektu.  
  
 `variable_name`  
 Název proměnné, která má být vložen. Obsahuje tato proměnná **IUnknown** objektu agregaci.  
  
## <a name="remarks"></a>Poznámky  
 Při použití objektu, **agregace** implementuje vnější obálku pro objekt agregovaný atribut C++ (zadáno v `clsid`).  
  
 Tento atribut vyžaduje, aby [třída typu coclass](../windows/coclass.md), [progid](../windows/progid.md), nebo [vi_progid –](../windows/vi-progid.md) atribut (nebo jiný atribut, který zahrnuje jednu z těchto) také použít stejného elementu. Pokud se používá jakékoli jeden atribut, budou automaticky použita další dvě. Například pokud **progid** se použije, **vi_progid –** a **třída typu coclass** jsou také použít.  
  
 **Projekty knihovny ATL**  
  
 Pokud tento atribut se používá v rámci projekt, který používá ATL chování změny atributů. Nejprve je přidána následující položka mapu COM cílového objektu:  
  
```  
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(_m_spAttrXXX, clsid)  
```  
  
 Druhý, [DECLARE_GET_CONTROLLING_UNKNOWN](../atl/reference/aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) makro je taky přidaný.  
  
## <a name="example"></a>Příklad  
  
```  
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
|**Platí pro**|**Třída**, `struct`|  
|**Opakovatelných**|Ano|  
|**Povinné atributy**|Jeden nebo více z následujících: **třída typu coclass**, **progid**, nebo **vi_progid –**.|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [COM – atributy](../windows/com-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Agregace](http://msdn.microsoft.com/library/windows/desktop/ms686558)   
 [agregovatelné](http://msdn.microsoft.com/library/windows/desktop/aa366721)   
 [COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](../atl/reference/com-interface-entry-macros.md#com_interface_entry_autoaggregate_blind)   
 