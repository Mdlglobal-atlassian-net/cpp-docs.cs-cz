---
title: DefaultValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.defaultvalue
dev_langs:
- C++
helpviewer_keywords:
- defaultvalue attribute
ms.assetid: efa5d050-b2cc-4d9e-9b8e-79954f218d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c838f057d9c5e59193d0578fe8aa871b1b75ee9d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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
 [V](../windows/in-cpp.md)   
 [pointer_default –](../windows/pointer-default.md)   
 [Jedinečné](../windows/unique-cpp.md)   
