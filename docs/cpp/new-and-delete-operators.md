---
title: nové a odstranit operátory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 447a03cec8beba331aedc8077a44dc9090fccbc6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078521"
---
# <a name="new-and-delete-operators"></a>Operátory new a delete

Jazyk C++ podporuje dynamické přidělování a navracení objektů pomocí [nové](../cpp/new-operator-cpp.md) a [odstranit](../cpp/delete-operator-cpp.md) operátory. Tyto operátory přidělují paměť objektům z fondu s názvem volné úložiště. **Nové** operátor volá funkci speciální [operátor new](../cpp/new-operator-cpp.md)a **odstranit** operátor volá funkci speciální [operátor delete](../cpp/delete-operator-cpp.md).

**Nové** podporuje funkce ve standardní knihovně jazyka C++ chování podle standardu jazyka C++, což je vyvolání výjimky std::bad_alloc Pokud selhání přidělení paměti. Pokud stále chcete non-throwing. verzi **nové**, propojit aplikaci s nothrownew.obj. Ale při propojení s nothrownew.obj výchozí **operátor new** ve standardní knihovně C++ nebude dál fungovat.

Seznam souborů knihoven, které tvoří knihovny prostředí Runtime jazyka C a standardní knihovny C++, naleznete v tématu [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).

##  <a id="new_operator"> </a> New – operátor

Například následující příkaz vyskytne v programu v jazyce, je přeložen volání funkce **operátor new**:

```cpp
char *pch = new char[BUFFER_SIZE];
```

Pokud je požadavek pro nula bajtů úložiště, **operátor new** vrací ukazatel na konkrétní objekt (opakovaná volání **operátor new** vrátí různé ukazatele). Pokud není dostatek paměti pro požadavek na přidělení, **operátor new** vyvolá výjimku std::bad_alloc, nebo vrátí **nullptr** případě propojení v non-throwing. **operátor new** podporovat.

Lze napsat rutinu, která se pokusí uvolnit paměť a opakovat přidělení; Zobrazit [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) Další informace. Podrobné informace o schématu obnovení naleznete v části zpracování není dostatek paměti tohoto tématu.

Dva obory **operátor new** funkce jsou popsány v následující tabulce.

### <a name="scope-for-operator-new-functions"></a>Obor pro funkce operator new

|Operátor|Rozsah|
|--------------|-----------|
|**:: new – operátor**|Globální|
|*Název třídy* **:: new – operátor**|Třída|

První argument **operátor new** musí být typu `size_t` (typ definovaný v \<stddef.h >), a návratový typ je vždy **void** <strong>\*</strong>.

Globální **operátor new** funkce je volána, když **nové** operátor se používá k přidělení paměti pro objekty předdefinovaných typů, uživatelem definované objekty typu třídy, které neobsahují **operátor new** funkce a pole libovolného typu. Při **nové** operátor se používá k přidělení paměti pro objekty typu třídy kde **operátor new** je definován, tuto třídu **operátor new** je volána.

**Operátor new** definovanou pro třídu je statickou členskou funkcí (který, proto nelze virtuální), která skrývá globální funkci **operátor new** funkce pro objekty typu třídy. Vezměte si situaci, kdy **nové** se používá k přidělení a nastavení paměti dané hodnotě:

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

Argument zadaný v závorkách **nové** je předán `Blanks::operator new` jako `chInit` argument. Ale globální **operátor new** funkce je skrytá, způsobí kód například následující vygeneruje chybu:

```cpp
Blanks *SomeBlanks = new Blanks;
```

Ve Visual C++ 5.0 a starších netřídní typy a všechna pole (bez ohledu na to, zda byly **třídy** typ) přidělena pomocí **nové** operátor vždy použít globální **operátor new** funkce.

Od verze Visual C++ 5.0, kompilátor podporuje členská pole **nové** a **odstranit** operátory v deklaraci třídy. Příklad:

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

Neexistuje jiný způsob zpracování požadavků na přidělení paměti selhalo: napsat vlastní rutinu obnovení pro zpracování takového selhání, pak registraci funkci voláním [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) funkci run-time.

##  <a id="delete_operator"> </a> Operátor delete

Paměti dynamicky přidělené pomocí **nové** operátor může být uvolněna pomocí **odstranit** operátor. Volání operátoru delete **operátor delete** funkce, která uvolní paměť zpět do fondu k dispozici. Použití **odstranit** operátor také způsobí, že destruktor třídy (pokud existuje) má být volána.

Globální a s rozsahem třídy **operátor delete** funkce. Pouze jeden **operátor delete** funkce lze definovat pro danou třídu; Pokud definována, skrývá globální **operátor delete** funkce. Globální **operátor delete** funkce je volána vždy pro pole libovolného typu.

Globální **operátor delete** funkce. Existují dvě formy pro globální **operátor delete** a člen třídy **operátor delete** funkce:

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

Pouze jeden z předchozí dvě různými formami může být k dispozici pro danou třídu. První formulář přijímá jeden argument typu `void *`, který obsahuje ukazatel na objekt, který chcete uvolnit. Druhý formulář – velikostí dealokace – přebírá dva argumenty, první z nich je ukazatelem na blok paměti určený k uvolnění a druhý z nich je počet bajtů k přidělení. Návratový typ obě formy **void** (**operátor delete** nemůže vracet hodnotu).

Záměrem druhý formulář je k urychlení vyhledávání ke kategorii správnou velikost pro objekt, který má být odstraněna, který je často není uložen téměř přidělení samotného a pravděpodobně bez mezipaměti; druhý typ je zvláště užitečné, když **operátor delete** funkce ze základní třídy se používá k odstranění objektu odvozené třídy.

**Operátor delete** je funkce statická, proto nemůže být virtuální. **Operátor delete** funkce dodržuje řízení přístupu, jak je popsáno v [řízení přístupu členů](../cpp/member-access-control-cpp.md).

Následující příklad ukazuje definované uživatelem **operátor new** a **operátor delete** funkce navržené tak, aby přidělování a navrácení paměti protokolu:

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

Předchozí kód lze použít k detekci "úniku paměti" – to znamená, paměti, která je přidělené ve volném úložišti, ale nikdy uvolněna. K provedení této detekce, globální **nové** a **odstranit** operátory jsou předefinována na počet přidělování a navracení zpět paměti.

Od verze Visual C++ 5.0, kompilátor podporuje členská pole **nové** a **odstranit** operátory v deklaraci třídy. Příklad:

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