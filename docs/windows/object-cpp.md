---
title: objekt (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 2667c8ecb14e31388737366c4de6c527bdc40f9d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012749"
---
# <a name="object-c"></a>object (C++)
Určuje vlastní rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[object]  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud předchozí definice rozhraní, **objekt** C++ atribut způsobí, že rozhraní budou umístěny v souboru IDL jako vlastní rozhraní.  
  
 Libovolné rozhraní označené objektu musí dědit z `IUnknown`. Tato podmínka splněna Pokud některý z základních rozhraní dědí od `IUnknown`. Pokud žádná základní rozhraní dědí od `IUnknown`, kompilátor způsobí, že rozhraní označené **objekt** odvodit z `IUnknown`.  
  
## <a name="example"></a>Příklad  
 Zobrazit [nonbrowsable](../windows/nonbrowsable.md) příklad, jak používat **objekt**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**interface**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Duální](../windows/dual.md)   
 [Dispinterface](../windows/dispinterface.md)   
 [Vlastní](../windows/custom-cpp.md)   
 [__interface](../cpp/interface.md)   