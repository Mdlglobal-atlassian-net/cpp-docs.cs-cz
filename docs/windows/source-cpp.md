---
title: zdroj (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.source
dev_langs: C++
helpviewer_keywords: source attribute
ms.assetid: 1878d05d-7709-4e97-b114-c62f38f5140e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f4bfc79a76ece278c62b4895cdeb2e10d6df42aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="source-c"></a>source (C++)
Na třídu určuje rozhraní zdrojového objektu COM pro spojovací body. Na vlastnosti nebo metody označuje, že člen vrátí objekt, nebo typu VARIANT, která je zdroj událostí systému.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ source(  
   interfaces  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `interfaces`  
 Jedno nebo více rozhraní, zadejte, když použijete zdrojový atribut na třídu. Tento parametr se nepoužívá při zdroje k vlastnosti nebo metody.  
  
## <a name="remarks"></a>Poznámky  
 **Zdroj** atribut C++ má stejné funkce jako [zdroj](http://msdn.microsoft.com/library/windows/desktop/aa367166) MIDL atribut.  
  
 Můžete použít [výchozí](../windows/default-cpp.md) atribut zadat výchozí zdroj rozhraní pro objekt.  
  
## <a name="example"></a>Příklad  
  
```  
// cpp_attr_ref_source.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid(11111111-1111-1111-1111-111111111111)]  
__interface b  
{  
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]  
   HRESULT get_I([out, retval]long *i);  
};  
  
[object, uuid(11111111-1111-1111-1111-111111111131)]  
__interface c  
{  
   [id(0), propget, bindable, displaybind, defaultbind, requestedit]   
   HRESULT et_I([out, retval]long *i);  
};  
  
[coclass, default(c), uuid(11111111-1111-1111-1111-111111111132)]  
class N : public b  
{  
};  
  
[coclass, source(c), default(b, c), uuid(11111111-1111-1111-1111-111111111133)]  
class NN : public b  
{  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, `struct`,`interface`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**Třída typu coclass** (při použití na třídě nebo struktuře)|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [coclass](../windows/coclass.md)   
