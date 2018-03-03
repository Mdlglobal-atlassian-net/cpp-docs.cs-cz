---
title: "nové a odstraňte operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- delete_cpp
- new
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++], dynamic allocation of objects
- nothrownew.obj
- delete keyword [C++], syntax
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3af862988502ac0d1908c466aae5e62b753509c2
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="new-and-delete-operators"></a>Operátory new a delete

C++ nepodporuje dynamické přidělování a zrušení přidělení objektů pomocí [nové](../cpp/new-operator-cpp.md) a [odstranit](../cpp/delete-operator-cpp.md) operátory. Tyto operátory přidělují paměť objektům z fondu s názvem volné úložiště. `new` Operátor volání funkce speciální [new – operátor](../cpp/new-operator-cpp.md)a `delete` operátor volání funkce speciální [delete – operátor](../cpp/delete-operator-cpp.md).  
  
 `new` Funkce standardní knihovny C++ podporuje chování určené ve verzi standard C++, který má vyvolat std::bad_alloc výjimka, pokud selže přidělení paměti. Pokud stále chcete verze – vyvolání `new`, propojit váš program s nothrownew.obj. Ale když můžete propojit s nothrownew.obj, výchozí `operator new` ve standardní knihovně C++ přestane fungovat.  
  
 Seznam soubory knihovny, které tvoří běhové knihovny jazyka C a standardní knihovny C++, naleznete v části [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).  
  
##  <a id="new_operator"></a> Operátor new  
 Je-li příkaz obdobný následujícímu příkazu nalezen v programu, je přeložen jako volání funkce `operator new`:  
  
```cpp  
char *pch = new char[BUFFER_SIZE];  
```  
  
Pokud se jedná o žádost 0 bajtů úložišť, **new – operátor** vrací ukazatel na objekt distinct (tedy opakovaná volání **new – operátor** vracet různé ukazatele). Pokud je nedostatek paměti pro požadavek na přidělení **new – operátor** std::bad_alloc výjimku nebo vrátí **nullptr** při připojení v jiných vyvolávání `operator new` podporovat.  
  
Můžete napsat rutiny, které se pokouší uvolnit paměť a opakujte přidělení; v tématu [_set_new_handler –](../c-runtime-library/reference/set-new-handler.md) Další informace. Další informace o obnovení schéma najdete v části zpracování nedostatek paměti v tomto tématu.  

  
Dva obory funkcí `operator new` jsou popsány v následující tabulce.  
  
### <a name="scope-for-operator-new-functions"></a>Obor pro funkce operator new  
  
|Operátor|Rozsah|  
|--------------|-----------|  
|**:: new – operátor**|Globální|  
|*Název třídy* **:: new – operátor**|Třída|  
  
 První argument **new – operátor** musí být typu **size_t –** (typem definovaným v \<stddef.h >), a návratový typ je vždy **void \***  .  
  
 Na globální **new – operátor** funkce je volána, když **nové** operátor se používá k přidělení objekty vestavěné typy, uživatelem definované objekty typu třídy, které neobsahují **new – operátor** funkce a pole libovolného typu. Při **nové** operátor se používá k přidělení objekty typu třídy kde **new – operátor** je definována této třídy a **new – operátor** je volána.  
  
 **New – operátor** funkce definovaný pro třídu je statické členské funkce (který, proto nelze virtuální), která skryje na globální **new – operátor** funkce pro objekty daného typu třídy. Podívejte se kde **nové** se používá k přidělení a zadanou hodnotu nastavení paměti:  
  
```cpp  
// spec1_the_operator_new_function1.cpp  
#include <malloc.h>  
#include <memory.h>  
  
class Blanks  
{  
public:  
    Blanks(){}  
    void *operator new( size_t stAllocateBlock, char chInit );  
};  
void *Blanks::operator new( size_t stAllocateBlock, char chInit )  
{  
    void *pvTemp = malloc( stAllocateBlock );  
    if( pvTemp != 0 )  
        memset( pvTemp, chInit, stAllocateBlock );  
    return pvTemp;  
}  
// For discrete objects of type Blanks, the global operator new function  
// is hidden. Therefore, the following code allocates an object of type  
// Blanks and initializes it to 0xa5  
int main()  
{  
   Blanks *a5 = new(0xa5) Blanks;  
   return a5 != 0;  
}  
```  
  
 Argument zadaný v závorkách, aby **nové** předaný `Blanks::operator new` jako `chInit` argument. Ale na globální **new – operátor** funkce skryt, který by například následující chybovou zprávu:  
  
```cpp  
Blanks *SomeBlanks = new Blanks;  
```  
  
 Ve Visual C++ nonclass 5.0 a starší, typy a všechna pole (bez ohledu na to, jestli byl z **– třída** typu) přidělen s použitím **nové** operátor vždy použít na globální **new – operátor** funkce.  
  
 Od verze Visual C++ 5.0, kompilátor podporuje pole člen **nové** a **odstranit** operátory v deklaraci třídy. Příklad:  
  
```cpp  
// spec1_the_operator_new_function2.cpp  
class MyClass  
{  
public:  
   void * operator new[] (size_t)  
   {  
      return 0;  
   }  
   void   operator delete[] (void*)  
   {  
   }  
};  
  
int main()   
{  
   MyClass *pMyClass = new MyClass[5];  
   delete [] pMyClass;  
}  
```  
  
