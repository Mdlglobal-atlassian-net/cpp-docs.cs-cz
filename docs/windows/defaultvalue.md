---
title: DefaultValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.defaultvalue
dev_langs: C++
helpviewer_keywords: defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb269a4c7e85269096e5df8a56e16bf898348118
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="defaultvalue"></a>defaultvalue
Umožňuje specifikaci výchozí hodnota pro typové volitelný parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[ defaultvalue= value ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *value*  
 Výchozí hodnota pro parametr.  
  
## <a name="remarks"></a>Poznámky  
 **Defaultvalue** atribut C++ má stejné funkce jako [defaultvalue](http://msdn.microsoft.com/library/windows/desktop/aa366793) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje metoda rozhraní pomocí **defaultvalue** atribut:  
  
```  
// cpp_attr_ref_defaultvalue.cpp  
// compile with: /LD  
#include <windows.h>  
  
[export] typedef long HRESULT;  
[export, ptr, string] typedef unsigned char * MY_STRING_TYPE;  
  
[  uuid("479B29EE-9A2C-11D0-B696-00A0C903487A"),  
   dual, oleautomation,  
   helpstring("IFireTabCtrl Interface"),  
   helpcontext(122), pointer_default(unique) ]  
  
__interface IFireTabCtrl : IDispatch {  
   [bindable, propget] HRESULT get_Size([out, retval, defaultvalue("33")] long *nSize);  
   [bindable, propput] HRESULT put_Size([in] int nSize);  
};  
  
[ module(name="ATLFIRELib", uuid="479B29E1-9A2C-11D0-B696-00A0C903487A",  
      version="1.0", helpstring="ATLFire 1.0 Type Library") ];  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Parametr rozhraní|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [na více systémů](../windows/out-cpp.md)   
 [retval –](../windows/retval.md)   
 [v](../windows/in-cpp.md)   
 [pointer_default –](../windows/pointer-default.md)   
 [jedinečné](../windows/unique-cpp.md)   
