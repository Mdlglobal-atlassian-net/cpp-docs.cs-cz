---
title: Kompilátor upozornění (úroveň 1) C4036
ms.date: 11/04/2016
f1_keywords:
- C4036
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
ms.openlocfilehash: 632e88bb64568c97e937e83e177598054a954f22
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609570"
---
# <a name="compiler-warning-level-1-c4036"></a>Kompilátor upozornění (úroveň 1) C4036

Nepojmenované "typ" jako skutečný parametr

Pro struktury, sjednocení, výčet nebo třídu použitou jako skutečný parametr je zadaný žádný název typu. Pokud používáte [/Zg](../../build/reference/zg-generate-function-prototypes.md) generovat prototypy funkcí, kompilátor vydá toto upozornění a komentáře výstupní formální parametr v generované prototypu.

Zadejte název typu, chcete-li vyřešit tato upozornění.

## <a name="example"></a>Příklad

Následující ukázka generuje C4036.

```
// C4036.c
// compile with: /Zg /W1
// D9035 expected
typedef struct { int i; } T;
void f(T* t) {}   // C4036

// OK
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```