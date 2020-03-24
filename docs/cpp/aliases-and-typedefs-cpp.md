---
title: Aliasy a definice Typedef (C++)
ms.date: 11/04/2016
f1_keywords:
- typedef_cpp
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
ms.openlocfilehash: 7a45c4570341aca056b9d4c30ea496317a1ac96f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181561"
---
# <a name="aliases-and-typedefs-c"></a>Aliasy a definice Typedef (C++)

Můžete použít *deklaraci aliasu* k deklaraci názvu, který se má použít jako synonymum pro dřív deklarovaný typ. (Tento mechanismus je také označován jako neformálněný jako *alias typu*). Tento mechanismus můžete použít také k vytvoření *šablony aliasu*, která může být zvláště užitečná pro vlastní přidělování.

## <a name="syntax"></a>Syntaxe

```
using identifier = type;
```

## <a name="remarks"></a>Poznámky

*RID*<br/>
Název aliasu.

*type*<br/>
Identifikátor typu, pro který vytváříte alias.

Alias nezavádí nový typ a nemůže měnit význam stávajícího názvu typu.

Nejjednodušší forma aliasu je ekvivalentem mechanismu **typedef** z c++ 03:

```cpp
// C++11
using counter = long;

// C++03 equivalent:
// typedef long counter;
```

Obě tyto umožňují vytvoření proměnných typu "čítač". Něco užitečnější by představovalo alias typu, jako je tento alias pro `std::ios_base::fmtflags`:

```cpp
// C++11
using fmtfl = std::ios_base::fmtflags;

// C++03 equivalent:
// typedef std::ios_base::fmtflags fmtfl;

fmtfl fl_orig = std::cout.flags();
fmtfl fl_hex = (fl_orig & ~std::cout.basefield) | std::cout.showbase | std::cout.hex;
// ...
std::cout.flags(fl_hex);
```

Aliasy také fungují s ukazateli na funkce, ale jsou mnohem čitelnější než ekvivalentní definice typedef:

```cpp
// C++11
using func = void(*)(int);

// C++03 equivalent:
// typedef void (*func)(int);

// func can be assigned to a function pointer value
void actual_function(int arg) { /* some code */ }
func fptr = &actual_function;
```

Omezením mechanismu **typedef** je, že nefunguje se šablonami. Syntaxe aliasu typu v jazyce C++ 11 však umožňuje vytvoření šablon aliasů:

```cpp
template<typename T> using ptr = T*;

// the name 'ptr<T>' is now an alias for pointer to T
ptr<int> ptr_int;
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít šablonu aliasu s vlastním přidělováním – v tomto případě typ vektoru Integer. Můžete nahradit libovolný typ pro **int** a vytvořit pohodlný alias pro skrytí seznamů složitých parametrů v hlavním funkčním kódu. Pomocí vlastního přidělování v celém kódu můžete zlepšit čitelnost a snížit riziko zavedení chyb způsobených překlepy.

```cpp
#include <stdlib.h>
#include <new>

template <typename T> struct MyAlloc {
    typedef T value_type;

    MyAlloc() { }
    template <typename U> MyAlloc(const MyAlloc<U>&) { }

    bool operator==(const MyAlloc&) const { return true; }
    bool operator!=(const MyAlloc&) const { return false; }

    T * allocate(const size_t n) const {
        if (n == 0) {
            return nullptr;
        }

        if (n > static_cast<size_t>(-1) / sizeof(T)) {
            throw std::bad_array_new_length();
        }

        void * const pv = malloc(n * sizeof(T));

        if (!pv) {
            throw std::bad_alloc();
        }

        return static_cast<T *>(pv);
    }

    void deallocate(T * const p, size_t) const {
        free(p);
    }
};

#include <vector>
using MyIntVector = std::vector<int, MyAlloc<int>>;

#include <iostream>

int main ()
{
    MyIntVector foov = { 1701, 1764, 1664 };

    for (auto a: foov) std::cout << a << " ";
    std::cout << "\n";

    return 0;
}
```

```Output
1701 1764 1664
```

## <a name="typedefs"></a>Typedefs

Deklarace **typedef** zavádí název, který v rámci svého oboru se změní na synonymum pro typ předaný částí deklarace *typu* .

Deklarace typedef je možné použít k vytvoření kratších nebo výstižnějších názvů pro typy, které jsou již definovány jazykem, nebo vlastní deklarované typy. Názvy typedef umožňují zapouzdřit podrobnosti implementace, které se mohou změnit.

Na rozdíl od deklarací **třídy**, **struktury**, **sjednocení**a **výčtu** nezavádí deklarace **typedef** nové typy – zavádí nové názvy pro existující typy.

Názvy deklarované pomocí **typedef** zabírají stejný obor názvů jako jiné identifikátory (kromě popisků příkazů). Proto nemohou používat identifikátor shodný s dříve deklarovaným názvem, vyjma deklarací typů tříd. Vezměte v úvahu v následujícím příkladu:

```cpp
// typedef_names1.cpp
// C2377 expected
typedef unsigned long UL;   // Declare a typedef name, UL.
int UL;                     // C2377: redefined.
```

Pravidla skrývání názvů, která se vztahují k jiným identifikátorům, také řídí viditelnost názvů deklarovaných pomocí **typedef**. Následující příklad je proto v jazyce C++ platný:

```cpp
// typedef_names2.cpp
typedef unsigned long UL;   // Declare a typedef name, UL
int main()
{
   unsigned int UL;   // Redeclaration hides typedef name
}

// typedef UL back in scope
```

```cpp
// typedef_specifier1.cpp
typedef char FlagType;

int main()
{
}

