---
title: Optimalizace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 35b5147b3561df409906af9134ae4ec921a7d16b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="optimize"></a>optimize
Určuje optimalizace, které budou provedeny u jednotlivých funkcí pomocí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## <a name="remarks"></a>Poznámky  
 **Optimalizovat** – Direktiva pragma musí být uvedena mimo funkci a na první funkci definovanou po je vidět – Direktiva pragma se projeví. **Na** a **vypnout** argumenty zapnout zadaný v možnosti *optimalizace seznamu* zapnout nebo vypnout.  
  
 *Optimalizace seznamu* může být nula nebo více parametrů uvedené v následující tabulce.  
  
### <a name="parameters-of-the-optimize-pragma"></a>Parametry optimalizovat – direktiva Pragma  
  
|Parametry.|Typ optimalizace|  
|--------------------|--------------------------|  
|**g**|Povolte globální optimalizace.|  
|**s** nebo **t**|Zadejte krátký nebo rychlou pořadí počítač kódu.|  
|**y**|Generovat ukazatele na rámce v zásobníku programu.|  
  
 Toto jsou stejná písmena použít s [/O](../build/reference/o-options-optimize-code.md) – možnosti kompilátoru. Například následující – direktiva pragma odpovídá **/Os** – možnost kompilátoru:  
  
```  
#pragma optimize( "ts", on )  
```  
  
 Pomocí **optimalizovat** – Direktiva pragma s prázdný řetězec (**""**) je speciální forma direktivu:  
  
 Při použití **vypnout** parametr, se změní optimalizace, uvedené v tabulce výše v tomto tématu se vypnout.  
  
 Při použití **na** parametr resetuje optimalizace na ty, které jste zadali s [/O](../build/reference/o-options-optimize-code.md) – možnost kompilátoru.  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)