---
title: s omezeným přístupem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.restricted
dev_langs:
- C++
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f79b4e53947e0e87fb70211ca40bc54f4500855f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39602769"
---
# <a name="restricted"></a>restricted
Určuje, že modul, rozhraní nebo dispinterface nejde volat libovolně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ restricted(  
   interfaces  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Rozhraní*  
 Jedno nebo více rozhraní, které nelze volat libovolně pro objekt modelu COM. Tento parametr platí pouze při použití na třídu.  
  
## <a name="remarks"></a>Poznámky  
 **s omezeným přístupem** C++ atribut má stejné funkce jako [s omezeným přístupem](http://msdn.microsoft.com/library/windows/desktop/aa367157) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje způsob použití **s omezeným přístupem** atribut:  
  
```cpp  
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
|**Platí pro**|Metody rozhraní **rozhraní**, **třídy**, **– struktura**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|**coclass** (při použití u **třídy** nebo **struktura**)|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   