void myproc( int )
{
    int FlagType;
}
```

Při deklarování identifikátoru místního oboru se stejným názvem jako typedef nebo při deklarování členu struktury nebo sjednocení ve stejném oboru nebo ve vnitřním oboru musí být určen specifikátor typu. Příklad:

```cpp
typedef char FlagType;
const FlagType x;
```

Pro opětovné použití názvu `FlagType` pro identifikátor, člen struktury nebo člen sjednocení musí být určen typ:

```cpp
const int FlagType;  // Type specifier required
```

Nestačí říct

```cpp
const FlagType;      // Incomplete specification
```

protože `FlagType` se považuje za část typu, nikoli identifikátor, který je znovu deklarován. Tato deklarace je neplatnou jako

```cpp
int;  // Illegal declaration
```

Pomocí typedef je možné deklarovat jakýkoli typ, včetně ukazatele, funkce a typů polí. Je možné deklarovat název typedef pro ukazatel na typ struktury nebo sjednocení před definováním typu struktury nebo sjednocení, pokud má definice stejnou viditelnost jako deklarace.

### <a name="examples"></a>Příklady

Jedním z použití deklarací **typedef** je vytvoření deklarací na základě jednotnosti a komprimace. Příklad:

```cpp
typedef char CHAR;          // Character type.
typedef CHAR * PSTR;        // Pointer to a string (char *).
PSTR strchr( PSTR source, CHAR target );
typedef unsigned long ulong;
ulong ul;     // Equivalent to "unsigned long ul;"
```

Chcete-li použít **typedef** k určení základních a odvozených typů ve stejné deklaraci, můžete oddělit deklarátory čárkami. Příklad:

```cpp
typedef char CHAR, *PSTR;
```

Následující příklad poskytuje typ `DRAWF` pro funkci nevracející žádnou hodnotu a přijímající dva celočíselné argumenty:

```cpp
typedef void DRAWF( int, int );
```

Po výše uvedeném příkazu **typedef** deklarace

```cpp
DRAWF box;
```

ekvivalentní deklaraci

```cpp
void box( int, int );
```

**definice typedef** je často kombinována s **strukturou** pro deklaraci a pojmenování uživatelsky definovaných typů:

```cpp
// typedef_specifier2.cpp
#include <stdio.h>

typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;

int main()
{
    mystruct ms;
    ms.i = 10;
    ms.f = 0.99;
    printf_s("%d   %f\n", ms.i, ms.f);
}
```

```Output
10   0.990000
```

### <a name="re-declaration-of-typedefs"></a>Změna deklarace definice typedef

Deklaraci **typedef** lze použít k předeklarování stejného názvu pro odkazování na stejný typ. Příklad:

```cpp
// FILE1.H
typedef char CHAR;

// FILE2.H
typedef char CHAR;

// PROG.CPP
#include "file1.h"
#include "file2.h"   // OK
```

*Programové programu CPP* obsahuje dva hlavičkové soubory, oba obsahují deklarace **typedef** pro název `CHAR`. Pokud obě tyto deklarace odkazují na stejný typ, je taková změna deklarace přijatelná.

**Definice typedef** nemůže předefinovat název, který byl dříve deklarován jako jiný typ. Proto, pokud *Soubor2. H* obsahuje

```cpp
// FILE2.H
typedef int CHAR;     // Error
```

kompilátor vygeneruje chybu z důvodu pokusu o změnu deklarace názvu `CHAR`, aby odkazoval na jiný typ. Dojde k rozšíření na konstrukce, jako jsou například:

```cpp
typedef char CHAR;
typedef CHAR CHAR;      // OK: redeclared as same type

typedef union REGS      // OK: name REGS redeclared
{                       //  by typedef name with the
    struct wordregs x;  //  same meaning.
    struct byteregs h;
} REGS;
```

### <a name="typedefs-in-c-vs-c"></a>definice typedef v C++ vs. C

Použití specifikátoru **typedef** s typy tříd je v podstatě podporováno z důvodu praxe ANSI C při deklaraci nepojmenovaných struktur v deklaracích **typedef** . Mnoho programátorů v jazyce C používá například následující:

```cpp
// typedef_with_class_types1.cpp
// compile with: /c
typedef struct {   // Declare an unnamed structure and give it the
                   // typedef name POINT.
   unsigned x;
   unsigned y;
} POINT;
```

Výhodou takovéto deklarace je, že umožňuje deklarace, jako jsou:

```cpp
POINT ptOrigin;
```

místo:

```cpp
struct point_t ptOrigin;
```

V C++nástroji je rozdíl mezi názvy **typedef** a typy reálných hodnot (deklarovaných pomocí klíčových slov **Class**, **struct**, **Union**a **Enum** ) více jedinečný. I když postupy jazyka C při deklaraci struktury Nameless v příkazu **typedef** stále fungují, neposkytuje žádné nevýhodné výhody jako v jazyce C.

```cpp
// typedef_with_class_types2.cpp
// compile with: /c /W1
typedef struct {
   int POINT();
   unsigned x;
   unsigned y;
} POINT;
```

Předchozí příklad deklaruje třídu s názvem `POINT` pomocí nepojmenované syntaxe **typedef** třídy. `POINT` se považuje za název třídy; následující omezení se ale vztahují na názvy zavedené tímto způsobem:

- Název (synonymum) se nemůže vyskytovat za předponou **třídy**, **struktury**nebo **sjednocení** .

- Název nelze použít jako název konstruktoru nebo destruktoru v deklaraci třídy.

Tato syntaxe v souhrnu neposkytuje žádný mechanismus dědičnosti, vytvoření nebo zničení.
