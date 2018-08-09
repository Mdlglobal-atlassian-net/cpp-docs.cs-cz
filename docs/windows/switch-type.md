---
title: switch_type – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c6c1b6dda469dec663e5a8c385d300b113246a77
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016441"
---
# <a name="switchtype"></a>switch_type
Určuje typ proměnné použité jako sjednocení discriminant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[switch_type(  
type  
}]  
```  
  
### <a name="parameters"></a>Parametry  
 *Typ*  
 Typ přepínače může být typ integer, znak, logická hodnota nebo výčet.  
  
## <a name="remarks"></a>Poznámky  
 **Switch_type –** C++ atribut má stejné funkce jako [switch_type –](http://msdn.microsoft.com/library/windows/desktop/aa367276) atribut MIDL.  
  
 Atributy C++ nepodporuje [zapouzdřené sjednocení](http://msdn.microsoft.com/library/windows/desktop/aa366811). [Nonencapsulated sjednocení](http://msdn.microsoft.com/library/windows/desktop/aa367119) jsou podporovány pouze v následujícím tvaru:  
  
```cpp  
// cpp_attr_ref_switch_type.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLibrary")];  
[ export ]  
struct SizedValue2 {  
   [switch_type("char"), switch_is(kind)] union {  
      [case(1), string]  
         wchar_t* wval;  
      [default, string]  
         char* val;  
   };  
   char kind;  
};  
```  
  
## <a name="example"></a>Příklad  
 Najdete v článku [případ](../windows/case-cpp.md) příklad ukázkový používání **switch_type –**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Definice TypeDef**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [– TypeDef, Enum, Union a struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [export](../windows/export.md)   