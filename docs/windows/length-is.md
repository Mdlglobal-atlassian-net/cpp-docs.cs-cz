---
title: length_is – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.length_is
dev_langs:
- C++
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d41c2c4747f69b5ddfae4cd5863c072cd2316ec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879604"
---
# <a name="lengthis"></a>length_is
Určuje počet elementů pole přenášet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ length_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *výraz*  
 Jeden nebo více výrazů jazyka C. Prázdný argument sloty jsou povoleny.  
  
## <a name="remarks"></a>Poznámky  
 **Length_is –** atribut C++ má stejné funkce jako [length_is –](http://msdn.microsoft.com/library/windows/desktop/aa367068) MIDL atribut.  
  
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
 [last_is –](../windows/last-is.md)   
 [size_is](../windows/size-is.md)   
