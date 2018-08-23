---
title: inline_depth | Dokumentace Microsoftu
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
ms.openlocfilehash: 8a6c8d05d326e11ecfef4df8d22cbf2b8d92bd77
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465388"
---
# <a name="inlinedepth"></a>inline_depth
Určuje hloubku, vloženého heuristického hledání tak, že žádná funkce nebude vložena, pokud je v hloubce (v grafu volání) větší než *n*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma inline_depth( [n] )  
```  
  
## <a name="remarks"></a>Poznámky  
 
Tato direktiva pragma řídí vkládání funkcí označených klíčovým slovem [vložené](../cpp/inline-functions-cpp.md) a [__inline](../cpp/inline-functions-cpp.md) nebo vložených automaticky `/Ob2` možnost.  
  
*n* může být hodnota mezi 0 a 255, kde 255 znamená neomezenou hloubku v grafu volání a nula zakazuje rozšiřování vkládáním.  Když *n* není zadán, je použita výchozí hodnota (254).  
  
**Inline_depth** – Direktiva pragma řídí počet, kolikrát lze řadu volání funkcí rozbalit. Je-li například hloubka vkládání čtyři a zavolá-li funkce A funkci B a funkce B zavolá funkci C, budou všechna tři volání rozbalena po vložení. Je-li však nejbližší počet rozbalení dva, jsou rozbaleny pouze funkce A a B a funkce C bude nadála volána.  
  
Chcete-li tuto direktivu pragma používat, je nutné nastavit `/Ob` – možnost kompilátoru na hodnotu 1 nebo 2. Nastavení hloubky pomocí této direktivy pragma se projeví při prvním volání funkce za direktivou.  
  
Během rozbalování lze hloubku vkládání snížit, ne však zvýšit. Pokud je hloubka šest a během rozbalování preprocesor nalezne **inline_depth** – Direktiva pragma s hodnotou osm, hloubka zůstává na hodnotě šest.  
  
**Inline_depth** – Direktiva pragma nemá žádný vliv na funkce označené klíčovým slovem `__forceinline`.  
  
> [!NOTE]
> Rekurzivní funkce mohou být nahrazeny vložením do maximální hloubky 16 volání.  
  
## <a name="see-also"></a>Viz také  
 
[Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
[inline_recursion](../preprocessor/inline-recursion.md)