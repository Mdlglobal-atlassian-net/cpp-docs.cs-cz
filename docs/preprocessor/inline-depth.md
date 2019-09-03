---
title: inline_depth – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
ms.openlocfilehash: be57178280e278683b85db1413ff5724b5260aef
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220980"
---
# <a name="inline_depth-pragma"></a>inline_depth – direktiva pragma

Určuje vloženou hloubku heuristického hledání. Funkce s hloubkou v grafu volání větším, než je zadaná hodnota, není vložena.

## <a name="syntax"></a>Syntaxe

> **#pragma inline_depth (** [ *n* ] **)**

## <a name="remarks"></a>Poznámky

Tato direktiva pragma řídí vkládání funkcí označených [](../cpp/inline-functions-cpp.md) jako inline a [__inline](../cpp/inline-functions-cpp.md), nebo vložených `/Ob` automaticky pod možností.

hodnota *n* může být v rozmezí 0 až 255, kde 255 znamená neomezenou hloubku v grafu volání. Hodnota 0 znemožňuje vložené rozšíření. Není-li zadána hodnota *n* , je použita výchozí hodnota 254.

Direktiva pragma **inline_depth** řídí počet, kolikrát lze rozšířit řadu volání funkcí. Například Předpokládejme, že vložená hloubka je 4. Pokud volání B a a B potom zavolá C, všechna tři volání budou rozbalená vložená. Pokud je však nejbližší rozšíření hloubky k disřádku 2, jsou rozbaleny pouze a a B a C zůstává jako volání funkce.

Chcete-li použít tuto direktivu pragma, `/Ob` je nutné nastavit možnost kompilátoru na hodnotu 1 nebo vyšší. Nastavení hloubky pomocí této direktivy pragma se projeví při prvním volání funkce za direktivou.

Vložená hloubka se dá během rozšiřování snížit, ale nezvyšuje se. Pokud je vložená hloubka 6 a během rozšiřování předprocesoru narazí na direktivu pragma **inline_depth** s hodnotou 8, zůstane hloubka 6.

Direktiva pragma **inline_depth** nemá žádný vliv na funkce označené `__forceinline`pomocí.

> [!NOTE]
> Rekurzivní funkce mohou být nahrazeny vložením do maximální hloubky 16 volání.

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_recursion](../preprocessor/inline-recursion.md)
