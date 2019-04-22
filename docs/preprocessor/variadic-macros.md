---
title: Variadická makra
ms.date: 11/04/2016
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
ms.openlocfilehash: da159ef979ccc38845064debebae55356bc9e9bd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022837"
---
# <a name="variadic-macros"></a>Variadická makra

Makra variadic jsou makra podobná funkcím, které obsahují proměnný počet argumentů.

## <a name="remarks"></a>Poznámky

Chcete-li použít makra variadic, lze zadat tři tečky jako poslední formální argument v definici makra a identifikátor nahrazení `__VA_ARGS__` může použít v definici pro vložení dalších argumentů.  `__VA_ARGS__` je nahrazen všemi argumenty, které odpovídají třem tečkám, včetně čárek mezi nimi.

Standard C určuje, že třem tečkám musí být předán alespoň jeden argument, aby se makro nepřekládalo na výraz s koncovou čárkou.  Implementace jazyka Visual C++ potlačí koncovou čárku, pokud nejsou třem tečkám předány žádné argumenty.

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