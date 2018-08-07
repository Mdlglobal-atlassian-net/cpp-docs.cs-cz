---
title: dispinterface | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dispinterface
dev_langs:
- C++
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6497d6da630095f4d7691edb076fc354b87e5a13
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569211"
---
# <a name="dispinterface"></a>dispinterface
Umístí rozhraní v souboru IDL jako rozhraní odbavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[dispinterface]  
```  
  
## <a name="remarks"></a>Poznámky  
 Když **dispinterface** C++ atribut předchází rozhraní, způsobí, že rozhraní být umístěny uvnitř bloku knihovny v souboru generovaného IDL.  
  
 Pokud zadáte základní třídy, rozhraní odbavení odvodí z `IDispatch`. Je nutné zadat [id](../windows/id.md) pro členy rozhraní odbavení.  
  
 Příklad použití pro [dispinterface](http://msdn.microsoft.com/library/windows/desktop/aa366802) v dokumentaci k MIDL:  
  
```  
dispinterface helloPro   
   { interface hello; };   
```  
  
 není platný pro **dispinterface** atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [umožňujících vazbu](../windows/bindable.md) příklad, jak používat **dispinterface**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**interface**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|**duální**, **objekt**, **oleautomation**, `local`, **ms_union –**|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy podle použití](../windows/attributes-by-usage.md)   
 [identifikátor UUID](../windows/uuid-cpp-attributes.md)   
 [Duální](../windows/dual.md)   
 [Vlastní](../windows/custom-cpp.md)   
 [objekt](../windows/object-cpp.md)   
 [__interface](../cpp/interface.md)   