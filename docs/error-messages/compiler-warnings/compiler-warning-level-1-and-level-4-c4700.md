---
title: Upozornění kompilátoru (úroveň 1 a 4) C4700
ms.date: 02/21/2018
f1_keywords:
- C4700
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
ms.openlocfilehash: fa3326bd5ab495dbc4c54130bb168422eb827dce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300291"
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>Upozornění kompilátoru (úroveň 1 a 4) C4700

> Neinicializovaná lokální proměnná '*název*"použít

Lokální proměnná *název* byl *použít*, tedy četlo, před jeho má byla přiřazena hodnota. V jazyce C a C++ nejsou ve výchozím nastavení inicializována lokální proměnné. Neinicializované proměnné může obsahovat libovolnou hodnotu, a jejich používání vede k nedefinovanému chování. Upozornění C4700 téměř vždy označuje chybu, která může způsobit nepředvídatelné výsledky nebo chyby ve svém programu.

Chcete-li vyřešit tento problém, můžete inicializovat místní proměnné, když jsou deklarovány nebo přiřadit hodnotu je před jejich použití. Funkci lze použít k inicializaci proměnné, který je předán jako parametr odkazu, nebo když je adresa předávána jako ukazatel parametr.

## <a name="example"></a>Příklad

Tato ukázka vygeneruje C4700 při používání proměnných t, u a v předtím, než jsou inicializovány a zobrazuje druh uvolňování paměti hodnotu, která může způsobit. Proměnné x, y a proveďte z nevyvolá upozornění, protože jsou inicializovány před použitím:

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

Pokud je tento kód spustit, t, u a v neinicializované a výstup s nepředvídatelné:

```Output
Value in s: 37816963
Value in w: 42
```
