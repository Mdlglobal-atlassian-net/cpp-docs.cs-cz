---
title: "inline_recursion – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
dev_langs: C++
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 36d7d65ea6c36c81654feda020fc05d777ac3d33
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="inlinerecursion"></a>inline_recursion
Řídí vložené rozšíření přímých nebo vzájemně rekurzivních volání funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma inline_recursion( [{on | off}] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Použití této – Direktiva pragma pro funkce řízení označen jako [vložené](../cpp/inline-functions-cpp.md) a [__inline](../cpp/inline-functions-cpp.md) nebo funkce, které kompilátor automaticky rozšíří v rámci /Ob2 možnost. Vyžaduje tato direktiva pragma [/Ob](../build/reference/ob-inline-function-expansion.md) nastavení – možnost kompilátoru 1 nebo 2. Výchozí stav pro direktivu pragma `inline_recursion` je vypnuto. Direktiva pragma se projeví při prvním volání funkce poté, co je zobrazena, a neovlivňuje definici funkce.  
  
 Direktiva pragma `inline_recursion` určuje, jak jsou rozbaleny rekurzivní funkce. Pokud je direktiva pragma `inline_recursion` vypnutá a vložená funkce zavolá sama sebe (buď přímo, nebo nepřímo), je funkce rozbalena pouze jednou. Pokud `inline_recursion` je, funkce je rozšířena několikrát, dokud nebude dosaženo hodnoty nastavené s [inline_depth –](../preprocessor/inline-depth.md) – Direktiva pragma, výchozí hodnota pro rekurzivní funkce, které je definované `inline_depth` omezený – Direktiva pragma nebo kapacitou .  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline_depth –](../preprocessor/inline-depth.md)   
 [/Ob (rozbalení vložené funkce)](../build/reference/ob-inline-function-expansion.md)