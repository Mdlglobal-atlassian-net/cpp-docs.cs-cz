---
title: Upozornění kompilátoru (úroveň 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: d5bee2eb874b965ff99e3dc0038d63d65b346318
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164349"
---
# <a name="compiler-warning-level-1-c4033"></a>Upozornění kompilátoru (úroveň 1) C4033

klíčové slovo Function musí vracet hodnotu.

Funkce nevrací hodnotu. Vrátí se Nedefinovaná hodnota.

Funkce, které používají `return` bez návratové hodnoty, musí být deklarovány jako typ `void`.

Tato chyba je určena pro kód jazyka C.

Následující ukázka generuje C4033:

```c
// C4033.c
// compile with: /W1 /LD
int test_1(int x)   // C4033 expected
{
   if (x)
   {
      return;   // C4033
   }
}
```
