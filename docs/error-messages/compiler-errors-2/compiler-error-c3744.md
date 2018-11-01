---
title: Chyba kompilátoru C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 407ed4b30b55b63aa9bf36de9f8675a531d70534
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516230"
---
# <a name="compiler-error-c3744"></a>Chyba kompilátoru C3744

__unhook musí mít aspoň 3 argumenty pro spravované události.

[__Unhook](../../cpp/unhook.md) funkce musí mít tři parametry při použití v programu, který je kompilován pro spravované rozšíření jazyka C++.

`__hook` a `__unhook` nejsou kompatibilní s/CLR programování. Místo toho použijte operátory += a-=.

C3744 dosažitelný pouze pomocí možnosti kompilátoru zastaralé **oldSyntax**.
