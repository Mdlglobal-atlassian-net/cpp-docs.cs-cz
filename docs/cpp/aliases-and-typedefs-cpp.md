---
title: Aliasy a definice TypeDef (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- typedef_cpp
dev_langs:
- C++
ms.assetid: af1c24d2-4bfd-408a-acfc-482e264232f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c020d9fc4a8bc5275fe77b05eff74fdcec25ec6c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="aliases-and-typedefs-c"></a>Aliasy a definice Typedef (C++)
Můžete použít *alias deklarace* deklarovat název, který bude používat jako synonymum pro dříve deklarovaného typu. (Tento mechanismus se také označuje neformálně jako *typ alias*). Tento mechanismus můžete také použít k vytvoření *alias šablony*, což může být obzvláště užitečné pro vlastní alokátorů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
using identifier = type;  
```  
  
## <a name="remarks"></a>Poznámky  
 `identifier`  
 Název aliasu.  
  
 `type`  
 Identifikátor typu, který vytváříte alias.  
  
 Alias nezavádí nový typ a nelze změnit význam stávající název typu.  
  
 Nejjednodušší forma alias je ekvivalentní `typedef` mechanismus z C ++ 03:  
  
```cpp  
// C++11  
using counter = long;  
  
// C++03 equivalent:  
// typedef long counter;  
```  
  
 Obě tyto umožňují vytvářet proměnné typu "čítač". Něco užitečnější by alias typ tohoto typu pro `std::ios_base::fmtflags`:  
  
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
  
 Aliasy také práci s ukazatelů na funkce, ale jsou mnohem srozumitelnější než ekvivalentní typedef:  
  
```cpp  
// C++11  
using func = void(*)(int);  
  
// C++03 equivalent:  
// typedef void (*func)(int);  
  
// func can be assigned to a function pointer value  
void actual_function(int arg) { /* some code */ }  
func fptr = &actual_function;  
  
```  
  
 O omezení `typedef` mechanismus je, že předchozí postup nebude fungovat se šablonami. Typ alias syntaxe C ++ 11 však umožňuje vytváření šablon alias:  
  
```cpp  
template<typename T> using ptr = T*;   
  
// the name 'ptr<T>' is now an alias for pointer to T  
ptr<int> ptr_int;  
  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat šablonu alias s vlastní allocator – v takovém případě celé vector typu. Můžete nahradit libovolný typ pro `int` Chcete-li vytvořit alias pohodlný skrytí komplexního parametru jsou uvedené v hlavním funkční kódu. Pomocí přidělujícího modulu vlastní prostřednictvím vašeho kódu můžete zlepšení čitelnosti a snižte riziko představení chyby způsobené překlepům.  
  
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
 A `typedef` deklarace představuje název, který v rámci svého oboru, stane synonymum pro typ poskytují *deklaraci typu* část deklarace.  
  
 Deklarace typedef je možné použít k vytvoření kratších nebo výstižnějších názvů pro typy, které jsou již definovány jazykem, nebo vlastní deklarované typy. Názvy typedef umožňují zapouzdřit podrobnosti implementace, které se mohou změnit.  
  
 Rozdíl k **třída**, `struct`, **– typ union**, a `enum` deklarace, `typedef` deklarace není zavést nové typy – se zavést nové názvy pro existující typy.  
  
 Názvy deklarováno s použitím `typedef` zabírají stejného oboru názvů jako ostatní identifikátory (s výjimkou příkaz popisky). Proto nemohou používat identifikátor shodný s dříve deklarovaným názvem, vyjma deklarací typů tříd. Podívejte se na následující příklad:  
  
```  
// typedef_names1.cpp  
// C2377 expected  
typedef unsigned long UL;   // Declare a typedef name, UL.  
int UL;                     // C2377: redefined.  
```  
  
 Pravidla skrývání názvů platná pro jiné identifikátory řídí i viditelnost názvů deklarovaných pomocí direktivy `typedef`. Následující příklad je proto v jazyce C++ platný:  
  
```  
// typedef_names2.cpp  
typedef unsigned long UL;   // Declare a typedef name, UL  
int main()  
{  
   unsigned int UL;   // Redeclaration hides typedef name  
}  
  
// typedef UL back in scope  
```  
 
  
```  
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
  
```  
typedef char FlagType;  
const FlagType x;  
```  
  
 Pro opětovné použití názvu `FlagType` pro identifikátor, člen struktury nebo člen sjednocení musí být určen typ:  
  
```  
const int FlagType;  // Type specifier required  
```  
  
 Nestačí říct  
  
```  
const FlagType;      // Incomplete specification  
```  
  
 protože `FlagType` se považuje za část typu, nikoli identifikátor, který je znovu deklarován. Tato deklarace je neplatnou jako  
  
```  
int;  // Illegal declaration   
```  
  
 Pomocí typedef je možné deklarovat jakýkoli typ, včetně ukazatele, funkce a typů polí. Je možné deklarovat název typedef pro ukazatel na typ struktury nebo sjednocení před definováním typu struktury nebo sjednocení, pokud má definice stejnou viditelnost jako deklarace.  
  
### <a name="examples"></a>Příklady  
 Jedno z použití deklarací `typedef` je vytvoření jednotnějších a kompaktnějších deklarací. Příklad:  
  
```cpp  
typedef char CHAR;          // Character type.  
typedef CHAR * PSTR;        // Pointer to a string (char *).  
PSTR strchr( PSTR source, CHAR target );  
typedef unsigned long ulong;  
ulong ul;     // Equivalent to "unsigned long ul;"  
```  
  
 Pro použití klíčového slova `typedef` ke specifikaci základních a odvozených typů ve stejné deklaraci je možné oddělit deklarátory čárkami. Příklad:  
  
```  
typedef char CHAR, *PSTR;  
```  
  
 Následující příklad poskytuje typ `DRAWF` pro funkci nevracející žádnou hodnotu a přijímající dva celočíselné argumenty:  
  
```  
typedef void DRAWF( int, int );  
```  
  
 Po výše uvedeném příkazu `typedef` bude deklarace  
  
```  
DRAWF box;   
```  
  
 ekvivalentní deklaraci  
  
```  
void box( int, int );  
```  
  
 Klíčové slovo `typedef` je často spojeno s klíčovým slovem `struct` pro deklarování a pojmenování uživatelských typů:  
  
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
  
### <a name="re-declaration-of-typedefs"></a>Opakované deklarace – definice TypeDef  
 Deklaraci `typedef` lze použít ke změně deklarace stejného názvu k odkazování na stejný typ. Příklad:  
  
```cpp  
// FILE1.H  
typedef char CHAR;  
  
// FILE2.H  
typedef char CHAR;  
  
// PROG.CPP  
#include "file1.h"  
#include "file2.h"   // OK  
```  
  
 Program PROG.CPP obsahuje dva soubory hlaviček, z nichž oba obsahují deklarace `typedef` pro název `CHAR`. Pokud obě tyto deklarace odkazují na stejný typ, je taková změna deklarace přijatelná.  
  
 Deklarace `typedef` nemůže předefinovat název, který byl dříve deklarován jako jiný typ. Proto pokud soubor FILE2.H obsahuje  
  
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
  
### <a name="typedefs-in-c-vs-c"></a>Definice TypeDef v C++ vs. C  
 Použití specifikátoru `typedef` spolu s typy tříd je široce podporováno kvůli postupům standardu ANSI C při deklarování nepojmenovaných struktur u deklarací `typedef`. Mnoho programátorů v jazyce C používá například následující:  
  
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
  
```  
POINT ptOrigin;  
```  
  
 místo:  
  
```  
struct point_t ptOrigin;  
```  
  
 V jazyce C++ rozdíl mezi `typedef` názvy a typy skutečné (deklarovat s **třída**, `struct`, **sjednocení**, a `enum` klíčová slova) více jedinečná. Přestože postup uplatňovaný v jazyce C, který spočívá v deklaraci nepojmenované struktury v příkazu `typedef`, stále funguje, neposkytuje žádné konvenční výhody jako v jazyce C.  
  
```cpp  
// typedef_with_class_types2.cpp  
// compile with: /c /W1  
typedef struct {  
   int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```  
  
 Předchozí příklad deklaruje třídu s názvem `POINT` pomocí syntaxe nepojmenované třídy `typedef`. `POINT` je považován za název třídy. Na názvy zavedené tímto způsobem se však vztahují následující omezení:  
  
-   Název (synonymum) se nesmí nacházet za **třída**, `struct`, nebo **sjednocení** předponu.  
  
-   Název nelze použít jako název konstruktoru nebo destruktoru v deklaraci třídy.  
  
 Tato syntaxe v souhrnu neposkytuje žádný mechanismus dědičnosti, vytvoření nebo zničení.  
