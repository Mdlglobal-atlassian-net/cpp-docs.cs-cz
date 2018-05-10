---
title: last_is – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.last_is
dev_langs:
- C++
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f27c0a12ddf5fe87f7065a16d042bd0afcfc0315
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="lastis"></a>last_is
Určuje index posledním elementem pole přenášet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ last_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *výraz*  
 Jeden nebo více výrazů jazyka C. Prázdný argument sloty jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 **Last_is –** atribut C++ má stejné funkce jako [last_is –](http://msdn.microsoft.com/library/windows/desktop/aa367066) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 V tématu [first_is –](../windows/first-is.md) příklad určení oddíl pole.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Pole v `struct` nebo **– typ union**, rozhraní parametr, rozhraní – metoda|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [first_is –](../windows/first-is.md)   
 [max_is –](../windows/max-is.md)   
 [length_is –](../windows/length-is.md)   
 [size_is](../windows/size-is.md)   
