---
title: inline_recursion | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
dev_langs:
- C++
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 222cb7151d975219d0e92bd1270778586e89b4d3
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466094"
---
# <a name="inlinerecursion"></a>inline_recursion
Řídí vložené rozšíření přímých nebo vzájemně rekurzivních volání funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma inline_recursion( [{on | off}] )  
```  
  
## <a name="remarks"></a>Poznámky  
 
Použití této direktivy pragma ovládacího prvku funkce označené jako [vložené](../cpp/inline-functions-cpp.md) a [__inline](../cpp/inline-functions-cpp.md) nebo funkce, které kompilátor automaticky rozbalí v `/Ob2` možnost. Použití této direktivy pragma vyžaduje [/Ob](../build/reference/ob-inline-function-expansion.md) nastavení parametru kompilátoru 1 nebo 2. Výchozí stav pro **inline_recursion** je vypnuté. Direktiva pragma se projeví při prvním volání funkce poté, co je zobrazena, a neovlivňuje definici funkce.  
  
**Inline_recursion** – Direktiva pragma řídí, jak jsou rozbaleny rekurzivní funkce. Pokud **inline_recursion** je vypnuté, a Pokud vložená funkce zavolá sama sebe (buď přímo nebo nepřímo), funkce rozbalena pouze jednou. Pokud **inline_recursion** zapnutý, je funkce rozbalena vícekrát, dokud nedosáhne hodnoty nastavené direktivou [inline_depth](../preprocessor/inline-depth.md) – Direktiva pragma, výchozí hodnota pro rekurzivní funkce, který je definován `inline_depth` – Direktiva pragma, nebo omezením kapacity.  
  
## <a name="see-also"></a>Viz také  
 
[Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
[inline_depth](../preprocessor/inline-depth.md)   
[/Ob (rozbalení vložené funkce)](../build/reference/ob-inline-function-expansion.md)