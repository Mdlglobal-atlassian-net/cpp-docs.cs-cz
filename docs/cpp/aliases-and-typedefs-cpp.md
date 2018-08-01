---
title: Aliasy a definice TypeDef (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 5fe9e5c1099f6c30483cdb20c48daf9c35fbed8e
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404974"
---
# <a name="aliases-and-typedefs-c"></a>Aliasy a definice Typedef (C++)
Můžete použít *deklarace aliasu* deklarovat název, který chcete použít jako synonymum pro dřív deklarovaného typu. (Tento mechanismus se také nazývá neformálně *alias typu*). Tento mechanismus lze také použít k vytvoření *šablonu aliasů*, což může být zvláště užitečná pro vlastních alokátorů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
using identifier = type;  
```  
  
## <a name="remarks"></a>Poznámky  
 *identifikátor*  
 Název aliasu.  
  
 *Typ*  
 Identifikátor typu, kterou vytváříte alias.  
  
 Alias nezavádí nový typ a nelze změnit význam existujícím názvem typu.  
  
 Nejjednodušší forma alias je ekvivalentní **typedef** mechanismus z C ++ 03:  
  
```cpp  
// C++11  
using counter = long;  
  
// C++03 equivalent:  
// typedef long counter;  
```  
  
 Obě tyto umožňují vytvářet proměnné typu informací, že čítač". Něco užitečnější by být alias typu, jako je ten pro `std::ios_base::fmtflags`:  
  
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
  
 Aliasy také fungovat ukazatelů na funkce, ale jsou mnohem čitelnější než ekvivalentní definice typu:  
  
```cpp  
// C++11  
using func = void(*)(int);  
  
// C++03 equivalent:  
// typedef void (*func)(int);  
  
// func can be assigned to a function pointer value  
void actual_function(int arg) { /* some code */ }  
func fptr = &actual_function;  
  
```  
  
 Omezení **typedef** mechanismu je, že nebude fungovat se šablonami. Syntaxe alias typu v C ++ 11, ale umožňuje vytvářet šablony aliasů:  
  
```cpp  
template<typename T> using ptr = T*;   
  
// the name 'ptr<T>' is now an alias for pointer to T  
ptr<int> ptr_int;  
  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí vlastního alokátoru šabloně aliasů – v takovém případě celé vektorového typu. Můžete použít libovolný typ pro **int** vytvořit alias vhodné skrýt komplexního parametru jsou uvedeny v hlavním funkční kódu. Pomocí vlastního alokátoru v rámci kódu můžete zlepšit čitelnost a snížit riziko zavlečení chyby způsobené překlepy.  
  
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
 A **typedef** deklarace zavádí název, který v rámci své působnosti stane synonymem pro typ daný *deklarace typu* částí deklarace.  
  
 Deklarace typedef je možné použít k vytvoření kratších nebo výstižnějších názvů pro typy, které jsou již definovány jazykem, nebo vlastní deklarované typy. Názvy typedef umožňují zapouzdřit podrobnosti implementace, které se mohou změnit.  
  
 Rozdíl od **třídy**, **struktury**, **sjednocení**, a **výčtu** deklarace, **typedef** deklarace nezavádí nové typy – ale zavádí nové názvy pro existující typy.  
  
 Názvy deklarované pomocí **typedef** zabírat stejný obor názvů jako jiné identifikátory (kromě popisků příkazů). Proto nemohou používat identifikátor shodný s dříve deklarovaným názvem, vyjma deklarací typů tříd. Vezměte v úvahu v následujícím příkladu:  
  
```cpp 
// typedef_names1.cpp  
// C2377 expected  
typedef unsigned long UL;   // Declare a typedef name, UL.  
int UL;                     // C2377: redefined.  
```  
  
 Pravidla skrývání názvů, které se vztahují na jiné identifikátory řídí i viditelnost názvů deklarovaných pomocí **typedef**. Následující příklad je proto v jazyce C++ platný:  
  
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
 Jedno použití **typedef** deklarace je, aby deklarace jednotnějších a kompaktnějších. Příklad:  
  
```cpp  
typedef char CHAR;          // Character type.  
typedef CHAR * PSTR;        // Pointer to a string (char *).  
PSTR strchr( PSTR source, CHAR target );  
typedef unsigned long ulong;  
ulong ul;     // Equivalent to "unsigned long ul;"  
```  
  
 Chcete-li použít **typedef** stanovit základních a odvozených typů ve stejné deklaraci je možné oddělit deklarátory čárkami. Příklad:  
  
```cpp 
typedef char CHAR, *PSTR;  
```  
  
 Následující příklad poskytuje typ `DRAWF` pro funkci nevracející žádnou hodnotu a přijímající dva celočíselné argumenty:  
  
```cpp 
typedef void DRAWF( int, int );  
```  
  
 Po výše uvedeném **typedef** prohlášení, deklarace  
  
```cpp 
DRAWF box;   
```  
  
 ekvivalentní deklaraci  
  
```cpp 
void box( int, int );  
```  
  
 **Definice TypeDef** je často v kombinaci s **struktura** pro deklarování a pojmenování uživatelských typů:  
  
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
  
### <a name="re-declaration-of-typedefs"></a>Opětovná deklarace TypeDef  
 **Typedef** ke změně deklarace stejného názvu k odkazování na stejný typ. je možné deklarace. Příklad:  
  
```cpp  
// FILE1.H  
typedef char CHAR;  
  
// FILE2.H  
typedef char CHAR;  
  
// PROG.CPP  
#include "file1.h"  
#include "file2.h"   // OK  
``` 
  
 Program *ProgID. CPP* obsahuje dva soubory hlaviček, z nichž oba obsahují **typedef** deklarace pro název `CHAR`. Pokud obě tyto deklarace odkazují na stejný typ, je taková změna deklarace přijatelná.  
  
 A **typedef** název, který se dřív deklaroval jako jiný typ nejde předefinovat. Proto pokud *FILE2. H* obsahuje  
  
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
  
### <a name="typedefs-in-c-vs-c"></a>v sadě Visual Studio C++ – definice TypeDef. C  
 Použití **typedef** specifikátor s typy tříd je široce podporováno kvůli ANSI C při deklarování nepojmenovaných struktur u **– typedef** deklarace. Mnoho programátorů v jazyce C používá například následující:  
  
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
  
 V jazyce C++ je rozdíl mezi **– typedef** názvy a reálnými typy (deklarované pomocí **třídy**, **struktury**, **sjednocení**a **výčtu** klíčových slov) zřetelný. I když deklaraci nepojmenované struktury v praxi C **typedef** příkazu stále funguje, žádné konvenční výhody jako v jazyce C.  
  
```cpp  
// typedef_with_class_types2.cpp  
// compile with: /c /W1  
typedef struct {  
   int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```  
  
 Předchozí příklad deklaruje třídu s názvem `POINT` pomocí Nepojmenovaná třída **typedef** syntaxe. `POINT` je považován za název třídy. Na názvy zavedené tímto způsobem se však vztahují následující omezení:  
  
-   Název (synonymum) se nemůže objevit po **třídy**, **struktura**, nebo **sjednocení** předponu.  
  
-   Název nelze použít jako název konstruktoru nebo destruktoru v deklaraci třídy.  
  
 Tato syntaxe v souhrnu neposkytuje žádný mechanismus dědičnosti, vytvoření nebo zničení.  