---
title: Kompilátor upozornění (úroveň 4) C4625
ms.date: 11/04/2016
f1_keywords:
- C4625
helpviewer_keywords:
- C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
ms.openlocfilehash: edcb43bf11c073e6ce721ba999fd99d28a8df15d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563069"
---
# <a name="compiler-warning-level-4-c4625"></a>Kompilátor upozornění (úroveň 4) C4625

'derived class': kopírovací konstuktor byl implicitně definovaný jako odstranit, protože kopírovací konstruktor základní třídy je nedostupné nebo odstraněné

Kopírovací konstruktor se odstranil nebo není k dispozici v základní třídě a proto se nevygeneroval pro odvozenou třídu. Jakýkoliv pokus o kopírování objektu tohoto typu způsobí chybu kompilátoru.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C4625 a ukazuje, jak ho opravit.

```
// C4625.cpp
// compile with: /W4 /c
#pragma warning(default : 4625)

struct A {
   A() {}

private:
   A(const A&) {}
};

struct C : private virtual A {};
struct B :  C {};   // C4625 no copy constructor

struct D : A {};
struct E :  D {};   // OK
```