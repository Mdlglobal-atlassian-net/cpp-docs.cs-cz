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
ms.openlocfilehash: cf241d4e599ad58c2e39680d8ed4e4e250b42b18
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988547"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Základní koncepce při práci se spravovanými výjimkami

Toto téma popisuje zpracování výjimek ve spravovaných aplikacích. To znamená, že aplikace kompilována s možností kompilátoru **/CLR** .

## <a name="in-this-topic"></a>V tomto tématu

- [Vyvolání výjimek v/CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Bloky try/catch pro rozšíření CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Poznámky

Pokud kompilujete s možností **/CLR** , můžete zpracovat výjimky CLR a standardní <xref:System.Exception> Třída poskytuje mnoho užitečných metod pro zpracování výjimek CLR a doporučuje se jako základní třída pro uživatelem definované třídy výjimek.

Zachycení typů výjimek odvozených z rozhraní není podporováno v rámci **/CLR**. Také modul CLR (Common Language Runtime) neumožňuje zachytit výjimky přetečení zásobníku; Při výjimce přetečení zásobníku dojde k ukončení procesu.

Další informace o rozdílech ve zpracování výjimek ve spravovaných a nespravovaných aplikacích naleznete v tématu [rozdíly v chování zpracování výjimek C++v části spravovaná rozšíření pro ](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Vyvolání výjimek v/CLR

Výraz C++ throw je rozšířen, aby vyvolal popisovač typu CLR. Následující příklad vytvoří vlastní typ výjimky a poté vyvolá instanci tohoto typu:

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

Hodnotový typ musí být zabalený před vyvolanou hodnotou:

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

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Bloky try/catch pro rozšíření CLR

**Stejný/** struktury bloku **catch** lze použít pro zachycení CLR a nativní výjimky:

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

### <a name="order-of-unwinding-for-c-objects"></a>Pořadí unwind pro C++ objekty

K vrácení zpět dojde u všech C++ objektů s destruktory, které mohou být v zásobníku run-time mezi aktivační funkcí a funkcí zpracování. Vzhledem k tomu, že typy CLR jsou přiděleny na haldu, neplatí pro ně zpětná vinutí.

Pořadí událostí pro vyvolanou výjimku je následující:

1. Modul runtime projde zásobníkem, který hledá příslušnou klauzuli catch, nebo v případě SEH filtr s výjimkou SEH pro zachycení výjimky. Klauzule catch jsou nejprve prohledávány v lexikálním pořadí a poté dynamicky v zásobníku volání.

1. Po nalezení správné obslužné rutiny se zásobník odblokuje do tohoto bodu. Pro každé volání funkce v zásobníku jsou jeho místní objekty destrukturované a jsou spouštěny __finally bloky od nejvíce po celém čísle směrem ven.

1. Po odvinutí zásobníku je provedena klauzule catch.

### <a name="catching-unmanaged-types"></a>Zachycení nespravovaných typů

Když je vyvolána nespravovaný objekt typu, je zabalen s výjimkou typu <xref:System.Runtime.InteropServices.SEHException>. Při hledání příslušné klauzule **catch** existují dvě možnosti.

- Pokud dojde k C++ nativnímu typu, výjimka je nezabalená a porovnána s typem, ke kterému došlo. Toto porovnání umožňuje zachycení nativního C++ typu běžným způsobem.

- Pokud je však klauzule **catch** typu **SEHException –** nebo kterákoli z jeho základních tříd zkontrolována jako první, klauzule zachytí výjimku. Proto byste měli umístit všechny klauzule catch, které před všechny C++ klauzule catch typů CLR nejprve zachytí nativní typy.

Je třeba mít na paměti, že:

```
catch(Object^)
```

and

```
catch(...)
```

bude zachytit jakýkoli vyvolaný typ, včetně výjimek SEH.

Pokud je nespravovaný typ zachycen pomocí catch (Object ^), neodstraní vyvolaný objekt.

Při vyvolávání nebo zachycování nespravovaných výjimek doporučujeme použít možnost kompilátoru [/EHsc](../build/reference/eh-exception-handling-model.md) namísto **/EHS** nebo **/EHa**.

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)
