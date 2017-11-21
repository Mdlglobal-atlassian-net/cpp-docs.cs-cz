---
title: "switch_type – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.switch_type
dev_langs: C++
helpviewer_keywords: switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99ec139c1ff10456639249c94451877a18cbbf51
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="switchtype"></a>switch_type
Určuje typ proměnnou použít jako union discriminant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[switch_type(  
type  
}]  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Typ přepínač může být typ integer, znak, logická hodnota nebo – výčet.  
  
## <a name="remarks"></a>Poznámky  
 **Switch_type –** atribut C++ má stejné funkce jako [switch_type –](http://msdn.microsoft.com/library/windows/desktop/aa367276) MIDL atribut.  
  
 Atributy C++ nepodporují [zapouzdřené sjednocení](http://msdn.microsoft.com/library/windows/desktop/aa366811). [Nonencapsulated sjednocení](http://msdn.microsoft.com/library/windows/desktop/aa367119) jsou podporovány pouze v následující podobě:  
  
```  
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
 Najdete v článku [případ](../windows/case-cpp.md) příklad pro ukázkové použití **switch_type –**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`typedef`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Export](../windows/export.md)   
