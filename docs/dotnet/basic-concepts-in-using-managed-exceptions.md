---
title: Základní koncepce při práci se spravovanými výjimkami
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
ms.openlocfilehash: 6bc1e9c6d40599ae9a821179dcf56dbb7e21bf10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372530"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Základní koncepce při práci se spravovanými výjimkami

Toto téma popisuje zpracování výjimek ve spravovaných aplikacích. To znamená, že aplikace, která je kompilována s parametrem kompilátoru **/clr.**

## <a name="in-this-topic"></a>V tomto tématu

- [Vyvolání výjimek pod /clr](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Try/Catch Bloky pro CLR rozšíření](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Poznámky

Pokud kompilujete pomocí parametru **/clr,** můžete zpracovat výjimky CLR a také standardní <xref:System.Exception> třída poskytuje mnoho užitečných metod pro zpracování výjimek CLR a je doporučena jako základní třída pro uživatelem definované třídy výjimek.

Zachycení typů výjimek odvozených z rozhraní není podporováno v **/clr**. Také běžný jazyk runtime neumožňuje zachytit výjimky přetečení zásobníku; výjimka přetečení zásobníku ukončí proces.

Další informace o rozdílech ve zpracování výjimek ve spravovaných a nespravovaných aplikacích naleznete [v tématu Rozdíly v chování zpracování výjimek v části Spravovaná rozšíření pro c++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Vyvolání výjimek pod /clr

Výraz vyvolání jazyka C++ je rozšířen tak, aby vyvolá popisovač na typ CLR. Následující příklad vytvoří vlastní typ výjimky a pak vyvolá instanci tohoto typu:

```cpp
// clr_exception_handling.cpp
// compile with: /clr /c
ref struct MyStruct: public System::Exception {
public:
   int i;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   throw pMyStruct;
}
```

Typ hodnoty musí být před vyvoláním zabalen:

```cpp
// clr_exception_handling_2.cpp
// compile with: /clr /c
value struct MyValueStruct {
   int i;
};

void GlobalFunction() {
   MyValueStruct v = {11};
   throw (MyValueStruct ^)v;
}
```

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Try/Catch Bloky pro CLR rozšíření

Stejnou strukturu **bloku catch try**/**catch** lze použít pro zachycení clr i nativnívýjimky:

```cpp
// clr_exception_handling_3.cpp
// compile with: /clr
using namespace System;
ref struct MyStruct : public Exception {
public:
   int i;
};

struct CMyClass {
public:
   double d;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   pMyStruct->i = 11;
   throw pMyStruct;
}

void GlobalFunction2() {
   CMyClass c = {2.0};
   throw c;
}

int main() {
   for ( int i = 1; i >= 0; --i ) {
      try {
         if ( i == 1 )
            GlobalFunction2();
         if ( i == 0 )
            GlobalFunction();
      }
      catch ( CMyClass& catchC ) {
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );
         Console::WriteLine( catchC.d );
      }
      catch ( MyStruct^ catchException ) {
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );
         Console::WriteLine( catchException->i );
      }
   }
}
```

### <a name="output"></a>Výstup

```
In 'catch(CMyClass& catchC)'
2
In 'catch(MyStruct^ catchException)'
11
```

### <a name="order-of-unwinding-for-c-objects"></a>Pořadí odvíjení pro objekty C++

Unwinding dochází pro všechny objekty Jazyka C++ s destruktory, které mohou být v zásobníku run-time mezi funkce vyvolání a zpracování funkce. Vzhledem k tomu, že clr typy jsou přiděleny na haldě, unwinding se nevztahuje na ně.

Pořadí událostí pro vyvolání výjimky je následující:

1. Runtime procházky zásobníku hledá příslušné catch klauzule nebo v případě SEH, s výjimkou filtru pro SEH, zachytit výjimku. Catch klauzule jsou prohledány nejprve v lexikálním pořadí a pak dynamicky dolů zásobníku volání.

1. Jakmile je nalezena správná obslužná rutina, zásobník je odvinut do tohoto bodu. Pro každé volání funkce v zásobníku jsou jeho místní objekty zničeny a __finally bloky jsou spouštěny, z většiny vnořených směrem ven.

1. Jakmile je odvíjení zásobníku, catch klauzule je proveden.

### <a name="catching-unmanaged-types"></a>Zachycení nespravovaných typů

Při vyvolání nespravovaného typu objektu je zabalen s <xref:System.Runtime.InteropServices.SEHException>výjimkou typu . Při hledání příslušné klauzule **catch** existují dvě možnosti.

- Pokud je zjištěn nativní typ C++, výjimka je rozbalena a porovnána s typem. Toto porovnání umožňuje nativní c++ typ zachytit normálním způsobem.

- Však pokud **catch** klauzule typu **SEHException** nebo některé z jeho základní třídy je zkoumána jako první, klauzule bude zachytit výjimku. Proto byste měli umístit všechny catch klauzule, které zachycují nativní c++ typy nejprve před všechny catch klauzule clr typy.

Všimněte si, že

```
catch(Object^)
```

a

```
catch(...)
```

bude oba zachytit všechny vyvržené typu, včetně výjimky SEH.

Pokud je nespravovaný typ zachycen catch(Object^), nezničí objekt, který byl vyvolán.

Při vyvolání nebo zachycení nespravované výjimky, doporučujeme použít možnost kompilátoru [/EHsc](../build/reference/eh-exception-handling-model.md) namísto **/EHs** nebo **/EHa**.

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)
