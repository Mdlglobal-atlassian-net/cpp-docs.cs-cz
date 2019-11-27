---
title: Upozornění kompilátoru (úroveň 4) C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: fcb66fca7e5b8708171849f885518c15b8355ac4
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541736"
---
# <a name="compiler-warning-level-4-c4239"></a>Upozornění kompilátoru (úroveň 4) C4239

používá se nestandardní rozšíření: token: převod z typu na typ.

Tento převod typu není povolený C++ standardem, ale tady je povolený jako rozšíření. Toto upozornění je vždy následováno alespoň jedním řádkem vysvětlení popisujícího porušení pravidla jazyka.

## <a name="example"></a>Příklad

Následující ukázka generuje C4239.

```cpp
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

```cpp
// C4239b.cpp
// compile with: /W4 /c
enum E { value };
struct S {
   E e : 2;
} s = { 5 };   // C4239
// try the following line instead
// } s = { (E)5 };
```