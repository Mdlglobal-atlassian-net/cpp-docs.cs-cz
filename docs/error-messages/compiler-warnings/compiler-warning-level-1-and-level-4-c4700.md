---
title: "Upozornění (úroveň 1 a 4) C4700 kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4700
dev_langs:
- C++
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00b871d6199338cc3040d6bddedb85f8732dfccd
ms.sourcegitcommit: 4e416049665819ac62f5300ddf86e94adede4ba0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>Upozornění kompilátoru (úroveň 1 a 4) C4700

> Neinicializovaný místní proměnné '*název*se používá

Místní proměnná *název* byl *používá*, tedy číst z, než má byla přiřazena hodnota. C a C++ místní proměnné nejsou inicializovány ve výchozím nastavení. Neinicializovaný proměnné může obsahovat libovolnou hodnotu a jejich používání vede k nedefinované chování. Upozornění C4700 téměř vždy označuje chybu, která může způsobit nepředvídatelné výsledky nebo dojde k chybě v programu.

Chcete-li tento problém vyřešit, můžete inicializovat místní proměnné, když jsou deklarovány nebo k nim přiřadíte hodnotu, než se používají. Funkce slouží k inicializaci proměnné, který se předá jako parametr odkazu, nebo při jeho adresy se předá jako parametr ukazatele.

## <a name="example"></a>Příklad

Tato ukázka generuje C4700, pokud se předtím, než se inicializují a zobrazuje druh hodnota paměti, která může způsobit používá proměnné t, u a v. Proměnné x, y a proveďte z není způsobit upozornění, protože se inicializují před použitím:

```cpp
// c4700.cpp
// compile by using: cl /EHsc /W4 c4700.cpp
#include <iostream>

// function takes an int reference to initialize
void initialize(int& i)
{
    i = 21;
}

int main()
{
    int s, t, u, v;   // Danger, uninitialized variables

    s = t + u + v;    // C4700: t, u, v used before initialization
    std::cout << "Value in s: " << s << std::endl;

    int w, x;         // Danger, uninitialized variables
    initialize(x);    // fix: call function to init x before use
    int y{10};        // fix: initialize y, z when declared
    int z{11};        // This C++11 syntax is recommended over int z = 11;

    w = x + y + z;    // Okay, all values initialized before use
    std::cout << "Value in w: " << w << std::endl;
}
```

Pokud je tento kód spustit, t, u a v Neinicializovaný a výstup s nepředvídatelným:

```Output
Value in s: 37816963
Value in w: 42
```
