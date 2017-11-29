---
title: "Funkce šablony | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- function templates
- templates, function
- function templates, about function templates
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4186329b164ab3fe6daba12ed3cbbd2008085fb9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="function-templates"></a>Šablony funkcí
Šablony třídy definují skupinu souvisejících tříd, které jsou založeny na typech argumentů předaných při vytváření instance třídy. Šablony funkce jsou podobné jako šablony třídy, ale definují skupinu funkcí. Pomocí šablon funkce lze určit sadu funkcí, které jsou založeny na stejném kódu, ale pracují s různými typy nebo třídami. Následující šablona funkce zamění dvě položky:  
  
```cpp
// function_templates1.cpp  
template< class T > void MySwap( T& a, T& b ) {  
   T c(a);   
   a = b;   
   b = c;  
}  
int main() {  
}  
```  
  
 Tento kód definuje skupinu funkcí, které zamění hodnoty argumentů. Z této šablony můžete vygenerovat funkce, které bude Prohodit **int** a **dlouho** typy a také uživatelem definované typy. Šablona funkce `MySwap` dokonce provede záměnu tříd, pokud je správně definován kopírovací konstruktor a operátor přiřazení těchto tříd.  
  
 Kromě toho šablony funkce zabrání v záměně objektů různých typů, protože kompilátor zná typy parametrů `a` a `b` v době kompilace.  
  
 Přestože lze tuto funkci pomocí ukazatelů typu void provést pomocí nešablonové funkce, verze s šablonou je typově bezpečná. Vezměte v úvahu následující volání:  
  
```cpp
int j = 10;  
int k = 18;  
CString Hello = "Hello, Windows!";  
MySwap( j, k );          //OK  
MySwap( j, Hello );      //error  
```  
  
 Druhé volání funkce `MySwap` vyvolá chybu v době kompilace, protože kompilátor nemůže funkci `MySwap` vygenerovat s parametry různých typů. Pokud byly použity ukazatele typu void, obě volání funkce se zkompilují správně, ale tato funkce nebude v době spuštění fungovat správně.  
  
 Explicitní určení argumentů šablony pro šablonu funkce je povoleno. Příklad:  
  
```cpp
// function_templates2.cpp  
template<class T> void f(T) {}  
int main(int j) {  
   f<char>(j);   // Generate the specialization f(char).  
   // If not explicitly specified, f(int) would be deduced.  
}  
```  
  
 Pokud je argument šablony explicitně zadán, jsou provedeny normální implicitní převody pro převod argumentu funkce na typ odpovídající parametrům šablony funkce. Ve výše uvedeném příkladu bude kompilátor převést `char j` na typ `int`.  
  
## <a name="see-also"></a>Viz také  
 [Šablony](../cpp/templates-cpp.md)   
 [Vytváření instancí šablon funkce](../cpp/function-template-instantiation.md)   
 [Explicitní vytvoření instance](../cpp/explicit-instantiation.md)   
 [Explicitní specializace šablon funkcí](../cpp/explicit-specialization-of-function-templates.md)