---
title: helpstringcontext – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringcontext
dev_langs:
- C++
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97b4b43f8cbd8f08cca4f6cf2f21294a625f289c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874574"
---
# <a name="helpstringcontext"></a>helpstringcontext
Určuje ID tématu nápovědy v souboru HLP nebo CHM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ helpstringcontext(  
   contextID  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `contextID`  
 32-bit identifikátor kontextové nápovědy v souboru nápovědy.  
  
## <a name="remarks"></a>Poznámky  
 **Helpstringcontext –** atribut C++ má stejné funkce jako [helpstringcontext –](http://msdn.microsoft.com/library/windows/desktop/aa366858) ODL – atribut.  
  
## <a name="example"></a>Příklad  
  
```  
// cpp_attr_ref_helpstringcontext.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[   object,   
   helpstring("help string"),   
   helpstringcontext(1),   
   uuid="11111111-1111-1111-1111-111111111111"  
]  
__interface IMyI   
{  
   HRESULT xx();  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, `interface`, rozhraní – metoda|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [Modul](../windows/module-cpp.md)   
