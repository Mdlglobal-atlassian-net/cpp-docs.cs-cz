---
title: objekt (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 601d67fb48f0ae826474d33e7dca0fbffff9478c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879705"
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
 [Duální](../windows/dual.md)   
 [Dispinterface](../windows/dispinterface.md)   
 [Vlastní](../windows/custom-cpp.md)   
 [__interface](../cpp/interface.md)   
