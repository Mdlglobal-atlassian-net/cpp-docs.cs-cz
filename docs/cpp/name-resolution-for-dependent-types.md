---
title: Překlad názvů u závislých typů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6421c634fb6d27bf79ea0ead9f0b6b8f5829f19
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402683"
---
# <a name="name-resolution-for-dependent-types"></a>Rozlišení názvů u závislých typů
Použití **typename** pro kvalifikované názvy v definicích šablon pro oznámení kompilátoru, že daný kvalifikovaný název identifikuje typ. Další informace najdete v tématu [typename](../cpp/typename.md).  
  
```cpp  
// template_name_resolution1.cpp  
#include <stdio.h>  
template <class T> class X  
{  
public:  
   void f(typename T::myType* mt) {}  
};  
  
class Yarg  
{  
public:  
   struct myType { };  
};  
  
int main()  
{  
   X<Yarg> x;  
   x.f(new Yarg::myType());  
   printf("Name resolved by using typename keyword.");  
}  
```  
  
```Output  
Name resolved by using typename keyword.  
```  
  
 Název vyhledávání nezávislých názvů zkontroluje názvy pro kontext definice šablony — v následujícím příkladu by tento kontext nalezl `myFunction(char)`– a kontext vytvoření instance šablony. V následujícím příkladu je vytvořena šablona instance ve funkci main. Proto `MyNamespace::myFunction` viditelná z místa vytvoření instance a je zvolena jako vhodnější shoda. Pokud by byla funkce `MyNamespace::myFunction` přejmenována, došlo by k zavolání funkce `myFunction(char)`.  
  
 Všechny názvy jsou vyhodnoceny jako závislé názvy. Přesto je doporučeno používat plně kvalifikované názvy, může-li dojít k jakýmkoli konfliktům.  
  
```cpp  
// template_name_resolution2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void myFunction(char)  
{  
   cout << "Char myFunction" << endl;  
}  
  
template <class T> class Class1  
{  
public:  
   Class1(T i)  
   {  
      // If replaced with myFunction(1), myFunction(char)  
      // will be called  
      myFunction(i);  
}  
};  
  
namespace MyNamespace  
{  
   void myFunction(int)  
   {  
      cout << "Int MyNamespace::myFunction" << endl;  
   }  
};  
  
using namespace MyNamespace;  
  
int main()  
{  
   Class1<int>* c1 = new Class1<int>(100);  
}  
```  
  
### <a name="output"></a>Výstup  
  
```Output  
Int MyNamespace::myFunction  
```  
  
### <a name="template-disambiguation"></a>Odstraňování mnohoznačnosti šablon  
 Aplikace [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] vynucuje pro odstraňování mnohoznačnosti s klíčovým slovem „template“ pravidla standardu C++98/03/11. V následujícím příkladu bude přijímat Visual C++ 2010 neodpovídající řádky a odpovídající řádky.  [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] přijímá pouze odpovídající řádky.  
  
```cpp  
#include <iostream>  
#include <ostream>  
#include <typeinfo>  
using namespace std;  
  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    #if defined(NONCONFORMANT)  
        typedef typename AY::Rebind<X>::Other AX; // nonconformant  
    #elif defined(CONFORMANT)  
        typedef typename AY::template Rebind<X>::Other AX; // conformant  
    #else  
        #error Define NONCONFORMANT or CONFORMANT.  
    #endif  
};  
  
int main() {  
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;  
}  
```  
  
 Shoda s pravidly odstraňování mnohoznačnosti je požadována, protože jazyk C++ standardně předpokládá, že typ `AY::Rebind` není šablona, proto kompilátor interpretuje následující znak „`<`“ jako znak „menší než“. Pro správnou analýzu znaku „`Rebind`“ jako ostré závorky musí kompilátor vědět, že typ `<` je šablona.  
  
## <a name="see-also"></a>Viz také:  
 [Překlad názvů](../cpp/templates-and-name-resolution.md)