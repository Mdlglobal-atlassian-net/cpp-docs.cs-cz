---
title: "helpstringcontext – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.helpstringcontext
dev_langs: C++
helpviewer_keywords: helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c5492d18085d78e20d6654898a6c66647e3bbe0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [modul](../windows/module-cpp.md)   
