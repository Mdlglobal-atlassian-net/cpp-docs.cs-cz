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
ms.openlocfilehash: 45244ace414fc073956684088ac43eb9b92f1e5b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588237"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Základní koncepce při práci se spravovanými výjimkami

Toto téma popisuje zpracování výjimek v spravovaných aplikací. To znamená, že aplikace, který je kompilován **/CLR** – možnost kompilátoru.

## <a name="in-this-topic"></a>V tomto tématu

- [Vyvolání výjimky v rámci/CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Bloky Try/Catch pro rozšíření modulu CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Poznámky

Pokud kompilujete s **/CLR** možnost, můžete zpracovávat výjimky CLR, stejně jako standardní [zpracování výjimek jazyka C++](../cpp/cpp-exception-handling.md) a [strukturované zpracování výjimek](../cpp/structured-exception-handling-c-cpp.md) (SEH). Výjimky modulu CLR je všechny výjimky vyvolané spravovaným typem. [System::Exception](https://msdn.microsoft.com/library/system.exception.aspx) třídy nabízí spoustu užitečných metod pro zpracování výjimek CLR a doporučuje se jako základní třída pro třídy definované uživatelem výjimek.

Zachycování výjimek typy odvozené od rozhraní není podporován v rámci **/CLR**. Kromě toho modul common language runtime nepovoluje jak zachytávat výjimky přetečení zásobníku; k výjimce přetečení zásobníku se ukončit proces.

Další informace o rozdíly ve zpracování výjimek ve spravovaných a nespravovaných aplikacích najdete v tématu [rozdíly ve výjimce zpracování chování v rámci spravovaných rozšíření jazyka C++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a> Vyvolání výjimky v rámci/CLR

Výraz throw C++ je rozšířená vyvolání popisovač na typ CLR. Následující příklad vytvoří typ vlastní výjimky a potom vyvolá instance tohoto typu:

```
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

Hodnotový typ musí být zabaleny před vyvolání:

```
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

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a> Bloky Try/Catch pro rozšíření modulu CLR

Stejné **zkuste**/**catch** blokové struktuře lze použít pro zachytávání CLR a nativní výjimky:

```
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

### <a name="order-of-unwinding-for-c-objects"></a>Pořadí uvolnění pro objekty C++

Uvolnění dochází u všech objektů jazyka C++ s destruktory, které mohou být v zásobníku za běhu mezi aktivační funkce a funkce zpracování. Protože typy CLR jsou přiděleny do haldy, uvolnění se nevztahuje na ně.

Pořadí událostí pro vyvolanou výjimku vypadá takto:

1. Modul runtime provede zásobníku pro klauzuli catch. odpovídající nebo v případě SEH, výjimkou filtr pro SEH pro zachycení výjimky. Klauzule catch se nejprve prohledán lexikální popořadě a potom dynamicky dolů v zásobníku volání.

1. Po nalezení obslužnou rutinu správné, když je zásobník odvinut do tohoto bodu. Pro každé volání funkce v zásobníku, jeho místní objekty jsou zničeny a __finally bloky provádějí, od těch s nejvíce vnořené pasivního.

1. Jakmile je zásobník odvinut, je proveden v klauzuli catch.

### <a name="catching-unmanaged-types"></a>Zachycení nespravovaného typy

Při vyvolání typem nespravovaného objektu je zabalený s výjimkou typu [System::Runtime.InteropServices::SEHException](https://msdn.microsoft.com/library/system.runtime.interopservices.sehexception.aspx). Při hledání odpovídající **catch** klauzule, existují dvě možnosti.

- Pokud je nativní typ jazyka C++, výjimky je neobalený a ve srovnání s byl zjištěn typ. Toto porovnání umožňuje nativní typu jazyka C++, chcete-li zachytit běžným způsobem.

- Nicméně pokud **catch** klauzule typu **SEHException –** nebo některý z jeho základních tříd je zkontrolován nejprve, bude v klauzuli zachycení výjimky. Proto je vhodné umístit všechny klauzule catch, které nejprve catch nativních typů C++ před všechny skutečné klauzule typy CLR.

Všimněte si, že

```
catch(Object^)
```

and

```
catch(...)
```

zachytí i všechny vyvolané výjimce typu včetně výjimky SEH.

Pokud nespravovaným typem se zachycuje prostřednictvím catch(Object^), nezničí Vyvolaný objekt.

Při vyvolávání a zachycování nespravované výjimky, doporučujeme použít [/EHsc](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru místo **/EHS** nebo **/EHa**.

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../windows/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../windows/safe-cast-cpp-component-extensions.md)<br/>
[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)