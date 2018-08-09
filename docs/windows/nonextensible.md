---
title: nonextensible – | Dokumentace Microsoftu
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
ms.openlocfilehash: 812f5e2462236faef1b2b13d5fb25320319e773e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015726"
---
# <a name="nonextensible"></a>nonextensible
Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nejde prodloužit s další členy v době běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[nonextensible]  
```  
  
## <a name="remarks"></a>Poznámky  
 **Nerozšiřitelnou kategorii** C++ atribut má stejné funkce jako [nerozšiřitelnou kategorii](http://msdn.microsoft.com/library/windows/desktop/aa367120) atribut MIDL.  
  
 Použití **nerozšiřitelnou kategorii** také vyžaduje [oleautomation](../windows/oleautomation.md) atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje jedno použití **nerozšiřitelnou kategorii** atribut:  
  
```cpp  
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
|**Platí pro**|**interface**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|`dual` a `oleautomation`, nebo `dispinterface`|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   