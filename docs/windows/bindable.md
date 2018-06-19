---
title: vazbu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.bindable
dev_langs:
- C++
helpviewer_keywords:
- bindable attribute
ms.assetid: a2360f92-927b-4af8-98cc-6eca7f4ec954
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a1cf16bfbeee2231133e60429a4a25e9d4fe85c8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861802"
---
# <a name="bindable"></a>bindable
Označuje, že vlastnost podporuje datovou vazbu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[bindable]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **Vazbu** atribut C++ má stejné funkce jako [vazbu](http://msdn.microsoft.com/library/windows/desktop/aa366738) MIDL atribut. Můžete ji použít v vlastnosti definované s [propget –](../windows/propget.md), [propput –](../windows/propput.md), nebo [propputref](../windows/propputref.md) atributy, případně je možné ručně definovat vazbu metoda.  
  
 Následující ukázky MFC ukazují použití **vazbu**:  
  
-   [Ovládací prvky – ukázky: Na základě MFC ActiveX – ovládací prvky](http://msdn.microsoft.com/en-us/a44adf86-0ba0-4504-bedb-512b6cba2e63)  
  
-   [Str ukázka: Ovládací prvek ActiveX](http://msdn.microsoft.com/en-us/9ba34d04-280e-49f4-90ae-41a6be44c95b)  
  
-   [Ukázka TESTHELP: Ovládací prvek ActiveX s popisy tlačítek a Nápověda](http://msdn.microsoft.com/en-us/d822861d-c6f0-4d0a-ad11-970eebb1e8cd)  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak můžete použít **vazbu** u vlastnosti:  
  
```  
// cpp_attr_ref_bindable.cpp  
// compile with: /LD  
#include <windows.h>  
[  
   uuid("479B29E3-9A2C-11D0-B696-00A0C903487A"),  
   dispinterface,  
   helpstring("property demo Interface")  
]  
__interface IPropDemo : IDispatch {  
  
   [propget, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([out, retval] long *nSize);  
   [propput, id(1), bindable, displaybind, defaultbind, requestedit] HRESULT P1([in] long nSize);  
   [id(3), bindable, propget] HRESULT Object([out, retval] IDispatch **ppObj);  
   [id(3), bindable, propputref] HRESULT Object([in] IDispatch* pObj);     
   [id(-552), helpstring("method AboutBox")] HRESULT AboutBox();  
};  
  
[ module(name="PropDemoLib", uuid="479B29E2-9A2C-11D0-B696-00A0C903487A", version="1.0", helpstring="property demo") ];  
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
 [defaultbind –](../windows/defaultbind.md)   
 [displaybind –](../windows/displaybind.md)   
 [immediatebind –](../windows/immediatebind.md)   
 [requestedit](../windows/requestedit.md)   
