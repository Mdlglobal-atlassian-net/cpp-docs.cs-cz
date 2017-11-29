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
ms.openlocfilehash: 75694398f01cdf790b292d53aff5466b1e27a919
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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