---
title: "Nestandardní chování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 73b60bbdbd38738f8cb5d127b464b14465de413b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nonstandard-behavior"></a>Nestandardní chování
V následujících oddílech jsou uvedeny některé z míst, kde implementace Visual C++ jazyka C++ nesplňuje standard C++. Čísla oddílů, která jsou uvedena níže, odkazují na čísla oddílů ve standardu C++ (ISO/IEC 14882:2011(E)).  
  
 Je uveden seznam omezení kompilátoru, která se liší od definované ve verzi C++ standard v [omezení kompilátoru](../cpp/compiler-limits.md).  
  
## <a name="covariant-return-types"></a>Kovariantní návratové typy  
 Virtuální základní třídy nejsou podporovány jako kovariantní návratové typy, pokud virtuální funkce má proměnný počet argumentů. To není v souladu s oddílem 10.3, odstavcem 7 specifikace C++ ISO. Následující ukázka nelze kompilovat, udělíte Chyba kompilátoru [C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md)  
  
```cpp  
// CovariantReturn.cpp  
class A   
{  
   virtual A* f(int c, ...);   // remove ...  
};  
  
class B : virtual A  
{  
   B* f(int c, ...);   // C2688 remove ...  
};  
```  
  
## <a name="binding-nondependent-names-in-templates"></a>Názvy nezávislé vazby v šablonách  
 Kompilátor Visual C++ aktuálně nepodporuje názvy nezávislé vazby při počáteční analýze šablony. To není v souladu s oddílem 14.6.3 specifikace C++ ISO. To může způsobit přetížení deklarované poté, co má být šablona (ale předtím, než je vytvořena instance šablony) zobrazena.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
namespace N {  
   void f(int) { cout << "f(int)" << endl;}  
}  
  
template <class T> void g(T) {  
    N::f('a');   // calls f(char), should call f(int)  
}  
  
namespace N {  
    void f(char) { cout << "f(char)" << endl;}  
}  
  
int main() {  
    g('c');  
}  
// Output: f(char)  
  
```  
  
## <a name="function-exception-specifiers"></a>Specifikátory výjimek funkcí  
 Specifikátory výjimek funkcí než `throw()` analyzovat, ale není použit. To není v souladu s oddílem 15.4 specifikace ISO C++. Příklad:  
  
```cpp  
void f() throw(int); // parsed but not used  
void g() throw();    // parsed and used  
```  
  
 Další informace o specifikace výjimek najdete v tématu [specifikace výjimek](../cpp/exception-specifications-throw-cpp.md).  
  
## <a name="chartraitseof"></a>char_traits::eof()  
 Standardní C++ stavů, které [char_traits::eof](../standard-library/char-traits-struct.md#eof) nesmí odpovídat platným `char_type` hodnotu. Visual C++ compiler vynucuje toto omezení pro typ `char`, ale ne pro typ `wchar_t`. To není v souladu s požadavky tabulky 62 v oddíle 12.1.1 specifikace C++ ISO. To zachycuje níže uvedený příklad.  
  
```cpp  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    char_traits<char>::int_type int2 = char_traits<char>::eof();  
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;  
  
    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();  
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;  
}  
```  
  
## <a name="storage-location-of-objects"></a>Umístění úložiště objektů  
 Standard C++ (odstavec 6 oddílu 1.8) vyžaduje jedinečná umístění úložiště objektů jazyka C++. V jazyce Visual C++ však existují případy, kde typy bez datových členů budou sdílet umístění úložiště s jinými typy po dobu životnosti objektu.