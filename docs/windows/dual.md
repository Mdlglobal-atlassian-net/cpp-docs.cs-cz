---
title: duální | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dual
dev_langs:
- C++
helpviewer_keywords:
- dual attribute
ms.assetid: 5d4a9069-d819-42cd-ba56-bbcda17157d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 460e3f5316bc4b4509e563fda2354106164b3b1a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="dual"></a>dual
Umístí rozhraní v souboru IDL jako duální rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[dual]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Když **duální** C++ atribut předchází rozhraní, způsobí, že rozhraní, které má být umístěn uvnitř bloku knihovny v souboru generovaného .idl.  
  
## <a name="example"></a>Příklad  
 Následující kód je blok atribut, který používá **duální** před definice rozhraní:  
  
```  
// cpp_attr_ref_dual.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLibrary")];  
  
[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), dual]  
  
__interface IStatic : IDispatch   
{  
   HRESULT Func1(int i);  
   [   propget,   
      id(1),   
      bindable,   
      displaybind,   
      defaultbind,   
      requestedit  
   ]   
   HRESULT P1([out, retval] long *nSize);  
   [   propput,   
      id(1),   
      bindable,   
      displaybind,   
      defaultbind,   
      requestedit  
   ]   
   HRESULT P1([in] long nSize);      
};  
  
[cpp_quote("#include file.h")];  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`interface`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|**dispinterface**|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy podle použití](../windows/attributes-by-usage.md)   
 [Vlastní](../windows/custom-cpp.md)   
 [Dispinterface](../windows/dispinterface.md)   
 [Objekt](../windows/object-cpp.md)   
 [__interface](../cpp/interface.md)   
