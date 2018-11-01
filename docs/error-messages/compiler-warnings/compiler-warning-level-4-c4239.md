---
title: Kompilátor upozornění (úroveň 4) C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: 067d1aef41280f4d14fe799e4f4ee26a9f1b9f5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451503"
---
# <a name="compiler-warning-level-4-c4239"></a>Kompilátor upozornění (úroveň 4) C4239

používá se nestandardní rozšíření: 'token': převod z 'type' na 'type'

Tento převod typu není povolený ve standardu jazyka C++, ale je povolena jako rozšíření. Toto upozornění je vždy následován alespoň jeden řádek vysvětlení popisující jazyk pravidla porušen.

## <a name="example"></a>Příklad

Následující ukázka generuje C4239.

```
// C4239.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

void func(void) {
   C & rC = C();   // C4239
   const C & rC2 = C();   // OK
   rC2;
}
```

## <a name="example"></a>Příklad

Převod z celočíselného typu na Výčtový typ není striktně povolený.

Následující ukázka generuje C4239.

```
// C4239b.cpp
// compile with: /W4 /c
enum E { value };
struct S {
   E e : 2;
} s = { 5 };   // C4239
// try the following line instead
// } s = { (E)5 };
```