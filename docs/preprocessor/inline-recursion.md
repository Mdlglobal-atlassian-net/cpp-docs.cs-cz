---
title: inline_recursion – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 0169e06e8e47f7b0a7b3f73e809ddc988bcf1e95
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220949"
---
# <a name="inline_recursion-pragma"></a>inline_recursion – direktiva pragma

Řídí vložené rozšíření přímých nebo vzájemně rekurzivních volání funkce.

## <a name="syntax"></a>Syntaxe

> **#pragma inline_recursion (** [{ **on** | **off** }] **)**

## <a name="remarks"></a>Poznámky

Tuto direktivu pragma použijte k řízení funkcí [](../cpp/inline-functions-cpp.md) označených jako inline a [__inline](../cpp/inline-functions-cpp.md) nebo Functions, které kompilátor `/Ob2` automaticky rozbalí do možnosti. Použití této direktivy pragma vyžaduje nastavení možnosti kompilátoru [/ob](../build/reference/ob-inline-function-expansion.md) na hodnotu 1 nebo 2. Výchozí stav pro **inline_recursion** je vypnutý. Tato direktiva pragma se projeví při prvním volání funkce poté, co je direktiva pragma zobrazena a nemá vliv na definici funkce.

Direktiva pragma **inline_recursion** řídí způsob, jakým jsou rozbaleny rekurzivní funkce. Pokud je **inline_recursion** vypnuté, a Pokud vložená funkce zavolá sám sebe, buď přímo nebo nepřímo, je funkce rozbalena pouze jednou. Pokud je **inline_recursion** zapnuto, je funkce rozbalena několikrát, dokud nedosáhne hodnoty nastavené direktivou pragma [inline_depth](../preprocessor/inline-depth.md) , výchozí hodnotou pro rekurzivní funkce, která je `inline_depth` definována direktivou pragma nebo omezením kapacity.

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_depth](../preprocessor/inline-depth.md)\
[/Ob (rozbalení vložené funkce)](../build/reference/ob-inline-function-expansion.md)
