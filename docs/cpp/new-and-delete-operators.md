---
title: Operátory new a delete
ms.date: 11/19/2019
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: fd170c1500e2d80879fdd89f7d825930189ae942
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367887"
---
# <a name="new-and-delete-operators"></a>new a delete – operátory

C++ podporuje dynamické přidělování a amlokace objektů pomocí [nové](new-operator-cpp.md) a [odstranit](delete-operator-cpp.md) operátory. Tyto operátory přidělují paměť objektům z fondu s názvem volné úložiště. **Nový** operátor volá [operátor](new-operator-cpp.md)speciální funkce nový a **operátor delete** volá operátor speciální funkce [delete](delete-operator-cpp.md).

**Nová** funkce ve standardní knihovně jazyka C++ podporuje chování zadané ve standardu Jazyka C++, kterým je vyvolání výjimky std::bad_alloc, pokud se přidělení paměti nezdaří. Pokud stále chcete non-házení verzi **nového**, propojit program s nothrownew.obj. Však při propojení s nothrownew.obj, výchozí **operátor nový** ve standardní knihovně C++ již funkce.

Seznam souborů knihovny, které tvoří knihovnu C Runtime a standardní knihovnu jazyka C++, naleznete v [tématu Funkce knihovny CRT](../c-runtime-library/crt-library-features.md).

## <a name="the-new-operator"></a><a id="new_operator"> </a> Nový operátor

Pokud je v programu zjištěn příkaz, například následující, převede se do volání **operátoru**funkce new :

```cpp
char *pch = new char[BUFFER_SIZE];
```

Pokud je požadavek pro nula bajtů úložiště, **operátor new** vrátí ukazatel na jiný objekt (to znamená, že opakované volání **operátoru new** vrátit různé ukazatele). Pokud není dostatek paměti pro požadavek přidělení, `std::bad_alloc` operátor **new** vyvolá výjimku nebo vrátí **nullptr,** pokud jste propojili v operátoru bez vyvolání **nové** podpory.

Můžete napsat rutinu, která se pokusí uvolnit paměť a opakovat přidělení; další informace naleznete [_set_new_handler.](../c-runtime-library/reference/set-new-handler.md) Další podrobnosti o schématu obnovení naleznete zpracování nedostatek paměti části tohoto tématu.

Dva obory pro nové funkce **operátoru** jsou popsány v následující tabulce.

### <a name="scope-for-operator-new-functions"></a>Prostor pro nové funkce operátora

|Operátor|Rozsah|
|--------------|-----------|
|**::operátor nový**|Globální|
|*název třídy* **::operátor nový**|Třída|

První argument **operátoru new** musí `size_t` být typu \<(typ definovaný v> stddef.h) a návratový typ je vždy **void** <strong>\*</strong>.

Globální **operátor nová** funkce je volána při **nový** operátor se používá k přidělení objekty předdefinované typy, objekty typu třídy, které neobsahují uživatelem definované **operátor nové** funkce a pole libovolného typu. Při **nové** operátor slouží k přidělení objektů typu třídy, kde je definován **operátor new,** operátor této třídy **new** se nazývá.

**Operátor nová** funkce definovaná pro třídu je statická členská funkce (která proto nemůže být virtuální), která skryje novou funkci globálního **operátoru** pro objekty tohoto typu třídy. Zvažte případ, kdy **se nový** používá k přidělení a nastavení paměti na danou hodnotu:

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

Argument zadaný v závorce **na new** je předán `Blanks::operator new` jako `chInit` argument. Globální operátor **nová** funkce je však skrytý, což způsobuje kód, jako je například následující generovat chybu:

```cpp
Blanks *SomeBlanks = new Blanks;
```

Kompilátor podporuje **nové** pole členů a **odstranění** operátorů v deklaraci třídy. Příklad:

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

### <a name="handling-insufficient-memory"></a>Zpracování nedostatku paměti

Testování neúspěšného přidělení paměti lze provést tak, jak je znázorněno zde:

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

Existuje jiný způsob, jak zpracovat neúspěšné požadavky na přidělení paměti. Napište vlastní rutinu obnovení pro zpracování takového selhání a zaregistrujte funkci voláním [funkce _set_new_handler](../c-runtime-library/reference/set-new-handler.md) run-time.

## <a name="the-delete-operator"></a><a id="delete_operator"> </a> Operátor odstranění

Paměť, která je dynamicky přidělena pomocí **nového** operátoru, může být uvolněna pomocí operátoru **delete.** Operátor delete volá funkci **delete operátoru,** která uvolní paměť zpět do dostupného fondu. Pomocí **delete** operátor také způsobí, že destruktor třídy (pokud existuje) má být volána.

Existují globální a třídy **rozsahem operátor odstranit** funkce. Pro danou třídu lze definovat pouze jednu funkci **odstranění operátoru;** pokud je definována, skryje funkci **global operator delete.** Funkce odstranění globálního **operátora** je vždy volána pro pole libovolného typu.

Funkce **odstranění** globálního operátoru. Existují dva formuláře pro funkce odstranění globálního **operátoru** a **operátoru** člena třídy:

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Pouze jeden z předchozích dvou formulářů může být k dispozici pro danou třídu. První formulář má jeden argument `void *`typu , který obsahuje ukazatel na objekt navrátit. Druhý formulář – velikost deallocation – trvá dva argumenty, z nichž první je ukazatel na blok paměti navrátit a druhý z nich je počet bajtů navrátit. Návratový typ obou formulářů je **void** **(operátor delete** nemůže vrátit hodnotu).

Záměrem druhého formuláře je urychlit hledání správné kategorie velikosti objektu, který má být odstraněn, který často není uložen v blízkosti samotného přidělení a pravděpodobně uncached. Druhý formulář je užitečné při **operátor odstranit** funkci ze základní třídy se používá k odstranění objektu odvozené třídy.

Funkce **odstranění operátora** je statická; proto nemůže být virtuální. Funkce **odstranění operátoru** se řídí řízením přístupu, jak je popsáno v [ovládacím prvku Členské řízení přístupu](member-access-control-cpp.md).

Následující příklad ukazuje uživatelem definované **operátor nové** a **operátor odstranit** funkce určené k protokolu přidělení a deallocations paměti:

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

Předchozí kód lze použít ke zjištění "úniku paměti" – to znamená paměti, která je přidělena na volném úložišti, ale nikdy uvolněna. Chcete-li provést toto zjišťování, globální **nové** a **odstranit** operátory jsou předefinovány počítat přidělení a amlokace paměti.

Kompilátor podporuje **nové** pole členů a **odstranění** operátorů v deklaraci třídy. Příklad:

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
