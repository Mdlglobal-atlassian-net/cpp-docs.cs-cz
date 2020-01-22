---
title: Upozornění kompilátoru (úroveň 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 36278615631d017db1d1c2fc4eecf8c1612892de
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518397"
---
# <a name="compiler-warning-level-1-c4789"></a>Upozornění kompilátoru (úroveň 1) C4789

> vyrovnávací paměť '*identifikátor*' velikosti *N* bajtů bude přetečení. *M* bajtů se zapíše s posunem *L* .

## <a name="remarks"></a>Poznámky

**C4789** upozorňuje na přetečení vyrovnávací paměti při použití specifických funkcí jazyka C run-time (CRT). Může také nahlásit neshodu velikosti, pokud jsou předány parametry nebo jsou vytvořeny přiřazení. Upozornění je možné, pokud jsou velikosti dat známy v době kompilace. Toto upozornění je vhodné pro situace, které mohou elude typickou detekci neshody datových velikostí.

**C4789** upozorňuje na to, že se data zkopírují do bloku dat, u kterého se ví, že je v době kompilace příliš malá.

K upozornění dojde, pokud kopie používá vnitřní formu jedné z těchto funkcí CRT:

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

Upozornění se zobrazí také při přetypování parametru na větší datový typ a pak vytvořit přiřazení kopírování z odkazu lvalue.

Vizuál C++ může toto upozornění vygenerovat pro cestu kódu, která se nikdy nespustí. Upozornění můžete dočasně zakázat pomocí `#pragma`, jak je znázorněno v následujícím příkladu:

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

Tento idiom zachovává C++ vizuální generování upozornění pro konkrétní blok kódu. `#pragma warning(push)` zachovává stávající stav před tím, než ho `#pragma warning(disable: 4789)` změní. `#pragma warning(pop)` obnoví stav nabízení a odstraní důsledky `#pragma warning(disable:4789)`. Další informace o C++ direktivách preprocesoru `#pragma`naleznete v tématech [Upozornění](../../preprocessor/warning.md) a direktivy [pragma a klíčové slovo __pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4789.

```cpp
// C4789.cpp
// compile with: /Oi /W1 /c
#include <string.h>
#include <stdio.h>

int main()
{
    char a[20];
    strcpy(a, "0000000000000000000000000\n");   // C4789

    char buf2[20];
    memset(buf2, 'a', 21);   // C4789

    char c;
    wchar_t w = 0;
    memcpy(&c, &w, sizeof(wchar_t));
}
```

## <a name="example"></a>Příklad

Následující ukázka také generuje C4789.

```cpp
// C4789b.cpp
// compile with: /W1 /O2 /c
// processor: x86
short G;

int main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```
