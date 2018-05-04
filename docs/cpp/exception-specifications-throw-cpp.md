---
title: Specifikace výjimek (throw, noexcept) (C++) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ab09d5aadb489208b2e7591c2bf0f60ab836da4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="exception-specifications-throw-noexcept-c"></a>Specifikace výjimek (throw, noexcept) (C++)

Specifikace výjimek jsou funkce jazyka C++, která označuje záměr programátora o typy výjimek, které mohou být přeneseny funkcí. Můžete určit, že funkce může nebo nemusí ukončete výjimkou pomocí *specifikace výjimek*. Kompilátor tyto informace můžete použít k optimalizaci volání funkce a ukončete program, pokud neočekávanou výjimku řídicí sekvence funkce. 

Před C ++ 17 nebyly k dispozici dva druhy specifikace výjimek. *Noexcept specifikace* nové v C ++ 11. Se určuje, zda je sada potenciální výjimky, které můžete vyhnuli funkce prázdný. *Specifikace výjimek dynamické*, nebo `throw(optional_type_list)` specifikace, se nepoužívá v C ++ 11 a odebrat součástí C ++ 17, s výjimkou `throw()`, což je alias `noexcept(true)`. Tato specifikace výjimek byla navržená tak, aby poskytují souhrnné informace o jaké výjimky může být vyvolána mimo funkci, ale v praxi byl nalezen způsobovat problémy. Jeden specifikace dynamické výjimka, která ukázat jako poněkud užitečné byl nepodmíněné `throw()` specifikace. Například deklarace funkce:

```cpp
void MyFunction(int i) throw();
```
říká kompilátoru funkce nevyvolá výjimku jakékoli výjimky. Ale v **/std: c ++ 14** režimu to může vést k undefined chování, pokud funkci výjimku. Proto doporučujeme používat [noexcept](../cpp/noexcept-cpp.md) operátor místo jeden výše:

```cpp
void MyFunction(int i) noexcept;
```
Následující tabulka shrnuje Microsoft Visual C++ implementace specifikace výjimek:

|Specifikace výjimek|Význam|
|-----------------------------|-------------|
|`noexcept`<br>`noexcept(true)`<br>`throw()`|Funkce nevyvolá výjimku. V [/std: c ++ 14](../build/reference/std-specify-language-standard-version.md) režimu (což je výchozí nastavení), `noexcept` a `noexcept(true)` odpovídají. Pokud je vyvolána výjimka z funkci, která je deklarovaná `noexcept` nebo `noexcept(true)`, [std::terminate](../standard-library/exception-functions.md#terminate) je volána. Pokud je vyvolána výjimka z funkce deklarován jako `throw()` v **/std: c ++ 14** režim, výsledek je nedefinovaný chování. Žádná konkrétní funkce je volána. Toto je odchylkami z C ++ 14 standardní, který vyžaduje kompilátor k vyvolání [std::unexpected](../standard-library/exception-functions.md#unexpected).  <br> **Visual Studio 2017 verze 15,5 a novější**: V **/std: c ++ 17** režimu `noexcept`, `noexcept(true)`, a `throw()` všechny odpovídají. V **/std: c ++ 17** režimu `throw()` je alias `noexcept(true)`. V **/std: c ++ 17** režim, pokud je vyvolána výjimka z funkce deklarované s žádným z těchto specifikací [std::terminate](../standard-library/exception-functions.md#terminate) je volána podle požadavku standardu C ++ 17.|
|`noexcept(false)`<br/>`throw(...)`<br/>Žádné specifikace|Funkce může vyvolat výjimku libovolného typu.|
|`throw(type)`| (**C ++ 14 a starší**) funkce může vyvolat výjimku typu `type`. Kompilátor přijímá syntaxe, ale interpretovat jako `noexcept(false)`. V **/std: c ++ 17** režimu kompilátor vydá upozornění C5040.|

Pokud výjimek slouží v aplikaci, musí být funkce v zásobníku volání, která zpracovává vyvolání výjimky před opustí rozsah vnější funkce označena `noexcept`, `noexcept(true)`, nebo `throw()`. Pokud žádné funkce volána mezi ten, který vyvolá výjimku a ten, který zpracovává výjimky jsou zadané jako `noexcept`, `noexcept(true)` (nebo `throw()` v **/std: c ++ 17** režimu), je ukončen program, když Funkce noexcept rozšíří výjimku.

Výjimka chování funkce závisí na následujících faktorech:

- Které [režim standardní kompilace jazyka](../build/reference/std-specify-language-standard-version.md) nastavena.
- Zda jsou kompilování funkce pod C nebo C++.

- Které [/EH](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru používáte.

- Určuje, zda explicitně zadat specifikace výjimek.

Specifikace výjimek explicitní nejsou povoleny u funkce jazyka C. Funkce C není považováno za generování výjimek v části **/EHsc**a může vyvolat strukturovaných výjimky v části **/EHs**, **/EHa**, nebo **/EHac**.

V následující tabulce je shrnuté, jestli funkce C++ může potenciálně throw pod různé výjimky kompilátoru zpracování možnosti:

|Funkce|/ EHsc|/ EHs|/EHa|/ EHac|
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

 [Zkuste, throw a catch – příkazy (C++)](../cpp/try-throw-and-catch-statements-cpp.md) [C++ zpracování výjimek](../cpp/cpp-exception-handling.md)