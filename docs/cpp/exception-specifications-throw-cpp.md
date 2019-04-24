---
title: Specifikace výjimek (throw, noexcept) (C++)
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 9280f3d96088d988a9d5cfe0f3d56444b865167e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154331"
---
# <a name="exception-specifications-throw-noexcept-c"></a>Specifikace výjimek (throw, noexcept) (C++)

Specifikace výjimek jsou funkce jazyka C++, které označují programátora záměr o typy výjimek, které můžete rozšířit pomocí funkce. Můžete určit, že funkce může nebo nemusí výjimku ukončit pomocí *specifikace výjimky*. Kompilátor tyto informace můžete použít k optimalizaci volání funkce a ukončení programu, pokud neočekávanou výjimku řídící funkce.

Před C ++ 17 se dva typy specifikace výjimky. *Noexcept specifikace* byla nová v C ++ 11. Určuje, zda sada potenciální výjimky, které může uniknout funkce je prázdný. *Specifikace dynamických výjimek*, nebo `throw(optional_type_list)` specifikace, bylo zastaralé v C ++ 11 a odstraněno v C ++ 17, s výjimkou `throw()`, což je alias pro `noexcept(true)`. Tato specifikace výjimky je navržená k poskytuje souhrnné informace o jaké výjimky mohou být vyvolány ve funkci, ale v praxi byl nalezen jako problematické. Jeden specifikace dynamických výjimek, který být částečně užitečné byla Nepodmíněný `throw()` specifikace. Například deklarace funkce:

```cpp
void MyFunction(int i) throw();
```
přikáže kompilátoru, že funkce nevyvolá žádné výjimky. Nicméně v **/std: c ++ 14** režimu to může vést k nedefinované chování, pokud funkce vyvolá výjimku. Proto doporučujeme použít [noexcept](../cpp/noexcept-cpp.md) operátor ne výše:

```cpp
void MyFunction(int i) noexcept;
```
Následující tabulka shrnuje implementaci specifikace výjimek Microsoft Visual C++:

|Specifikace výjimek|Význam|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|Funkce nevyvolá výjimku. V [/std: c ++ 14](../build/reference/std-specify-language-standard-version.md) režimu (výchozí), `noexcept` a `noexcept(true)` jsou ekvivalentní. Když výjimka je vyvolána z funkce, která je deklarována `noexcept` nebo `noexcept(true)`, [std::terminate](../standard-library/exception-functions.md#terminate) je vyvolána. Když je výjimka vyvolána z funkce deklarované jako `throw()` v **/std: c ++ 14** režimu, výsledek je nedefinované chování. Žádná konkrétní funkce je vyvolána. Toto je odchylkami od C ++ 14 na úrovni standard, který vyžaduje kompilátor, který má být vyvolán [std::unexpected](../standard-library/exception-functions.md#unexpected).  <br/> **Visual Studio 2017 verze 15.5 nebo novější**: V **/std: c ++ 17** režimu `noexcept`, `noexcept(true)`, a `throw()` jsou všechny ekvivalentní. V **/std: c ++ 17** režimu `throw()` je alias pro `noexcept(true)`. V **/std: c ++ 17** režimu, když výjimka je vyvolána z funkce deklarovaná pomocí některé z těchto specifikací [std::terminate](../standard-library/exception-functions.md#terminate) se vyvolá podle požadavku standardu C ++ 17.|
|`noexcept(false)`<br/>`throw(...)`<br/>Žádné podmínky|Funkce může vyvolat výjimky jakéhokoli typu.|
|`throw(type)`| (**C ++ 14 a dřívějších**) funkce může vyvolat výjimku typu `type`. Kompilátor přijímá syntaxi, ale interpretovat jako `noexcept(false)`. V **/std: c ++ 17** režimu kompilátor vydá upozornění C5040.|

Pokud zpracování výjimek se používá v aplikaci, musí být funkce v zásobníku volání, která zpracovává vyvolané výjimky před opustí vnějším oboru funkce označena `noexcept`, `noexcept(true)`, nebo `throw()`. Pokud žádné funkce volána mezi ten, který vyvolá výjimku a ten, který zpracovává výjimku jsou zadané jako `noexcept`, `noexcept(true)` (nebo `throw()` v **/std: c ++ 17** režimu), program se ukončí, když Funkce noexcept šíří výjimku.

Chování výjimky funkce závisí na následujících faktorech:

- Které [režim standardní kompilace jazyka](../build/reference/std-specify-language-standard-version.md) nastavena.
- Jste kompilovali funkci pod C nebo C++.

- Které [/EH](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru použijete.

- Určuje, zda explicitně zadáte specifikaci výjimky.

Explicitní specifikace výjimek nejsou povoleny ve funkcích c. Funkci jazyka C předpokládá, že není k vyvolání výjimky v rámci **/EHsc**a může vyvolat strukturované výjimky v rámci **/EHS**, **/EHa**, nebo **/EHac**.

Následující tabulka uvádí, zda funkci jazyka C++ může potenciálně vyvolat v rámci různých zpracování možností kompilátoru výjimek:

|Funkce|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|C++ funguje bez specifikací výjimek|Ano|Ano|Ano|Ano|
|Funkce jazyka C++ s `noexcept`, `noexcept(true)`, nebo `throw()` specifikace výjimek|Ne|Ne|Ano|Ano|
|Funkce jazyka C++ s `noexcept(false)`, `throw(...)`, nebo `throw(type)` specifikace výjimek|Ano|Ano|Ano|Ano|

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

## <a name="see-also"></a>Viz také:

[try, throw a catch – příkazy (C++)](../cpp/try-throw-and-catch-statements-cpp.md)<br/>
[Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)