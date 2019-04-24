---
title: Kompilátor upozornění (úroveň 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 36a5032098c5caabb1b050833e487fd58679a782
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187228"
---
# <a name="compiler-warning-level-1-c4789"></a>Kompilátor upozornění (úroveň 1) C4789

> vyrovnávací paměť "*identifikátor*" velikosti *N* bajtů bude mít přeběhnutí; *M* bajtů se zapíše s posunem *L*

## <a name="remarks"></a>Poznámky

**C4789** upozorní o přetečení vyrovnávací paměti, když se používají konkrétní funkce jazyka C za běhu (CRT). Když jsou předávány parametry nebo přiřazení dojde ke ho může také nahlásit neshody velikost. Upozornění je možné, pokud jsou velikosti dat v době kompilace znám. Toto upozornění se používá v situacích, které může elude typické neshoda velikost dat zjišťování.

**C4789** vás upozorní, když se data zkopírovala do bloku dat, který je známý jako moc malé v době kompilace.

Upozornění v případě kopírování používá vnitřní formu některou z těchto funkcí CRT:

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy –](../../c-runtime-library/reference/memcpy-wmemcpy.md)

Upozornění se zobrazí také při přetypování parametr větší datový typ a pak proveďte přiřazení kopie z reference na lvalue.

Visual C++ může vytvořit toto upozornění pro cestu kódu, který se nikdy neprovede. Upozornění můžete dočasně zakázat s použitím `#pragma`, jak je znázorněno v tomto příkladu:

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

Tohoto idiomu uchovává Visual C++ ze generování upozornění pro tento konkrétní blok kódu. `#pragma warning(push)` Zachová stávající stav před `#pragma warning(disable: 4789)` změní. `#pragma warning(pop)` Obnoví vložené stavu a odebere účinky `#pragma warning(disable:4789)`. Další informace o C++ direktivy preprocesoru `#pragma`, naleznete v tématu [upozornění](../../preprocessor/warning.md) a [direktivy Pragma a klíčové slovo __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

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

Následující ukázka rovněž vygeneruje C4789.

```cpp
// C4789b.cpp
// compile with: /W1 /O2 /c
// processor: x86
short G;

void main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```