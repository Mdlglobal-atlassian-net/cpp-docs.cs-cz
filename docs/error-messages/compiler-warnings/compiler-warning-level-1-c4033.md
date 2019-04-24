---
title: Kompilátor upozornění (úroveň 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: bef57d99ec9057f8b008deabda00b8a422a9e509
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151692"
---
# <a name="compiler-warning-level-1-c4033"></a>Kompilátor upozornění (úroveň 1) C4033

'function' musí vracet hodnotu

Funkce nevrací hodnotu. Nedefinovaná hodnota se vrátí.

Funkce, které používají `return` bez návratové hodnoty musí být deklarovaný jako typ `void`.

Tato chyba je pro kód jazyka C.

Následující ukázka generuje C4033:

```
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