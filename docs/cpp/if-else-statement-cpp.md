---
title: "if-else – příkaz (C++) | Microsoft Docs"
ms.custom: 
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- else_cpp
- if_cpp
dev_langs: C++
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
- if keyword [C++], if-else
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 96233323e5a95f88a43fb56162393238f8c2e091
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="if-else-statement-c"></a>if-else – příkaz (C++)
Ovládá podmíněné větvení. Příkazy v *bloku v případě* jsou vykonány pouze v případě *výraz if* jehož výsledkem je hodnota nulová (nebo `true`). Pokud hodnota *výraz* nenulový, *statement1* jsou vykonány jiné příkazy v bloku a else bloku, pokud existuje, bude přeskočena. Pokud hodnota *výraz* rovná nule, pak pokud bloku se přeskočí a else bloku, pokud existuje, je proveden. Výrazy, které vyhodnotí jako nulová
- `true`
- ukazatel jinou hodnotu než null
- žádné jiné hodnoty než nula aritmetické, nebo 
- Zadejte typ třídy, který definuje konverzi jednoznačným aritmetické, logická hodnota nebo ukazatel. (Informace o převody najdete v tématu [standardní převody](../cpp/standard-conversions.md).)   
  
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
```  
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
## <a name="if-statement-with-an-initializer"></a>Pokud příkaz s inicializátoru
**Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): **Pokud** příkaz může také obsahovat výraz, který deklaruje a inicializuje proměnnou s názvem. Používejte tento formulář příkaz v případě, když proměnné je potřeba jenom v rámci oboru bloku v případě. 

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

 Ve všech typech **Pokud** příkaz *výraz*, která může mít libovolnou hodnotu kromě strukturou, vyhodnotí, včetně všech vedlejší účinky. Ovládací prvek předává z **Pokud** příkaz, který má další příkaz v programu Pokud jeden z *příkaz*s obsahuje [zalomení](../cpp/break-statement-cpp.md), [pokračovat](../cpp/continue-statement-cpp.md), nebo [goto](../cpp/goto-statement-cpp.md).  
  
 **Else** klauzuli `if...else` příkazu je přidružen na nejbližší předchozí **Pokud** příkaz ve stejném oboru, který nemá odpovídající **else** příkaz.   

## <a name="constexpr-if-statements"></a>constexpr Pokud příkazy
**Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): V šablonách funkce, můžete použít **constexpr Pokud** příkaz větvení rozhodnout kompilace bez nutnosti uchýlit k více přetížení funkce. Můžete například napsat jedné funkce této obslužné rutiny parametr rozbalování, (je vyžadována žádné přetížení nula parametr): 

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
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [switch – příkaz (C++)](../cpp/switch-statement-cpp.md)