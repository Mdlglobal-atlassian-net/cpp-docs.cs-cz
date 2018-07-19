---
title: if-else – příkaz (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/17/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- else_cpp
- if_cpp
dev_langs:
- C++
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
- if keyword [C++], if-else
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42174837f0f60f9a4e3ba9f19702210d6d34ccca
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947491"
---
# <a name="if-else-statement-c"></a>if-else – příkaz (C++)
Ovládá podmíněné větvení. Příkazy v *blok if* jsou spouštěny pouze v případě *výraz if* vyhodnotí jako nenulové hodnoty (nebo TRUE). Pokud hodnota *výraz* nenulové, *statement1* další příkazy v bloku jsou vykonány a else bloku, pokud jsou k dispozici, se přeskočí. Pokud hodnota *výraz* je nula, pak se přeskočila blok if a else bloku, pokud jsou k dispozici, je proveden. Jsou výrazy, které vedou na nenulovou
- HODNOTA TRUE
- nenulový ukazatel
- žádné jiné hodnoty než nula aritmetické, nebo 
- Zadejte typ třídy definující jednoznačný převod na aritmetický, logickou hodnotu nebo ukazatele. (Informace o převodech naleznete v tématu [standardní převody](../cpp/standard-conversions.md).)   
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
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

// Visual Studio 2017 version 15.3 and later:
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

// Visual Studio 2017 version 15.3 and later:
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
    void do_somthing(){}
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
## <a name="if-statement-with-an-initializer"></a>Pokud příkaz pomocí inicializátoru
**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): **Pokud** příkaz může také obsahovat výraz, který deklaruje a inicializuje proměnnou s názvem. Používejte tento formulář příkaz if proměnné je potřeba pouze v rámci oboru bloku if. 

```cpp
## Example  
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

 Ve všech typech **Pokud** příkazu *výraz*, což může mít libovolnou hodnotu, s výjimkou struktury, vyhodnocen včetně všechny vedlejší účinky. Ovládání přejde z **Pokud** příkaz dalšímu příkazu v programu není-li jeden z *příkaz*neobsahuje [přerušení](../cpp/break-statement-cpp.md), [pokračovat](../cpp/continue-statement-cpp.md), nebo [goto](../cpp/goto-statement-cpp.md).  
  
 **Else** klauzuli `if...else` je přidružena k nejbližšímu příkazu předchozí **Pokud** příkaz ve stejném oboru, který nemá odpovídající **else** příkaz.   

## <a name="constexpr-if-statements"></a>constexpr Pokud příkazy
**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): V rámci šablony funkce, můžete použít `constexpr if` příkaz rozhodnutí kompilace větvení bez nutnosti uchýlit se k více přetížení funkce. Můžete například napsat jedinou funkci tohoto popisovače parametru při rozbalování (je vyžadována žádná přetížená metoda parametr nula): 

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
// handle t
   do_something(t);

   // handle r conditionally
   constexpr if (sizeof...(r)) 
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
 [Příkazy výběru](../cpp/selection-statements-cpp.md)   
 [klíčová slova](../cpp/keywords-cpp.md)   
 [switch – příkaz (C++)](../cpp/switch-statement-cpp.md)