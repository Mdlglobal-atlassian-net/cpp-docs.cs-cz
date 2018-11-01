---
title: Kompilátor upozornění (úroveň 1) C4743
ms.date: 11/04/2016
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: d17fd65f1108aab6e3ce97ec75c0ffb899c06cda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441844"
---
# <a name="compiler-warning-level-1-c4743"></a>Kompilátor upozornění (úroveň 1) C4743

"*typ*"má jinou velikost v"*file1*"a"*file2*': *číslo* a *číslo* bajtů

Externí proměnné odkazovat nebo definované ve dvou souborech má různé typy v těchto souborech a kompilátor určili, že velikost proměnné v *file1* se liší od velikost proměnné v *file2*.

To se důležité nestane, pokud toto upozornění může být generována pro jazyk C++. Pokud deklarujete stejné typy se stejným názvem ve dvou různých souborech, pokud tyto deklarace obsahovat virtuální funkce, a pokud deklarace nejsou stejné, kompilátor může vygenerovat upozornění C4744 pro tabulky virtuálních funkcí. Upozornění dochází, protože existují dvě tabulky různé velikosti virtuálních funkcí pro stejného typu a linkeru musíte zvolit jeden z nich začlenit do spustitelného souboru.  Je možné, že může dojít k programu volání nesprávné virtuální funkce.

Pokud chcete vyřešit toto upozornění, použijte stejné definice typu nebo používat jiné názvy typů nebo proměnné.

## <a name="example"></a>Příklad

Tato ukázka obsahuje jednu definici typu.

```
// C4743a.cpp
// compile with: /c
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
};

void C::f1(void) {}
void C::f2(void) {}
void C::f3(void) {}
C q;
```

## <a name="example"></a>Příklad

Následující ukázka generuje C4743.

```
// C4743b.cpp
// compile with: C4743a.cpp /W1 /GL /O2
// C4743 expected
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
    virtual void f4(void);
    virtual void f5(void);
};

void C::f4(void) {}
void C::f5(void) {}
C x;

int main() {}
```