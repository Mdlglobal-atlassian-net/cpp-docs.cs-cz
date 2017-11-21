---
title: "s omezeným přístupem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.restricted
dev_langs: C++
helpviewer_keywords: restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c6a6b0172b0078dee659964b36ec37464ec1705d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="restricted"></a>restricted
Určuje, že členem modulu, rozhraní nebo dispinterface nelze volat libovolně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ restricted(  
   interfaces  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `interfaces`  
 Jedno nebo více rozhraní, které nemusí být volat libovolně u objektu COM. Tento parametr je pouze platný při použití na třídu.  
  
## <a name="remarks"></a>Poznámky  
 **s omezeným přístupem** atribut C++ má stejné funkce jako [s omezeným přístupem](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje způsob použití **s omezeným přístupem** atribut:  
  
```  
// cpp_attr_ref_restricted.cpp  
// compile with: /LD  
#include "windows.h"  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface b  
{  
};  
  
[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]  
class c : public a, public b  
{  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Rozhraní metody `interface`, **třída**,`struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**Třída typu coclass** (při použití **třída** nebo `struct`)|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
