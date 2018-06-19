---
title: noncreatable – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.noncreatable
dev_langs:
- C++
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4055d541fa60c714262a64466734bc2b2323775b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877820"
---
# <a name="noncreatable"></a>noncreatable
Definuje objekt, který nelze vytvořit instanci samostatně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[noncreatable]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **Noncreatable –** atribut C++ má stejné funkce jako [noncreatable –](http://msdn.microsoft.com/library/windows/desktop/aa367118) MIDL atribut a je automaticky předána do vygenerovaného. IDL soubor kompilátorem.  
  
 Pokud tento atribut se používá v rámci projekt, který používá ATL, změní chování atribut. Kromě výše uvedených chování atribut také vloží [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makro. Toto makro označuje ATL objekt nelze vytvořit externě.  
  
## <a name="example"></a>Příklad  
  
```  
// cpp_attr_ref_noncreatable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("11111111-1111-1111-1111-111111111111")]  
__interface A   
{  
};  
  
[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]  
class CMyClass : public A   
{  
   HRESULT xx();  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, `struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**coclass**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   
