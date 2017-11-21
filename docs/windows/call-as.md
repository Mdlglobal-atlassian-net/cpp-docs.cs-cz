---
title: call_as | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.call_as
dev_langs: C++
helpviewer_keywords: call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4ce0123f6f06d47d920ed55a1460944393960ff6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="callas"></a>call_as
Umožňuje [místní](../windows/local-cpp.md) funkce nejde mapovat na vzdálené funkce tak, aby při vzdálené funkce je volána, místní funkce je volána.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ call_as(  
   function  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *funkce*  
 Místní funkce, kterou chcete volat při vzdálené funkce je volána.  
  
## <a name="remarks"></a>Poznámky  
 **Call_as** atribut C++ má stejné funkce jako [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak můžete použít **call_as** k mapování funkce nonremotable (**f1**) na funkci učinit vzdáleným (**Remf1**):  
  
```  
// cpp_attr_ref_call_as.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
[dual, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMInterface {  
   [local] HRESULT f1 ( int i );  
   [call_as(f1)] HRESULT Remf1 ( int i );   
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Rozhraní – metoda|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [místní](../windows/local-cpp.md)   
