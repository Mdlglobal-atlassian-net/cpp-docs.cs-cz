---
title: Upozornění kompilátoru (úroveň 1) C4838
ms.date: 11/04/2016
f1_keywords:
- C4838
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
ms.openlocfilehash: 552c7d9e868ae531b1ff2ef20db7adfa813a4fbe
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051223"
---
# <a name="compiler-warning-level-1-c4838"></a>Upozornění kompilátoru (úroveň 1) C4838

převod z ' type_1 ' na ' type_2 ' vyžaduje zužující převod

Při použití agregace nebo Inicializace seznamu byl nalezen implicitní zužující převod.

Jazyk C umožňuje implicitní zužující převody v přiřazeních a inicializaci a řídí se C++ podle potřeby, a to i v případě neočekávaného zúžení je příčinou mnoha chyb kódu. Aby byl kód zabezpečený, C++ vyžaduje se diagnostická zpráva, když dojde k zužujícímu převodu v inicializačním seznamu. V jazyce C++Visual Studio je diagnostika [Chyba kompilátoru C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md) při použití jednotné syntaxe inicializace podporované od verze Visual Studio 2015. Kompilátor generuje upozornění C4838 při použití seznamu nebo agregace syntaxe inicializace, kterou podporuje Visual Studio 2013.

Zužující převod může být v pořádku, když víte, že možný rozsah přepočítaných hodnot se může vejít do cíle. V tomto případě znáte více než kompilátor. Pokud uděláte zužující převod záměrně, udělejte své záměry explicitně pomocí statického přetypování. V opačném případě tato varovná zpráva téměř vždy indikuje, že ve vašem kódu máte chybu. Můžete ji opravit tím, že zajistěte, aby objekty, které inicializujete, měly typy, které jsou dostatečně velké pro zpracování vstupů.

Následující ukázka generuje C4838 a ukazuje jeden ze způsobů, jak ji opravit:

```cpp
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