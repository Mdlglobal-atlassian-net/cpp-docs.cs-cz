---
title: implements_category – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.implements_category
dev_langs:
- C++
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6770f8303af63c66f0d1a656c2b36e034cc2be83
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879032"
---
# <a name="implementscategory"></a>implements_category
Určuje součást kategorie implementované cílové třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ implements_category(  
   implements_category="uuid"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 **implements_category**  
 ID implementovaná kategorie.  
  
## <a name="remarks"></a>Poznámky  
 **Implements_category –** C++ atribut určuje součást kategorie implementované cílové třídy. K tomu je potřeba vytváření mapy kategorie a přidávání samostatných položky určeného **implements_category –** atribut. Další informace najdete v tématu [co jsou součástí kategorií a jak se budou fungují?](http://msdn.microsoft.com/library/windows/desktop/ms694322).  
  
 Tento atribut vyžaduje, aby [třída typu coclass](../windows/coclass.md), [progid](../windows/progid.md), nebo [vi_progid –](../windows/vi-progid.md) atribut (nebo jiný atribut, který zahrnuje jednu z těchto) také použít stejného elementu. Pokud se používá jakékoli jeden atribut, budou automaticky použita další dvě. Například pokud **progid** se použije, **vi_progid –** a **třída typu coclass** jsou také použít.  
  
## <a name="example"></a>Příklad  
 Následující kód určuje, že následující objekt implementuje kategorie ovládacího prvku.  
  
```  
// cpp_attr_ref_implements_category.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="MyLib")];  
[ coclass, implements_category("CATID_Control"),  
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]  
class CMyClass {};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, `struct`|  
|**Opakovatelných**|Ano|  
|**Povinné atributy**|Jeden z následujících: **třída typu coclass**, **progid**, nebo **vi_progid –**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [COM – atributy](../windows/com-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [IMPLEMENTED_CATEGORY](../atl/reference/category-macros.md#implemented_category)   
 