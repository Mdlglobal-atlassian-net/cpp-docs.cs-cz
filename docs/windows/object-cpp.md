---
title: objekt (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.object
dev_langs: C++
helpviewer_keywords: object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5714d7c3bd029c7b1df636044ed1968f53600848
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="object-c"></a>object (C++)
Určuje vlastní rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[object]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Při předchozím definici rozhraní **objekt** C++ atribut způsobuje rozhraní umístit do souboru IDL jako vlastní rozhraní.  
  
 Každé rozhraní označené jako objekt musí dědit z **IUnknown**. Toto je podmínka Pokud některá z základní rozhraní dědí od **IUnknown**. Pokud žádná základní rozhraní dědí od **IUnknown**, kompilátor způsobí, že rozhraní označené jako **objekt** k odvozování z **IUnknown**.  
  
## <a name="example"></a>Příklad  
 V tématu [nonbrowsable](../windows/nonbrowsable.md) příklad použití **objekt**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`interface`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [duální](../windows/dual.md)   
 [dispinterface](../windows/dispinterface.md)   
 [vlastní](../windows/custom-cpp.md)   
 [__interface](../cpp/interface.md)   
