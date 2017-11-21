---
title: dispinterface | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.dispinterface
dev_langs: C++
helpviewer_keywords: dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e52d050b9b05ccb72969c531297367e729c258b1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dispinterface"></a>dispinterface
Umístí rozhraní v souboru IDL jako rozhraní odesílání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[dispinterface]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Když **dispinterface** C++ atribut předchází rozhraní, způsobí, že rozhraní, které má být umístěn uvnitř bloku knihovny v souboru generovaného .idl.  
  
 Pokud nezadáte základní třídu, rozhraní dispatch odvodí z `IDispatch`. Je nutné zadat [id](../windows/id.md) pro členy rozhraní odesílání.  
  
 Příklad použití pro [dispinterface](http://msdn.microsoft.com/library/windows/desktop/aa366802) v dokumentaci k MIDL:  
  
```  
dispinterface helloPro   
   { interface hello; };   
```  
  
 není platná pro **dispinterface** atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [vazbu](../windows/bindable.md) příklad použití **dispinterface**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`interface`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|**duální**, **objekt**, **oleautomation**, `local`, **ms_union –**|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy podle použití](../windows/attributes-by-usage.md)   
 [UUID](../windows/uuid-cpp-attributes.md)   
 [duální](../windows/dual.md)   
 [vlastní](../windows/custom-cpp.md)   
 [objekt](../windows/object-cpp.md)   
 [__interface](../cpp/interface.md)   
