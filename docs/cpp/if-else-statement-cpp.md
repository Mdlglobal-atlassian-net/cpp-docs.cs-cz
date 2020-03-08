---
title: if-else – příkaz (C++)
ms.date: 07/20/2019
description: Použijte příkazy if-else v C++ k řízení podmíněného větvení.
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: 0e9de2d39e09e148c7e4f3ea82c3dadb173c2d0c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884147"
---
# <a name="if-else-statement-c"></a>if-else – příkaz (C++)

Ovládá podmíněné větvení. Příkazy v *bloku If* jsou spouštěny pouze v případě, že *výraz IF-Expression* je vyhodnocen jako nenulová hodnota (nebo true). Pokud je hodnota *výrazu* nenulová, *příkaz1* a všechny ostatní příkazy v bloku jsou spuštěny a blok else-Block, pokud je k dispozici, je vynechán. Pokud je hodnota *výrazu* nula, pak je if-Block vynechán a je proveden blok else-Block, pokud je k dispozici. Výrazy, které se vyhodnotí jako nenulové, jsou

- PRAVDA
- ukazatel, který není null,
- Jakákoli nenulová hodnota aritmetického typu nebo
- typ třídy, který definuje jednoznačnou konverzi na aritmetický typ, logickou hodnotu nebo typ ukazatele. (Informace o převodech naleznete v tématu [standardní převody](../cpp/standard-conversions.md).)

## <a name="syntax"></a>Syntaxe

```cpp
if ( expression )
{
   statement1;
   ...
}
else  // optional
{
   statement2;
   ...
}

// C++17 - Visual Studio 2017 version 15.3 and later:
if ( initialization; expression )
{
   statement1;
   ...
}
else  // optional
{
   statement2;
   ...
}

// C++17 - Visual Studio 2017 version 15.3 and later:
if constexpr (expression)
{
    statement1;
    ...
}
else  // optional
{
   statement2;
   ...
}
```

## <a name="example"></a>Příklad

```cpp
// if_else_statement.cpp
#include <iostream>

using namespace std;

class C
{
    public:
    void do_something(){}
};
void init(C){}
bool is_true() { return true; }
int x = 10;

int main()
{
    if (is_true())
    {
        cout << "b is true!\n";  // executed
    }
    else
    {
        cout << "b is false!\n";
    }

    // no else statement
    if (x == 10)
    {
        x = 0;
    }

    C* c;
    init(c);
    if (c)
    {
        c->do_something();
    }
    else
    {
        cout << "c is null!\n";
    }
}
```

## <a name="if_with_init"></a>If – příkaz s inicializátorem

**Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): příkaz **if** může obsahovat také výraz, který deklaruje a inicializuje pojmenovanou proměnnou. Tuto formu příkazu if-Statement použijte, pokud je proměnná požadována pouze v rámci rozsahu bloku If-Block.

## <a name="example"></a>Příklad

```cpp
#include <iostream>
#include <mutex>
#include <map>
#include <string>
#include <algorithm>

using namespace std;

map<int, string> m;
mutex mx;
bool shared_flag; // guarded by mx
void unsafe_operation() {}

int main()
{

    if (auto it = m.find(10); it != m.end())
    {
        cout << it->second;
        return 0;
    }

    if (char buf[10]; fgets(buf, 10, stdin))
    {
        m[0] += buf;
    }

    if (lock_guard<mutex> lock(mx); shared_flag)
    {
        unsafe_operation();
        shared_flag = false;
    }

    string s{ "if" };
    if (auto keywords = { "if", "for", "while" }; any_of(keywords.begin(), keywords.end(), [&s](const char* kw) { return s == kw; }))
    {
        cout << "Error! Token must not be a keyword\n";
    }
}
```

Ve všech formulářích příkazu **if** je *výraz*, který může mít libovolnou hodnotu s výjimkou struktury, vyhodnocen, včetně všech vedlejších účinků. Řízení se předává z příkazu **if** do dalšího příkazu v programu, pokud některý z *příkazů neobsahuje příkaz* [Break](../cpp/break-statement-cpp.md), [Continue](../cpp/continue-statement-cpp.md)nebo [goto](../cpp/goto-statement-cpp.md).

Klauzule **Else** příkazu `if...else` je přidružená k nejbližšímu předchozímu příkazu **if** ve stejném oboru, který nemá odpovídající příkaz **Else** .

## <a name="a-nameif_constexpr-if-constexpr-statements"></a><a name="if_constexpr">, pokud příkazy constexpr

**Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): v šablonách funkcí můžete použít příkaz **if constexpr** k provedení rozhodování o rozvětvení v době kompilace, aniž by bylo nutné se uchýlit k vícenásobným přetížením funkcí. Můžete například napsat jednu funkci, která zpracovává parametr unpacking (žádné přetížení nula parametrů není nutné):

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
    // handle t
    do_something(t);

    // handle r conditionally
    if constexpr (sizeof...(r))
    {
        f(r...);
    }
    else
    {
        g(r...);
    }
}
```

## <a name="see-also"></a>Viz také

[Příkazy výběru](../cpp/selection-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[switch – příkaz (C++)](../cpp/switch-statement-cpp.md)