---
title: Upozornění (úroveň 1) C4789 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4789
dev_langs:
- C++
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 167bca2a4596a738813309eceb7e22751b5584b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087328"
---
# <a name="compiler-warning-level-1-c4789"></a>Kompilátor upozornění (úroveň 1) C4789

> vyrovnávací paměť "*identifikátor*" velikosti *N* bajtů bude mít přeběhnutí; *M* bajtů se zapíše s posunem *L*

## <a name="remarks"></a>Poznámky

Upozorní při použití konkrétních funkcí (CRT) jazyka C za běhu přetečení vyrovnávací paměti parametry jsou předány a přiřazení provádějí, tak, aby objemy dat je známo, že v době kompilace. Toto upozornění se používá v situacích, které může elude typické neshoda velikost dat zjišťování.

Upozornění se zobrazí, když data, jejichž délka je znám v době kompilace, je zkopírován a umístit do bloku dat, jejíž velikost je v době kompilace znám příliš malá pro data. Kopie musíte to provést pomocí jedné z následujících funkcí CRT vnitřní formuláře:

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy –](../../c-runtime-library/reference/memcpy-wmemcpy.md)

Upozornění se zobrazí také při datový typ parametru se neshoduje s použitím přetypování, a pak pokus o přiřazení kopie z reference na lvalue.

Visual C++ může vytvořit toto upozornění pro cestu kódu, který se nikdy nespustí. Upozornění můžete dočasně zakázat s použitím `#pragma`, jak je znázorněno v tomto příkladu:

```cpp
#pragma(push)
#pragma warning ( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma(pop)
```

Visual C++ se takto zachová generování upozornění pro tento konkrétní blok kódu. `#pragma(push)` Zachová stávající stav před `#pragma warning(disable: 4789)` změní. `#pragma(pop)` Obnoví vložené stavu a odebere účinky `#pragma warning(disable:4789)`. Další informace o direktivě preprocesoru C++ `#pragma`, naleznete v tématu [upozornění](../../preprocessor/warning.md) a [direktivy Pragma a klíčové slovo __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

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