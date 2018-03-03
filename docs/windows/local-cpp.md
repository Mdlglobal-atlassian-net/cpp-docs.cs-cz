---
title: "místní (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.local
dev_langs:
- C++
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3543adfe0cb25f7946e6ed6c81c4bd66a7b60324
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="local-c"></a>local (C++)
Při použití v hlavičce rozhraní, můžete použít MIDL kompilátoru jako generátor záhlaví. Při použití v jednotlivé funkce, označí místní postupu, pro které jsou generovány žádné zástupných procedur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[local]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 `local` Atribut C++ má stejné funkce jako [místní](http://msdn.microsoft.com/library/windows/desktop/aa367071) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 V tématu [call_as](../windows/call-as.md) příklad použití `local`.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`interface`, rozhraní – metoda|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|**dispinterface**|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [call_as](../windows/call-as.md)   
