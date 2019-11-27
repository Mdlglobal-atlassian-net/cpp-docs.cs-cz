---
title: Operátory new a delete
ms.date: 11/19/2019
f1_keywords:
- delete_cpp
- new
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: c64b15f1e1e63b1e743743883429ffd11007de0a
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246439"
---
# <a name="new-and-delete-operators"></a>new a delete – operátory

C++podporuje dynamické přidělování a navracení objektů pomocí operátorů [New](new-operator-cpp.md) a [Delete](delete-operator-cpp.md) . Tyto operátory přidělují paměť objektům z fondu s názvem volné úložiště. Operátor **New** volá speciální [operátor funkce New](new-operator-cpp.md)a operátor **Delete** volá speciální [operátor delete](delete-operator-cpp.md).

**Nová** funkce ve C++ standardní knihovně podporuje chování zadané ve C++ standardu, což má vyvolat výjimku std:: bad_alloc, pokud se přidělení paměti nepovede. Pokud stále chcete nevyvolávánou verzi **nového**, propojte program s nothrownew. obj. Pokud však propojíte s nothrownew. obj, výchozí **operátor New** ve C++ standardní knihovně již nebude fungovat.

Seznam souborů knihoven, které tvoří běhovou knihovnu jazyka C a C++ standardní knihovnu, naleznete v tématu [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).

##  <a id="new_operator"></a> Operátor New

V případě, že se v programu objevil příkaz, jako je následující, se přeloží na volání **operátoru funkce New**:

```cpp
char *pch = new char[BUFFER_SIZE];
```

Pokud je požadavek na nulové bajty úložiště, **operátor New** vrátí ukazatel na odlišný objekt (to znamená, že opakovaná volání **operátoru new** vrací různé ukazatele). Pokud není k dispozici dostatek paměti pro požadavek na přidělení, **operátor New** vyvolá výjimku `std::bad_alloc`, nebo vrátí **nullptr** , pokud jste propojili v neaktivačním **operátoru nová** podpora.

Můžete napsat rutinu, která se pokusí uvolnit paměť a opakovat přidělení. Další informace najdete v tématu [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) . Další podrobnosti o schématu obnovení najdete v části zpracování nedostatku paměti v tomto tématu.

Dva obory pro **operátor New** Functions jsou popsány v následující tabulce.

### <a name="scope-for-operator-new-functions"></a>Rozsah pro funkce operator new

|Operátor|Obor|
|--------------|-----------|
|**:: operator new**|Globální|
|*název třídy* **:: operator new**|Třída|

První argument **operátoru new** musí být typu `size_t` (typ definovaný v \<STDDEF. h >) a návratový typ je vždycky **void** <strong>\*</strong>.

Globální funkce **operator new** je volána, když je operátor **New** použit k přidělení objektů předdefinovaných typů, objektů typu třídy, které neobsahují uživatelsky definované **operátory New** functions a pole libovolného typu. Když je operátor **New** použit k přidělení objektů typu třídy, kde je definován **operátor New** , je volána **Nová operátor** této třídy.

Funkce **operator new** definovaná pro třídu je statická členská funkce (která nemůže být proto virtuální), která skrývá globální funkci **operator new** pro objekty daného typu třídy. Vezměte v úvahu případ, kdy se **Nový** používá k přidělení a nastavení paměti pro danou hodnotu:

```cpp
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

Argument dodaný v závorkách do **nového** je předán `Blanks::operator new` jako argument `chInit`. Globální funkce **operator new** je však skrytá, což způsobí, že následující kód vygeneruje chybu:

```cpp
Blanks *SomeBlanks = new Blanks;
```

Kompilátor podporuje členské pole **New** a **Delete** operátory v deklaraci třídy. Příklad:

```cpp
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

### <a name="handling-insufficient-memory"></a>Zpracování nedostatečné paměti

Testování přidělení neúspěšné paměti lze provést, jak je znázorněno zde:

```cpp
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

Existuje jiný způsob, jak zpracovat neúspěšné požadavky na přidělení paměti. Zapište vlastní rutinu obnovení pro zpracování takového selhání a pak zaregistrujte funkci voláním funkce run-time [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) .

##  <a id="delete_operator"></a> Operátor delete

Paměť, která je dynamicky přidělena pomocí operátoru **New** , může být uvolněna pomocí operátoru **Delete** . Operátor delete volá funkci **operátoru delete** , která uvolní paměť zpátky do dostupného fondu. Použití operátoru **Delete** také způsobí, že destruktor třídy (pokud existuje), který má být volán.

Existují globální funkce pro **odstranění operátorů** a rozsahu třídy. Pro danou třídu lze definovat pouze jednu funkci **operátoru delete** ; je-li definována, skryje funkci globální **operátor delete** . Funkce globálního **operátoru delete** je vždy volána pro pole libovolného typu.

Funkce globálního **operátoru delete** Existují dva formuláře pro funkce globálního **operátoru delete** a **operátoru** člena třídy:

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Pro danou třídu může být přítomna pouze jedna z předchozích dvou forem. První formulář přebírá jeden argument typu `void *`, který obsahuje ukazatel na objekt, který má být vrácen. Druhý formulář – určení velikosti přidělení – přebírá dva argumenty, první z nich je ukazatel na blok paměti pro uvolnění a druhý z nich je počet bajtů, které mají být navrácena. Návratový typ obou forem je **void** (**operátor delete** nemůže vracet hodnotu).

Účelem druhé formy je urychlení vyhledávání pro kategorii správné velikosti objektu, který má být odstraněn, což je často neuloženo v blízkosti samotného přidělení a pravděpodobně není uloženo do mezipaměti. Druhý formulář je užitečný v případě, že **operátor delete** funkce ze základní třídy slouží k odstranění objektu odvozené třídy.

Funkce **operátoru delete** je statická; Proto nemůže být virtuální. Funkce **operátoru delete** dodržuje řízení přístupu, jak je popsáno v tématu [Member-Access Control](member-access-control-cpp.md).

Následující příklad ukazuje uživatelsky definované funkce **operator new** a **operátor delete** určené k protokolování přidělení a navracení paměti:

```cpp
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

Předchozí kód se dá použít ke zjištění "úniku paměti", tj. paměti, která je přidělená na bezplatné úložiště, ale nikdy se neuvolňuje. Chcete-li provést toto zjištění, jsou globální operátory **New** a **Delete** předefinovány pro počítání přidělení a navracení paměti.

Kompilátor podporuje členské pole **New** a **Delete** operátory v deklaraci třídy. Příklad:

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
