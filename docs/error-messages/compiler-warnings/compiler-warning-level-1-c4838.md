---
title: Kompilátor upozornění (úroveň 1) C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: dcb7062c751320a9f9c612b42caf6d018047d8d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380835"
---
# <a name="compiler-warning-level-1-c4838"></a>Kompilátor upozornění (úroveň 1) C4838

Převod z 'type_1' na 'type_2' vyžaduje zúžení převodu

Při použití inicializace agregace nebo seznamu byl nalezen implicitní zužující převod.

Jazyk C umožňuje implicitní zužující převody přiřazení a inicializace a C++ řídí barvy, i když neočekávané zúžení je příčinou chyby mnoho kódu. Chcete-li kód bezpečnější, C++ standard vyžaduje diagnostické zprávy při výskytu zužující převod v inicializačního seznamu. V jazyce Visual C++ je diagnostiky [Chyba kompilátoru C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md) při použití syntaxe jednotnou inicializaci podporované od v sadě Visual Studio 2015. Kompilátor vygeneruje upozornění C4838 při používání seznamu nebo syntaxe agregační inicializace podporuje Visual Studio 2013.

Zužující převod může být v pořádku, pokud víte, že možné rozsahu hodnot převedený vejde do cíle. V takovém případě znáte více než kompilátor. Pokud provedete zužující převod záměrně, ujistěte se, vaše záměry explicitní pomocí statické přetypování. Toto upozornění, jinak téměř vždy označuje, že máte chybu v kódu. Můžete to napravit tak, že objekty, které je inicializovat mít typy, které jsou dostatečně velký, aby zpracovávat vstupy.

Následující ukázka generuje C4838 a ukazuje jeden způsob, jak ho opravit:

```
// C4838.cpp -- C++ narrowing conversion diagnostics
// Compile by using: cl /EHsc C4838.cpp

struct S1 {
    int m1;
    double m2, m3;
};

void function_C4838(double d1) {
    double ad[] = { 1, d1 }; // OK
    int ai[] = { 1, d1 };    // warning C4838
    S1 s11 = { 1, 2, d1 };   // OK
    S1 s12 { d1, 2, 3 };     // warning C4838
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838
}
```