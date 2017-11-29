---
title: "size_is – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.size_is
dev_langs: C++
helpviewer_keywords: size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0e8b3f6e8df8ff7f493c50f52e1e839f4ca9baa9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sizeis"></a>size_is
Zadejte velikost paměti přidělené velikostí ukazatele, velikost ukazatele na velikosti ukazatele a jedním - nebo vícerozměrná pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ size_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *výraz*  
 Velikost paměti přidělené velikostí ukazatele.  
  
## <a name="remarks"></a>Poznámky  
 **Size_is –** atribut C++ má stejné funkce jako [size_is –](http://msdn.microsoft.com/library/windows/desktop/aa367164) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [first_is –](../windows/first-is.md) pro ukázku určení oddíl pole.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Pole v `struct` nebo **– typ union**, rozhraní parametr, rozhraní – metoda|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|**max_is –**|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [first_is –](../windows/first-is.md)   
 [last_is –](../windows/last-is.md)   
 [max_is –](../windows/max-is.md)   
 [length_is –](../windows/length-is.md)   