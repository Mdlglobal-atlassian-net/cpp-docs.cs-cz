---
title: "Vlastní (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.custom
dev_langs: C++
helpviewer_keywords: custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7f811197526d2d3da0700af27be84151da79d67f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 *UUID*  
 Jedinečný identifikátor.  
  
 *Hodnota*  
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
