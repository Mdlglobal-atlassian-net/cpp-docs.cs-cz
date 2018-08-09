---
title: místní (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.local
dev_langs:
- C++
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ad1fb4dd281918b0d9ab3494c9a9f060468fc389
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018094"
---
# <a name="local-c"></a>local (C++)
Při použití v záhlaví rozhraní, můžete pomocí kompilátoru MIDL jako generátor záhlaví. Při použití jednotlivých funkcí, určuje místní postupu, pro které jsou generovány žádné zástupné procedury.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[local]  
```  
  
## <a name="remarks"></a>Poznámky  
 **Místní** C++ atribut má stejné funkce jako [místní](http://msdn.microsoft.com/library/windows/desktop/aa367071) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Zobrazit [call_as](../windows/call-as.md) příklad, jak používat **místní**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**rozhraní**, rozhraní – metoda|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|`dispinterface`|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [call_as](../windows/call-as.md)   