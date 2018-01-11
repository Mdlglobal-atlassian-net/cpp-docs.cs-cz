---
title: "requires_category – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.requires_category
dev_langs: C++
helpviewer_keywords: requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 677e3c94a5db69dafb66a5cd33749c129cb35afb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="requirescategory"></a>requires_category
Určuje požadovanou součást kategorie cílové třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
     [ requires_category(   
  requires_category  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *requires_category*  
 ID požadované kategorii.  
  
## <a name="remarks"></a>Poznámky  
 **Requires_category –** C++ atribut určuje kategorie součásti potřebné v cílové třídě. Další informace najdete v tématu [REQUIRED_CATEGORY](../atl/reference/category-macros.md#required_category).  
  
 Tento atribut vyžaduje, aby [třída typu coclass](../windows/coclass.md), [progid](../windows/progid.md), nebo [vi_progid –](../windows/vi-progid.md) atribut (nebo jiný atribut, který zahrnuje jednu z těchto) také použít stejného elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód vyžaduje, že objekt implementovat řízení kategorii.  
  
```  
// cpp_attr_ref_requires_category.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="MyLibrary")];  
  
[ coclass, requires_category("CATID_Control"),  
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]  
class CMyClass {};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**,`struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Jeden nebo více z následujících: **třída typu coclass**, **progid**, nebo **vi_progid –**.|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [COM – atributy](../windows/com-attributes.md)   
 [implements_category](../windows/implements-category.md)   
