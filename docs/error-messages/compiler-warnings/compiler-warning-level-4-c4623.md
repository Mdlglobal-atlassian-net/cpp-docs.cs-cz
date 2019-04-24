---
title: Kompilátor upozornění (úroveň 4) C4623
ms.date: 11/04/2016
f1_keywords:
- C4623
helpviewer_keywords:
- C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
ms.openlocfilehash: d1b659a6aed593a2e3f01ac1b82e60878cb09c80
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220465"
---
# <a name="compiler-warning-level-4-c4623"></a>Kompilátor upozornění (úroveň 4) C4623

"`derived class`': výchozí konstruktor byl implicitně definovaný jako odstranit, protože výchozí konstruktor základní třídy je nedostupné nebo odstraněné

Konstruktor nebyl dostupný v základní třídě a pro odvozené třídy se nevygeneroval. Jakýkoliv pokus o vytvoření objektu tohoto typu v zásobníku způsobí chybu kompilátoru.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C4623.

```
// C4623.cpp
// compile with: /W4
#pragma warning(default : 4623)
class B {
   B();
};

class C {
public:
   C();
};

class D : public B {};   // C4623 - to fix, make B's constructor public
class E : public C {};   // OK - class C constructor is public

int main() {
   // D d;  will cause an error
}
```