---
title: Upozornění kompilátoru (úroveň 1) C4036
ms.date: 11/04/2016
f1_keywords:
- C4036
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
ms.openlocfilehash: 812f36884d24ac988353dbcb18609d4c506e3110
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164258"
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
