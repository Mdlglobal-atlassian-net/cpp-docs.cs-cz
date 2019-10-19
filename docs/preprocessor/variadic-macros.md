---
title: Makra variadické
ms.date: 10/17/2019
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
ms.openlocfilehash: de4d3a7f03f613cb058e564664f01837df23aefb
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587886"
---
# <a name="variadic-macros"></a>Makra variadické

Makra variadic jsou makra podobná funkcím, které obsahují proměnný počet argumentů.

## <a name="remarks"></a>Poznámky

Chcete-li použít makra variadické, mohou být tři tečky zadány jako konečný formální argument v definici makra a náhradní identifikátor `__VA_ARGS__` lze použít v definici pro vložení dalších argumentů.  `__VA_ARGS__` se nahradí všemi argumenty, které se shodují se třemi tečkami, včetně čárky mezi nimi.

Standard jazyka C určuje, že se třemi tečkami musí být předán alespoň jeden argument, aby bylo zajištěno, že makro nebude přeloženo na výraz s koncovou čárkou. Tradiční implementace společnosti C++ Microsoft potlačuje koncovou čárku, pokud se tři tečky nepředávají žádné argumenty. Pokud je nastavena možnost kompilátoru `/experimental:preprocessor`, není koncová čárka potlačena.

## <a name="example"></a>Příklad

```cpp
// variadic_macros.cpp
#include <stdio.h>
#define EMPTY

#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }
#define CHECK3(...) { printf(__VA_ARGS__); }
#define MACRO(s, ...) printf(s, __VA_ARGS__)

int main() {
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print

    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");

    // always invokes printf in the macro
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");

    MACRO("hello, world\n");

    MACRO("error\n", EMPTY); // would cause error C2059, except VC++
                             // suppresses the trailing comma
}
```

```Output
here are some varargs1(1)
here are some varargs2(4)
here are some varargs3(5)
hello, world
error
```

## <a name="see-also"></a>Viz také:

[Makra (C/C++)](../preprocessor/macros-c-cpp.md)
