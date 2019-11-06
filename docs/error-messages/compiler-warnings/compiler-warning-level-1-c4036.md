---
title: Upozornění kompilátoru (úroveň 1) C4036
ms.date: 11/04/2016
f1_keywords:
- C4036
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
ms.openlocfilehash: 858cf089d3f681438a221115c8758c38a5cf8d9a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626271"
---
# <a name="compiler-warning-level-1-c4036"></a>Upozornění kompilátoru (úroveň 1) C4036

Nepojmenovaný typ jako skutečný parametr

Není zadán žádný název typu pro strukturu, sjednocení, výčet nebo třídu použitou jako skutečný parametr. Pokud k vygenerování prototypů funkcí používáte [/ZG](../../build/reference/zg-generate-function-prototypes.md) , kompilátor vydá toto upozornění a Zakomentovat formální parametr ve vygenerovaném prototypu.

Chcete-li vyřešit toto upozornění, zadejte název typu.

## <a name="example"></a>Příklad

Následující ukázka generuje C4036.

```c
// C4036.c
// compile with: /Zg /W1
// D9035 expected
typedef struct { int i; } T;
void f(T* t) {}   // C4036

// OK
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```