### <a name="handling-insufficient-memory"></a>Zpracování nedostatek paměti  
 Testování neúspěchu přidělení paměti lze provést například následujícím kódem:  
  
```cpp  
// insufficient_memory_conditions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
#define BIG_NUMBER 100000000  
int main() {  
   int *pI = new int[BIG_NUMBER];  
   if( pI == 0x0 ) {  
      cout << "Insufficient memory" << endl;  
      return -1;  
   }  
}  
```  
  
 Existuje jiné způsoby pro zpracování požadavků na přidělení paměti se nezdařilo: zápis vlastní obnovení rutiny pro zpracování takové selhání a pak zaregistrovat funkce voláním [_set_new_handler –](../c-runtime-library/reference/set-new-handler.md) běhové funkce.  
  
##  <a id="delete_operator"></a> Operátor delete  
 Paměti, která se přidělí dynamicky pomocí **nové** operátor může být uvolněno pomocí **odstranit** operátor. Operátor volání odstranění **delete – operátor** funkci, což uvolní paměť zpět do fondu k dispozici. Pomocí **odstranit** operátor také způsobí, že destruktoru třídy (pokud existuje) má být volána.  
  
 Existují globální a s rozsahem třídy **delete – operátor** funkce. Pouze jeden **delete – operátor** funkce lze definovat pro danou třídu; Pokud definované, skryje na globální **delete – operátor** funkce. Na globální **delete – operátor** funkce je volána vždy pro pole libovolného typu.  
  
 Na globální **delete – operátor** funkce. Existují dva způsoby pro globální konfiguraci **delete – operátor** a člena třídy **delete – operátor** funkce:  
  
```cpp  
void operator delete( void * );  
void operator delete( void *, size_t );  
```  
  
 Pro danou třídu mohou existovat jenom jedna z předchozí dva způsoby. První formulář přijímá jeden argument typu **void \*** , která obsahuje ukazatel na objekt, který chcete zrušit přidělení. Druhý formulář – velikost navrácení – má dva argumenty, první z nich je ukazatel na oblast paměti se zrušit přidělení a druhá které počet bajtů se zrušit přidělení. Návratový typ obou formulářů `void` (**delete – operátor** nemůže vrátit hodnotu).  
  
 Druhého formuláře je cílem urychlit hledání správné velikosti kategorii objekt, který má být odstraněn, který je často není uložen téměř přidělení sám a pravděpodobně neuložená ve vyrovnávací paměti; druhý formulář je obzvláště užitečné, když **delete – operátor** funkce ze základní třídy se používá k odstranění objekt odvozené třídy.  
  
 **Delete – operátor** funkce je statická; proto nemůže být virtuální. `operator delete` Funkce dodržuje řízení přístupu, jak je popsáno v [řízení přístup ke členu](../cpp/member-access-control-cpp.md).  
  
 Následující příklad ukazuje, uživatelem definované **new – operátor** a **delete – operátor** funkce, navržená tak, aby přidělení a navrácení paměti protokolu:  
  
```cpp  
// spec1_the_operator_delete_function1.cpp  
// compile with: /EHsc  
// arguments: 3  
#include <iostream>  
using namespace std;  
  
int fLogMemory = 0;      // Perform logging (0=no; nonzero=yes)?  
int cBlocksAllocated = 0;  // Count of blocks allocated.  
  
// User-defined operator new.  
void *operator new( size_t stAllocateBlock ) {  
   static int fInOpNew = 0;   // Guard flag.  
  
   if ( fLogMemory && !fInOpNew ) {  
      fInOpNew = 1;  
      clog << "Memory block " << ++cBlocksAllocated  
          << " allocated for " << stAllocateBlock  
          << " bytes\n";  
      fInOpNew = 0;  
   }  
   return malloc( stAllocateBlock );  
}  
  
// User-defined operator delete.  
void operator delete( void *pvMem ) {  
   static int fInOpDelete = 0;   // Guard flag.  
   if ( fLogMemory && !fInOpDelete ) {  
      fInOpDelete = 1;  
      clog << "Memory block " << cBlocksAllocated--  
          << " deallocated\n";  
      fInOpDelete = 0;  
   }  
  
   free( pvMem );  
}  
  
int main( int argc, char *argv[] ) {  
   fLogMemory = 1;   // Turn logging on  
   if( argc > 1 )  
      for( int i = 0; i < atoi( argv[1] ); ++i ) {  
         char *pMem = new char[10];  
         delete[] pMem;  
      }  
   fLogMemory = 0;  // Turn logging off.  
   return cBlocksAllocated;  
}  
```  
  
 Předchozí kód můžete použít k detekci "úniku paměti" – to znamená, paměti, která je přidělena na úložišti volné, ale nebyla uvolněna. K provedení této detekce na globální **nové** a **odstranit** operátory jsou předefinována počet přidělení a zrušení přidělení paměti.  
  
 Od verze Visual C++ 5.0, kompilátor podporuje pole člen **nové** a **odstranit** operátory v deklaraci třídy. Příklad:  
  
```cpp  
// spec1_the_operator_delete_function2.cpp  
// compile with: /c  
class X  {  
public:  
   void * operator new[] (size_t) {  
      return 0;  
   }  
   void operator delete[] (void*) {}  
};  
  
void f() {  
   X *pX = new X[5];  
   delete [] pX;  
}  
```  

