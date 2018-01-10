---
title: "Základní koncepce při práci se spravovanými výjimkami | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5e2faf56f050610e6c98ff82cdca10333a54fd93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Základní koncepce při práci se spravovanými výjimkami
Toto téma popisuje zpracování výjimek v spravovaných aplikací. To znamená, aplikace, která je kompilovat s **/CLR** – možnost kompilátoru.  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [Vyvolání výjimek v režimu kompilace/CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor1)  
  
-   [Try/Catch – bloky pro rozšíření CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)  
  
## <a name="remarks"></a>Poznámky  
 Pokud je kompilovat s **/CLR** možnost, může zpracovat výjimky CLR a také standardní [zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md) a [strukturovanému zpracování výjimek](../cpp/structured-exception-handling-c-cpp.md) (SEH). Výjimky CLR je jakékoli výjimky vyvolané spravovaného typu. [System::Exception](https://msdn.microsoft.com/en-us/library/system.exception.aspx) třída poskytuje mnoho užitečných metod pro zpracování výjimky CLR a doporučuje se jako základní třída pro třídy uživatelem definované výjimky.  
  
 Zachytávání výjimek typy odvozené z rozhraní není podporován v rámci **/CLR**. Kromě toho modul common language runtime nepovoluje můžete zachytit výjimky přetečení zásobníku; proces ukončí výjimce přetečení zásobníku.  
  
 Další informace o rozdíly ve zpracování výjimek ve spravovaných a nespravovaných aplikacích najdete v tématu [rozdíly v výjimka zpracování chování pod spravovaných rozšíření pro C++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Vyvolání výjimek v režimu kompilace/CLR  
 Výraz throw C++ je rozšířeno na throw popisovač typu CLR. Následující příklad vytvoří typ vlastní výjimky a pak vyvolá instance tohoto typu:  
  
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
  
 Typ hodnoty musí být zabaleny před hlášeny:  
  
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
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Try/Catch – bloky pro rozšíření CLR  
 Stejné **zkuste**/**catch** bloku struktura může být použita pro zachytávání CLR a nativní výjimky:  
  
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
  
### <a name="order-of-unwinding-for-c-objects"></a>Pořadí Unwinding pro objekty C++  
 Unwinding dochází k pro všechny objekty C++ s destruktory, které mohou být v zásobníku běhu mezi aktivační funkce a funkce zpracování. Protože typy CLR mají při přidělování v haldě, unwinding se nevztahuje na ně.  
  
 Pořadí událostí pro vyvolaná výjimka je následující:  
  
1.  Modul runtime prochází zásobník vyhledávání pro klauzuli odpovídající catch nebo v případě SEH, výjimkou filtr SEH k zachycení výjimky. Catch – klauzule vyhledávají nejprve v lexikální pořadí a potom dynamicky dolů zásobníku volání.  
  
2.  Jakmile obslužnou rutinu správné nenajde, je oddělen do bodu zásobníku. Pro každé volání funkce v zásobníku se destructed jeho místní objekty a __finally jsou spouštěny bloky, ze většinu i vnořený.  
  
3.  Po oddělen zásobníku se spustí v klauzuli catch.  
  
### <a name="catching-unmanaged-types"></a>Zachytávání nespravované typy  
 Při vyvolání typ nespravované objektu, který je uzavřen do k výjimce typu [System::Runtime.InteropServices::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx). Při hledání odpovídající **catch** klauzule, máte dvě možnosti.  
  
-   Jestliže je nativní typ C++, je výjimka úkony, spočívající a porovná typ došlo. Toto porovnání umožňuje nativního typu C++ na se zjistilo běžným způsobem.  
  
-   Ale pokud **catch** klauzule typu **SEHException –** nebo některý z jeho základních tříd je zkontrolován nejprve, bude v klauzuli zachytávat výjimky. Proto byste měli umístit všechny catch věty, které nejprve catch nativní typy C++ před všechny catch klauzule typy CLR.  
  
 Všimněte si, že  
  
```  
catch(Object^)  
```  
  
 and  
  
```  
catch(...)  
```  
  
 obě catch jakýmikoli vyvolané včetně SEH výjimky.  
  
 Pokud nespravovaný typ je zachytila catch(Object^), se nezničí objekt výjimce dojde.  
  
 Při vyvolání nebo zachytávání nespravované výjimky, doporučujeme použít [/EHsc](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru místo **/EHs** nebo **/EHa**.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../windows/exception-handling-cpp-component-extensions.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)