---
title: Chyba kompilátoru C3744 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d644a621fc6d8e460e1b97e5baec360de8662365
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063720"
---
# <a name="compiler-error-c3744"></a>Chyba kompilátoru C3744

__unhook musí mít aspoň 3 argumenty pro spravované události.

[__Unhook](../../cpp/unhook.md) funkce musí mít tři parametry při použití v programu, který je kompilován pro spravované rozšíření jazyka C++.

`__hook` a `__unhook` nejsou kompatibilní s/CLR programování. Místo toho použijte operátory += a-=.

C3744 dosažitelný pouze pomocí možnosti kompilátoru zastaralé **oldSyntax**.
