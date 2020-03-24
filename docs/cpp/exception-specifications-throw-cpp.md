---
title: Specifikace výjimek (throw, s výjimkou)C++()
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 6f8f9466b867603738919c6210055d02d3c579ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180040"
---
# <a name="exception-specifications-throw-noexcept-c"></a>Specifikace výjimek (throw, s výjimkou)C++()

Specifikace výjimek jsou funkce C++ jazyka, která indikuje záměr programátora o typech výjimek, které lze rozšířit funkcí. Můžete určit, že funkce může nebo nemusí ukončit výjimku pomocí *specifikace výjimky*. Kompilátor může tyto informace použít k optimalizaci volání funkce a k ukončení programu v případě, že funkce řídí neočekávanou výjimku.

Před C++ 17 byly dva druhy specifikace výjimek. *Specifikace s výjimkou* byla nová v c++ 11. Určuje, zda sada potenciálních výjimek, které mohou být uvozeny funkcí, je prázdná. *Specifikace dynamické výjimky*nebo specifikace `throw(optional_type_list)` byla v c++ 11 zastaralá a byla odebrána v c++ 17, s výjimkou `throw()`, což je alias pro `noexcept(true)`. Tato specifikace výjimky byla navržena tak, aby poskytovala souhrnné informace o tom, jaké výjimky mohou být vyvolány z funkce, ale v praxi bylo zjištěno problematické. Jedna specifikace dynamické výjimky, která se ukázalo jako poněkud užitečná, byla specifikace nepodmíněného `throw()`. Například deklarace funkce:

```cpp
void MyFunction(int i) throw();
```

instruuje kompilátor, že funkce nevyvolá žádné výjimky. V **/std: v režimu c++ 14** to však může vést k nedefinovanému chování, pokud funkce vyvolá výjimku. Proto doporučujeme použít operátor [s výjimkou](../cpp/noexcept-cpp.md) místo výše uvedeného:

```cpp
void MyFunction(int i) noexcept;
```

Následující tabulka shrnuje implementaci specifikací výjimek od C++ Microsoftu:

|Specifikace výjimek|Význam|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|Funkce nevyvolá výjimku. V [/std: režim c++ 14](../build/reference/std-specify-language-standard-version.md) (což je výchozí nastavení), `noexcept` a `noexcept(true)` jsou ekvivalentní. Je-li vyvolána výjimka ze funkce, která je deklarována `noexcept` nebo `noexcept(true)`, je vyvolána [std:: Terminate](../standard-library/exception-functions.md#terminate) . Je-li vyvolána výjimka z funkce deklarované jako `throw()` v režimu **/std: c++ 14** , výsledek je nedefinované chování. Není vyvolána žádná konkrétní funkce. Jedná se o rozdíl od standardu C++ 14, který vyžaduje, aby kompilátor vyvolal [std:: unnečekaná](../standard-library/exception-functions.md#unexpected).  <br/> **Visual Studio 2017 verze 15,5 a novější**: v **/std: režim c++ 17** , `noexcept`, `noexcept(true)`a `throw()` jsou všechny ekvivalentní. V **/std: režim c++ 17** , `throw()` je alias pro `noexcept(true)`. V **/std: režim c++ 17** , pokud je výjimka vyvolána z funkce deklarované s některou z těchto specifikací, [std:: Terminate](../standard-library/exception-functions.md#terminate) je vyvolána podle požadavků standardu c++ 17.|
|`noexcept(false)`<br/>`throw(...)`<br/>Bez specifikace|Funkce může vyvolat výjimku libovolného typu.|
|`throw(type)`| (**C++ 14 a starší**) Funkce může vyvolat výjimku typu `type`. Kompilátor akceptuje syntaxi, ale interpretuje ji jako `noexcept(false)`. V **/std: v režimu c++ 17** problémy s kompilátorem upozorňují na C5040.|

Pokud je v aplikaci použito zpracování výjimek, musí být funkce v zásobníku volání, která zpracovává výjimky vyvolané před opuštěním vnějšího oboru funkce označené `noexcept`, `noexcept(true)`nebo `throw()`. Pokud jsou volány jakékoli funkce mezi tou, která vyvolá výjimku a ta, která zpracovává výjimku, je zadána jako `noexcept`, `noexcept(true)` (nebo `throw()` v režimu **/std: c++ 17** ), program je ukončen, když funkce s výjimkou šíří výjimku.

Chování výjimky funkce závisí na následujících faktorech:

- Který [jazyk standardní režim kompilace](../build/reference/std-specify-language-standard-version.md) je nastaven.
- Bez ohledu na to, zda kompilujete funkci C++pod C nebo.

- Který parametr kompilátoru [/eh](../build/reference/eh-exception-handling-model.md) používáte.

- Bez ohledu na to, zda explicitně zadáte specifikaci výjimky.

Explicitní specifikace výjimek nejsou u funkcí jazyka C povoleny. Předpokládá se, že funkce jazyka C nevyvolává výjimky v **/EHsc**a může vyvolat strukturované výjimky pod **/EHS**, **/EHa**nebo **/EHAC**.

Následující tabulka shrnuje, jestli C++ funkce může potenciálně vyvolat v různých možnostech zpracování výjimek kompilátoru:

|Funkce|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|C++funkce bez specifikace výjimek|Ano|Ano|Ano|Ano|
|C++funkce s `noexcept`, `noexcept(true)`nebo `throw()` specifikace výjimek|Ne|Ne|Ano|Ano|
|C++funkce s `noexcept(false)`, `throw(...)`nebo `throw(type)` specifikace výjimek|Ano|Ano|Ano|Ano|

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

[try, throw a catch – příkazy (C++)](../cpp/try-throw-and-catch-statements-cpp.md)<br/>
[Moderní C++ osvědčené postupy pro výjimky a zpracování chyb](errors-and-exception-handling-modern-cpp.md)
