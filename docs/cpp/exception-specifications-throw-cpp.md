---
title: "Specifikace výjimek (throw) (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++], throw() vs. throw(...)
- throw keyword [C++], exception specifications
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7559bdf725727b79f99ed3bfcd4d6b7301528110
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exception-specifications-throw-noexcept-c"></a>Specifikace výjimek (throw, noexcept) (C++)
Specifikace výjimek jsou funkce jazyka C++, která označuje záměr programátora o typy výjimek, které mohou být přeneseny funkcí. Můžete určit, že funkce může nebo nemusí ukončete výjimkou pomocí *specifikace výjimek*. Kompilátor tyto informace můžete použít k optimalizaci volání funkce a ukončete program, pokud neočekávanou výjimku řídicí sekvence funkce. Existují dva druhy specifikace výjimek. *Noexcept specifikace* je nového v C ++ 11. Se určuje, zda je sada potenciální výjimky, které můžete vyhnuli funkce prázdný. *Specifikace výjimek dynamické*, nebo `throw(optional_type_list)` specifikace, se již nepoužívá v C ++ 11 a je podporován pouze částečně Visual Studio. Tato specifikace výjimek byla navržená tak, aby poskytují souhrnné informace o jaké výjimky může být vyvolána mimo funkci, ale v praxi byl nalezen způsobovat problémy. Jeden specifikace dynamické výjimka, která ukázat jako poněkud užitečné byl nepodmíněné `throw()` specifikace. Například deklarace funkce:  
  
```cpp  
void MyFunction(int i) throw();  
```  
  
 říká kompilátoru funkce nevyvolá výjimku jakékoli výjimky. Jedná se o ekvivalent pomocí [__declspec(nothrow)](../cpp/nothrow-cpp.md). Jeho použití je považován za volitelné.  
  
V ISO C ++ 11 Standard [noexcept](../cpp/noexcept-cpp.md) operátor zavedl jako náhrada. Je podporována v sadě Visual Studio 2015 a novější. Pokud je to možné, používat `noexcept` výraz k určení, zda funkce může vyvolat výjimky. Použijte například tuto deklaraci funkce místo výše jeden:  
  
```cpp  
void MyFunction(int i) noexcept;  
```  
  
Zatímco Visual C++ plně podporuje `noexcept` výrazu, který se odchyluje od na ISO C++ Standard v jeho implementaci specifikace dynamické výjimek.  Následující tabulka shrnuje Visual C++ implementace specifikace výjimek:  
  
|Specifikace výjimek|Význam|  
|-----------------------------|-------------|  
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|Funkce nevyvolá výjimku. Ale pokud je vyvolána výjimka mimo funkci označena `throw()`, volání kompilátoru Visual C++ `std::terminate`, nikoli `std::unexpected`. V tématu [std::unexpected](../c-runtime-library/reference/unexpected-crt.md) Další informace. Pokud je označena jako funkce `noexcept`, `noexcept(true)`, nebo `throw()`, Visual C++ compiler předpokládá, že funkce nevyvolá výjimku výjimky jazyka C++ a generuje kód odpovídajícím způsobem. Protože kód optimalizace může provést C++ compiler založen na předpokladu, že funkce nevyvolá výjimku všechny výjimky jazyka C++ Pokud funkci způsobí výjimku, nemusí se správně spustit program.|  
|`noexcept(false)`<br/>`throw(...)`<br/>Žádné specifikace|Funkce může vyvolat výjimku libovolného typu.|  
|`throw(type)`|Funkce může vyvolat výjimku typu `type`. V jazyce Visual C++, je tato syntaxe přijato, ale je interpretován jako `noexcept(false)`.|  
  
 Pokud výjimek slouží v aplikaci, musí být funkce v zásobníku volání, která zpracovává vyvolání výjimky před opustí rozsah vnější funkce označena `noexcept`, `noexcept(true)`, nebo `throw()`. Pokud žádné funkce volána mezi ten, který vyvolá výjimku a ten, který zpracovává výjimky jsou zadané jako `noexcept`, `noexcept(true)`, nebo `throw()`, program je ukončen po funkci noexcept šíří se výjimka.  
  
 Výjimka chování funkce závisí na následujících faktorech:  
  
-   Zda jsou kompilování funkce pod C nebo C++.  
  
-   Které [/EH](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru používáte.  
  
-   Určuje, zda explicitně zadat specifikace výjimek.  
  
 Specifikace výjimek explicitní nejsou povoleny u funkce jazyka C. Funkce C není považováno za generování výjimek v části **/EHsc**a může vyvolat strukturovaných výjimky v části **/EHs**, **/EHa**, nebo **/EHac**.  
  
 V následující tabulce je shrnuté, jestli funkce C++ může potenciálně throw pod různé výjimky kompilátoru zpracování možnosti:  
  
|Funkce|/ EHsc|/ EHs|/ EHa|/ EHac|  
|--------------|------------|-----------|-----------|------------|  
|Funkce C++ s žádné specifikace výjimek|Ano|Ano|Ano|Ano|  
|Funkce C++ s `noexcept`, `noexcept(true)`, nebo `throw()` specifikace výjimek|Ne|Ne|Ano|Ano|  
|Funkce C++ s `noexcept(false)`, `throw(...)`, nebo `throw(type)` specifikace výjimek|Ano|Ano|Ano|Ano|  
  
## <a name="example"></a>Příklad  
  
```cpp  
// exception_specification.cpp  
// compile with: /EHs  
#include <stdio.h>  
  
void handler() {  
   printf_s("in handler\n");  
}  
  
void f1(void) throw(int) {  
   printf_s("About to throw 1\n");  
   if (1)  
      throw 1;  
}  
  
void f5(void) throw() {  
   try {  
      f1();  
   }  
   catch(...) {  
      handler();  
    }  
}  
  
// invalid, doesn't handle the int exception thrown from f1()  
// void f3(void) throw() {  
//   f1();  
// }  
  
void __declspec(nothrow) f2(void) {  
   try {  
      f1();  
   }  
   catch(int) {  
      handler();  
    }  
}  
  
// only valid if compiled without /EHc   
// /EHc means assume extern "C" functions don't throw exceptions  
extern "C" void f4(void);  
void f4(void) {  
   f1();  
}  
  
int main() {  
   f2();  
  
   try {  
      f4();  
   }  
   catch(...) {  
      printf_s("Caught exception from f4\n");  
   }  
   f5();  
}  
```  
  
```Output  
About to throw 1  
in handler  
About to throw 1  
Caught exception from f4  
About to throw 1  
in handler  
```  
  
## <a name="see-also"></a>Viz také  
 [Zkuste, throw a catch – příkazy (C++)](../cpp/try-throw-and-catch-statements-cpp.md)   
 [Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)