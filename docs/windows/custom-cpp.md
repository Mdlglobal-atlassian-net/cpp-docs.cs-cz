---
title: Vlastní (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.custom
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b37d87d5380b9d4dac69cee702654285461ead6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871624"
---
# <a name="custom-c"></a>custom (C++)
Definuje metadata pro objekt knihovny typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ custom(  
   uuid,   
   value  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *uuid*  
 Jedinečný identifikátor.  
  
 *value*  
 Hodnota, která mohou být umístěny na hodnotu typu variant.  
  
## <a name="remarks"></a>Poznámky  
 **Vlastní** C++ atributu způsobí, že informace do knihovny typů. Budete potřebovat nástroj, který čte vlastní hodnotu z knihovny typů.  
  
 **Vlastní** atribut má stejné funkce jako [vlastní](http://msdn.microsoft.com/library/windows/desktop/aa366766) MIDL atribut.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Bez COM `interface`, **třída**, `enum`s, `idl_module` metody, členové rozhraní, rozhraní parametry `typedef`s, **– typ union**s, `struct`s|  
|**Opakovatelných**|Ano|  
|**Povinné atributy**|**Třída typu coclass** (při použití u třídy)|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Samostatné atributy](../windows/stand-alone-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
