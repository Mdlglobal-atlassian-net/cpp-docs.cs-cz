---
title: "Překlad názvů pro lokálně deklarované názvy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 743b88f3-de11-48f4-ae83-931449ea3886
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9561b1e0b270dd245b5617653d5cf8c909434a98
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="name-resolution-for-locally-declared-names"></a>Rozlišení názvů pro lokálně deklarované názvy

Na samotný název šablony lze odkazovat s argumenty šablony nebo bez nich. V rozsahu šablony třídy odkazuje samotný název na tuto šablonu. V rozsahu specializace šablony nebo částečné specializace odkazuje samotný název na tuto specializaci nebo částečnou specializaci. Na ostatní specializace nebo částečné specializace šablony se lze také odkazovat s příslušnými argumenty šablony.  
  
## <a name="example"></a>Příklad

 Následující kód ukazuje, že název šablony třídy A je v rozsahu specializace nebo částečné specializace interpretován různě.  
  
```cpp
// template_name_resolution3.cpp  
// compile with: /c  
template <class T> class A {  
   A* a1;   // A refers to A<T>  
   A<int>* a2;  // A<int> refers to a specialization of A.  
   A<T*>* a3;   // A<T*> refers to the partial specialization A<T*>.  
};  
  
template <class T> class A<T*> {  
   A* a4; // A refers to A<T*>.  
};  
  
template<> class A<int> {  
   A* a5; // A refers to A<int>.  
};  
```  
  
## <a name="example"></a>Příklad

 V případě konfliktu názvu mezi parametrem šablony a jiným objektem lze nebo nelze parametr šablony skrýt. Následující pravidla vám pomohou určit prioritu.  
  
 Parametr šablony je v rozsahu od bodu, kde se poprvé objeví, až do konce šablony třídy nebo funkce. Pokud se název znovu zobrazí v seznamu argumentů šablony nebo seznamu základních tříd, odkazuje na stejný typ. Ve standardním jazyce C++ nemohou být ve stejném oboru deklarovány žádné jiné názvy, které jsou stejné jako parametr šablony. Rozšíření společnosti Microsoft umožňuje redefinovat parametr šablony v rozsahu šablony. Následující příklad ukazuje použití parametru šablony v základní specifikaci šablony třídy.  
  
```cpp
// template_name_resolution4.cpp  
// compile with: /EHsc  
template <class T>  
class Base1 {};  
  
template <class T>  
class Derived1 : Base1<T> {};  
  
int main() {  
   // Derived1<int> d;  
}  
```  
  
## <a name="example"></a>Příklad

 Při definování členských funkcí šablony mimo šablonu třídy lze použít jiný název parametru šablony. Pokud definice členské funkce šablony používá jiný název parametru šablony než deklarace a název použitý v definici je v konfliktu s jiným členem deklarace, má člen v deklaraci šablony přednost.  
  
```cpp
// template_name_resolution5.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T> class C {  
public:  
   struct Z {  
      Z() { cout << "Z::Z()" << endl; }  
   };  
   void f();  
};  
  
template <class Z>  
void C<Z>::f() {  
   // Z refers to the struct Z, not to the template arg;  
   // Therefore, the constructor for struct Z will be called.  
   Z z;  
}  
  
int main() {  
   C<int> c;  
   c.f();  
}  
```  
  
```Output  
Z::Z()  
```  
  
## <a name="example"></a>Příklad

 Při definici funkce šablony nebo členské funkce mimo obor názvů, ve kterém byla šablona deklarována, má argument šablony přednost před názvy ostatních členů v oboru názvů.  
  
```cpp
// template_name_resolution6.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
namespace NS {  
   void g() { cout << "NS::g" << endl; }  
  
   template <class T> struct C {  
      void f();  
      void g() { cout << "C<T>::g" << endl; }  
   };  
};  
  
template <class T>  
void NS::C<T>::f() {  
   g(); // C<T>::g, not NS::g  
};  
  
int main() {  
   NS::C<int> c;  
   c.f();  
}  
```  
  
```Output  
C<T>::g  
```  
  
## <a name="example"></a>Příklad

 V definicích, které se nacházejí mimo deklaraci šablony třídy, pokud má šablona třídy základní třídu nezávislou na argumentu šablony a pokud základní třída nebo některý z jejích členů má stejný název jako argument šablony, pak název základní třídy nebo členu tento argument šablony skryje.  
  
```cpp
// template_name_resolution7.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct B {  
   int i;  
   void print() { cout << "Base" << endl; }  
};  
  
template <class T, int i> struct C : public B {  
   void f();  
};  
  
template <class B, int i>  
void C<B, i>::f() {  
   B b;   // Base class b, not template argument.  
   b.print();  
   i = 1; // Set base class's i to 1.  
}  
  
int main() {  
   C<int, 1> c;  
   c.f();  
   cout << c.i << endl;  
}  
```  
  
```Output  
Base  
1  
```  
  
## <a name="see-also"></a>Viz také

 [Překlad názvů](../cpp/templates-and-name-resolution.md)
