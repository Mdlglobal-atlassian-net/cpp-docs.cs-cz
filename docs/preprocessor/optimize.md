---
title: Optimalizace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bff0e4cc40bfa0e355f348c02f01cb0c7445b596
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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