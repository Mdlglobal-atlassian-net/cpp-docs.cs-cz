---
title: call_as | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.call_as
dev_langs:
- C++
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8fb431c6aad10f7e974ed139ddf83cfb0a58d30a
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465867"
---
# <a name="callas"></a>call_as
Umožňuje [místní](../windows/local-cpp.md) funkce mají být namapovány na vzdálenou funkci tak, aby při vzdálené funkce je volána, je vyvolána lokální funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ call_as(  
   function  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *– funkce*  
 Lokální funkce, kterou chcete volat při vyvolání vzdálenou funkci.  
  
## <a name="remarks"></a>Poznámky  
 **Call_as** C++ atribut má stejné funkce jako [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak můžete **call_as** mapovat funkci nonremotable (**f1**) na funkci lze používat vzdáleně (**Remf1**):  
  
```cpp  
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
|**Platí pro**|Metoda rozhraní|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [místní](../windows/local-cpp.md)   