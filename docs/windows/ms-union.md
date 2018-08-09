---
title: ms_union – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.ms_union
dev_langs:
- C++
helpviewer_keywords:
- ms_union attribute
ms.assetid: bb548689-6962-457e-af56-8ffdf68987eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 52e91e8084b1f055002aba7c2f544002d31feffc
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020236"
---
# <a name="msunion"></a>ms_union
Určuje zarovnání reprezentace dat sítě nonencapsulated sjednocení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ms_union]  
```  
  
## <a name="remarks"></a>Poznámky  
 **Ms_union –** C++ atribut má stejné funkce jako [ms_union –](http://msdn.microsoft.com/library/windows/desktop/aa367100) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje umístění **ms_union –**:  
  
```cpp  
// cpp_attr_ref_ms_union.cpp  
// compile with: /LD  
#include <unknwn.h>  
[object, ms_union, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl {  
   HRESULT DisplayString([in, string] char * p1);  
};  
  
[export, switch_type(short)] union _WILLIE_UNION_TYPE  {  
   [case(24)]  
      float fMays;  
   [case(25)]  
      double dMcCovey;  
   [default]  
      int x;  
 };  
  
[public] typedef _WILLIE_UNION_TYPE WILLIE_UNION_TYPE;  
  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Nonencapsulated sjednocení|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|`dispinterface`|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)   