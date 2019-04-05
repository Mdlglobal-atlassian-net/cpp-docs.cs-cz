---
title: inline_recursion
ms.date: 11/04/2016
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 80ffabc6ac7c95fd7d9fb4e62bea38c2a04b04f0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026909"
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

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[inline_depth](../preprocessor/inline-depth.md)<br/>
[/Ob (rozbalení vložené funkce)](../build/reference/ob-inline-function-expansion.md)