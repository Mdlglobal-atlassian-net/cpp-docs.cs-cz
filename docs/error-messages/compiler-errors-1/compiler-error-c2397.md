---
title: Chyba kompilátoru C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 02a8bb09e0b22619bd61e6c4675057263a62a9d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206012"
---
# <a name="compiler-error-c2397"></a>Chyba kompilátoru C2397

převod z ' type_1 ' na ' type_2 ' vyžaduje zužující převod

Při použití jednotné inicializace byl nalezen implicitní zužující převod.

Jazyk C umožňuje implicitní zužující převody v přiřazeních a inicializaci a řídí se C++ podle potřeby, a to i v případě neočekávaného zúžení je příčinou mnoha chyb kódu. Aby byl kód zabezpečený, C++ vyžaduje se diagnostická zpráva, když dojde k zužujícímu převodu v inicializačním seznamu. V jazyce C++Visual Studio je diagnostika Chyba kompilátoru C2397 při použití jednotné syntaxe inicializace podporované od verze Visual Studio 2015. Kompilátor generuje [Upozornění kompilátoru (úroveň 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) při použití seznamu nebo agregační syntaxe inicializace, kterou podporuje Visual Studio 2013.

Zužující převod může být v pořádku, když víte, že možný rozsah přepočítaných hodnot se může vejít do cíle. V tomto případě znáte více než kompilátor. Pokud uděláte zužující převod záměrně, udělejte své záměry explicitně pomocí statického přetypování. V opačném případě tato chybová zpráva skoro vždy indikuje, že máte chybu ve vašem kódu. Můžete ji opravit tím, že zajistěte, aby objekty, které inicializujete, měly typy, které jsou dostatečně velké pro zpracování vstupů.

Následující ukázka generuje C2397 a ukazuje jeden ze způsobů, jak ji opravit:

```
// C2397.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C2397.cpp
#include <vector>

struct S1 {
    int m1;
    double m2, m3;
};

void function_C2397(double d1) {
    char c1 { 127 };          // OK
    char c2 { 513 };          // error C2397

    std::vector<S1> vS1;
    vS1.push_back({ d1, 2, 3 }); // error C2397

    // Possible fix if you know d1 always fits in an int
    vS1.push_back({ static_cast<int>(d1), 2, 3 });
}
```
