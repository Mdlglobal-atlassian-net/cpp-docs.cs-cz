---
title: "defaultvtable – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.defaultvtable
dev_langs: C++
helpviewer_keywords: defaultvtable attribute
ms.assetid: 5b3ed483-f69e-44dd-80fc-952028eb9d73
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0753887cef2b169758351be9fafc0ec532bacb05
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="defaultvtable"></a>defaultvtable
Definuje rozhraní jako výchozí vtable rozhraní pro objekt COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ defaultvtable(  
   interface  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `interface`  
 Určené rozhraní, které chcete mít výchozí vtable pro objekt COM.  
  
## <a name="remarks"></a>Poznámky  
 **Defaultvtable –** atribut C++ má stejné funkce jako [defaultvtable –](http://msdn.microsoft.com/library/windows/desktop/aa366795) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje na třídu, která použít atributy **defaultvtable –** zadat výchozí rozhraní:  
  
```  
// cpp_attr_ref_defaultvtable.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI1 {  
   HRESULT x();  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000002")]  
__interface IMyI2 {  
   HRESULT x();  
};  
  
[object, uuid("00000000-0000-0000-0000-000000000003")]  
__interface IMyI3 {  
   HRESULT x();  
};  
  
[coclass, source(IMyI3, IMyI1), default(IMyI3, IMyI2), defaultvtable(IMyI1),  
uuid("00000000-0000-0000-0000-000000000004")]  
class CMyC3 : public IMyI3 {};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**,`struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**Třída typu coclass**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   