---
title: "Řešení přetížení volání šablony funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function templates overload resolution
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 64bc9371fcddad5f76f1474832a8d69188b60583
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overload-resolution-of-function-template-calls"></a>Rozlišení přetížení volání šablony funkce
Šablonu funkce můžete přetížení funkcí objektu bez šablony se stejným názvem. V tomto scénáři se volání funkce vyřeší první pomocí odvození argumentu šablony pro vytvoření instance šablony funkce s jedinečný specializace. Pokud se nezdaří odvození argumentu šablony, jiné přetížení funkce jsou považovány za vyřešit volání. Tyto další přetížení, také známé jako sada candidate zahrnují objektu bez šablony funkce a další funkce vytvořenou instanci šablony. Pokud odvození argumentu šablony úspěšné, generované funkce se porovná s jinými funkcemi určit nejlepší shodu, následující pravidla pro rozlišení přetížení. Další informace najdete v tématu [přetížení funkcí](function-overloading.md).  
  
## <a name="example"></a>Příklad

 Pokud je funkce objektu bez šablony stejně dobrý shoda pro šablonu funkce, funkce objektu bez šablony je zvoleno (Pokud explicitně byly zadány argumenty šablony), jak ve volání `f(1, 1)` v následujícím příkladu.  
  
```cpp
// template_name_resolution9.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void f(int, int) { cout << "f(int, int)" << endl; }  
void f(char, char) { cout << "f(char, char)" << endl; }  
  
template <class T1, class T2>  
void f(T1, T2)  
{  
   cout << "void f(T1, T2)" << endl;  
};  
  
int main()  
{  
   f(1, 1);   // Equally good match; choose the nontemplate function.  
   f('a', 1); // Chooses the template function.  
   f<int, int>(2, 2);  // Template arguments explicitly specified.  
}  
```  
  
```Output  
f(int, int)  
void f(T1, T2)  
void f(T1, T2)  
```  
  
## <a name="example"></a>Příklad

 Další příklad ukazuje, že přesně odpovídající funkce šablony je upřednostňovaný, pokud objektu bez šablony funkce vyžaduje převod.  
  
```cpp
// template_name_resolution10.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void f(int, int) { cout << "f(int, int)" << endl; }  
  
template <class T1, class T2>  
void f(T1, T2)  
{  
   cout << "void f(T1, T2)" << endl;  
};  
  
int main()  
{  
   long l = 0;  
   int i = 0;  
   // Call the template function f(long, int) because f(int, int)  
   // would require a conversion from long to int.  
   f(l, i);  
}  
```  
  
```Output  
void f(T1, T2)  
```  
  
## <a name="see-also"></a>Viz také

 [Překlad názvů](../cpp/templates-and-name-resolution.md)   
 [typename](../cpp/typename.md)   
 
