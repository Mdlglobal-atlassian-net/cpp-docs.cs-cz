---
title: inline_depth – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
dev_langs:
- C++
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e40b9382abc8ee0fa0c003964eebe75bc075e473
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="inlinedepth"></a>inline_depth
Určuje hloubku vloženého heuristického hledání tak, že nebude vložena žádná funkce, nachází-li se v hloubce (v grafu volání) větší než `n`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma inline_depth( [n] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato direktiva pragma ovládací prvky vložené funkce, které jsou označeny [vložené](../cpp/inline-functions-cpp.md) a [__inline](../cpp/inline-functions-cpp.md) nebo automaticky v rámci možnost /Ob2 vloženou obslužnou.  
  
 Parametr `n` může nabývat hodnoty mezi 0 a 255, kde 255 znamená neomezenou hloubku v grafu volání a nula zakazuje rozšiřování vkládáním.  Není-li parametr `n` zadán, je použita výchozí hodnota (254).  
  
 **Inline_depth –** – Direktiva pragma řídí počet, kolikrát řady volání funkce se dají rozšířit. Je-li například hloubka vkládání čtyři a zavolá-li funkce A funkci B a funkce B zavolá funkci C, budou všechna tři volání rozbalena po vložení. Je-li však nejbližší počet rozbalení dva, jsou rozbaleny pouze funkce A a B a funkce C bude nadála volána.  
  
 Chcete-li tuto direktivu pragma používat, je zapotřebí nastavit možnost kompilátoru /Ob na hodnotu 1 nebo 2. Nastavení hloubky pomocí této direktivy pragma se projeví při prvním volání funkce za direktivou.  
  
 Během rozbalování lze hloubku vkládání snížit, ne však zvýšit. Pokud vložené hloubka je šest a během rozšiřování preprocesor dojde **inline_depth –** – Direktiva pragma s hodnotou osm hloubka zůstane šest.  
  
 **Inline_depth –** – Direktiva pragma nemá žádný vliv na funkce, které jsou označené jako `__forceinline`.  
  
> [!NOTE]
>  Rekurzivní funkce mohou být nahrazeny vložením do maximální hloubky 16 volání.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline_recursion](../preprocessor/inline-recursion.md)