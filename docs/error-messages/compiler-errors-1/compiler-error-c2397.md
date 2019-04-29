---
title: Compiler Error C2397
ms.date: 11/04/2016
f1_keywords:
- C2397
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
ms.openlocfilehash: 61f23269e0b6ed65a485f11e49e492d2248b8a42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378931"
---
# <a name="compiler-error-c2397"></a>Compiler Error C2397

Převod z 'type_1' na 'type_2' vyžaduje zúžení převodu

Při použití jednotnou inicializaci byl nalezen implicitní zužující převod.

Jazyk C umožňuje implicitní zužující převody přiřazení a inicializace a C++ řídí barvy, i když neočekávané zúžení je příčinou chyby mnoho kódu. Chcete-li kód bezpečnější, C++ standard vyžaduje diagnostické zprávy při výskytu zužující převod v inicializačního seznamu. V jazyce Visual C++ diagnostiky je chyba kompilátoru C2397 při použití syntaxe podporované od jednotné inicializace v sadě Visual Studio 2015. Kompilátor generuje [upozornění kompilátoru (úroveň 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) při používání seznamu nebo syntaxe agregační inicializace podporuje Visual Studio 2013.

Zužující převod může být v pořádku, pokud víte, že možné rozsahu hodnot převedený vejde do cíle. V takovém případě znáte více než kompilátor. Pokud provedete zužující převod záměrně, ujistěte se, vaše záměry explicitní pomocí statické přetypování. V opačném případě tuto chybovou zprávu téměř vždy označuje, že máte chybu v kódu. Můžete to napravit tak, že objekty, které je inicializovat mít typy, které jsou dostatečně velký, aby zpracovávat vstupy.

Následující ukázka generuje C2397 a ukazuje jeden způsob, jak ho opravit:

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