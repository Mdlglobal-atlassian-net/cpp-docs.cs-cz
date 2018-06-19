---
title: nonextensible – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87cdbf66676ed2a3e6054006270b39ad80325857
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881598"
---
# <a name="nonextensible"></a>nonextensible
Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nelze ji rozšířit s další členy v době běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[nonextensible]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **Nonextensible –** atribut C++ má stejné funkce jako [nonextensible –](http://msdn.microsoft.com/library/windows/desktop/aa367120) MIDL atribut.  
  
 Použití **nonextensible –** taky vyžaduje [oleautomation](../windows/oleautomation.md) atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje jedno použití **nonextensible –** atribut:  
  
```  
// cpp_attr_ref_nonextensible.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export] typedef long HRESULT;  
  
[dual, nonextensible, ms_union, oleautomation,   
uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   HRESULT procedure (int i);   
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`interface`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**duální** a **oleautomation**, nebo **dispinterface**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
