---
title: "range_adapter – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::range_adapter
dev_langs: C++
helpviewer_keywords: range_adapter class [STL/CLR]
ms.assetid: 3fbe2a65-1216-46a0-a182-422816b80cfb
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5455c1912b3108291f530ee9488a4e0078ba39a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rangeadapter-stlclr"></a>range_adapter (STL/CLR)
Třída šablony, která zabalí pár iterátory, které se používají k implementaci několik rozhraní základní třídy knihovny (BCL). Použijete range_adapter – k manipulaci s rozsah STL/CLR, jako by šlo BCL kolekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 ITER –  
 Typ přidružený k zabalené iterátory.  
  
## <a name="members"></a>Členové  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[range_adapter::range_adapter (STL/CLR)](../dotnet/range-adapter-range-adapter-stl-clr.md)|Vytvoří objekt adaptéru.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[range_adapter::Operator = (STL/CLR)](../dotnet/range-adapter-operator-assign-stl-clr.md)|Nahradí uložené iterator pár.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.Collections.IEnumerable>|Iteruje elementů v kolekci.|  
|<xref:System.Collections.ICollection>|Udržuje skupinu elementů.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Iteruje typové elementů v kolekci...|  
|<xref:System.Collections.Generic.ICollection%601>|Udržuje typové prvků.|  
  
## <a name="remarks"></a>Poznámky  
 Range_adapter – ukládá pár iterátory, které zase vymezují pořadí elementů. Objekt implementuje čtyři BCL rozhraní, které umožňují iteraci v rámci prvků, v pořadí. Tuto třídu šablony můžete použít k manipulaci s rozsahy STL/CLR podobně jako kontejnery BCL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – nebo adaptér >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [collection_adapter – (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [make_collection – (STL/CLR)](../dotnet/make-collection-stl-clr.md)