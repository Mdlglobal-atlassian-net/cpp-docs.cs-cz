---
title: size_is | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.size_is
dev_langs:
- C++
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c6b5309d62db094bf706fe7d3d1bcec99c3ec9a9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645448"
---
# <a name="sizeis"></a>size_is
Zadejte velikost paměti přidělené pro velikosti ukazatele, velikosti ukazatele na velikosti ukazatele a single - nebo vícedimenzionální pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ size_is(  
   "expression"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *Výraz*  
 Velikost paměti přidělené pro velikosti ukazatele.  
  
## <a name="remarks"></a>Poznámky  
 **Size_is** C++ atribut má stejné funkce jako [size_is](http://msdn.microsoft.com/library/windows/desktop/aa367164) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [first_is –](../windows/first-is.md) ukázku toho, jak zadat část pole.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Pole v **struktura** nebo **sjednocení**, rozhraní parametr, rozhraní – metoda|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|`max_is`|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [– TypeDef, Enum, Union a struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [first_is –](../windows/first-is.md)   
 [last_is –](../windows/last-is.md)   
 [max_is –](../windows/max-is.md)   
 [length_is](../windows/length-is.md)   