---
title: Třídy úložiště (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- thread_local_cpp
- external_cpp
- static_cpp
- register_cpp
dev_langs:
- C++
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 659b76a640a0dfaee75179f135fee9d1eeb5ba02
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058333"
---
# <a name="storage-classes-c"></a>Třídy úložiště (C++)

A *třídu úložiště* deklarace proměnných v rámci jazyka C++ je specifikátor typu, který řídí životnost, propojení a paměti umístění objektů. Předaný objekt může mít pouze jednu třídu úložiště. Proměnné definované v rámci bloku mají automatického úložiště, pokud není stanoveno jinak pomocí **extern**, **statické**, nebo `thread_local` specifikátorů. Automatické objekty a proměnné nemají žádné propojení; nejsou viditelné pro kód mimo blok.

**Poznámky**

1. [Proměnlivé](../cpp/mutable-data-members-cpp.md) – klíčové slovo lze považovat za specifikátor paměťové třídy. Je však pouze k dispozici v sezamu členů definice třídy.

1. **Visual C++ 2010 nebo novějším:** **automaticky** – klíčové slovo již není specifikátorem třídy úložiště jazyka C++ a **zaregistrovat** – klíčové slovo je zastaralý. **Visual Studio 2017 verze 15.7 nebo novější:** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): **zaregistrovat** – klíčové slovo se odebere z jazyka C++.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="in-this-section"></a>V této části:

- [static](#static)
- [extern](#extern)
- [možnost thread_local](#thread_local)

## <a name="static"></a> Statická

**Statické** – klíčové slovo lze použít k deklarování proměnných a funkcí v globálním oboru, oboru názvů a oboru třídy. Statické proměnné lze také deklarovat v místním oboru.

Statické trvání znamená, že objekt nebo proměnná jsou přiděleny po spuštění programu a je uvolněno spolu s ukončením programu. Externí propojení znamená, že je název proměnné viditelné z vnějšku souboru, ve kterém je deklarována. Naopak interní propojení znamená, že název není viditelné z vnějšku souboru, ve kterém je deklarována. Standardně má objekt nebo proměnná, která je definována v globálním oboru názvů statické trvání a vnější propojení. **Statické** – klíčové slovo lze použít v následujících situacích.

1. Pokud deklarujete proměnnou nebo funkci v rozsahu souboru (globální nebo obor názvů), **statické** – klíčové slovo určuje, že proměnná nebo funkce má vnitřní propojení. Při deklarování proměnné proměnná obsahuje statické trvání a kompilátor inicializuje ji na hodnotu 0 neurčíte jinou hodnotu.

1. Při deklaraci proměnné ve funkci, **statické** – klíčové slovo určuje, že proměnná zůstane ve stavu mezi volání této funkce.

1. Když deklarujete datový člen v deklaraci třídy **statické** – klíčové slovo určuje, že jedna kopie člena je sdílena všemi instancemi třídy. Statický datový člen musí být definován v rozsahu souboru. Integrální datový člen, který deklarujete jako **const static** může mít inicializátor.

1. Když deklarujete člena funkce v deklaraci třídy **statické** – klíčové slovo určuje, že funkce je sdílena všemi instancemi třídy. Statické členské funkce nelze přistupovat k členu instance, protože funkce nemá implicitní **to** ukazatele. Chcete-li získat přístup k instanci člena, deklarujte funkci s parametrem, který je instancí ukazatele nebo odkazu.

1. Nelze deklarovat členy unie jako statické. Nicméně globálně deklarované anonymní sjednocení musí být explicitně deklarovány **statické**.

Tento příklad ukazuje, jak si deklarovaná proměnná **statické** ve funkci zachová svůj stav mezi voláními dané funkce.

```cpp
// static1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void showstat( int curr ) {
   static int nStatic;    // Value of nStatic is retained
                          // between each function call
   nStatic += curr;
   cout << "nStatic is " << nStatic << endl;
}

int main() {
   for ( int i = 0; i < 5; i++ )
      showstat( i );
}
```

```Output
nStatic is 0
nStatic is 1
nStatic is 3
nStatic is 6
nStatic is 10
```

Tento příklad ukazuje použití **statické** ve třídě.

```cpp
// static2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CMyClass {
public:
   static int m_i;
};

int CMyClass::m_i = 0;
CMyClass myObject1;
CMyClass myObject2;

int main() {
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject1.m_i = 1;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject2.m_i = 2;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   CMyClass::m_i = 3;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;
}
```

```Output
0
0
1
1
2
2
3
3
```

Tento příklad ukazuje místní proměnná deklarovaná **statické** v členské funkci. Statická proměnná je k dispozici pro celý program; všechny instance daného typu sdílí stejnou kopii statické proměnné.

```cpp
// static3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
struct C {
   void Test(int value) {
      static int var = 0;
      if (var == value)
         cout << "var == value" << endl;
      else
         cout << "var != value" << endl;

      var = value;
   }
};

int main() {
   C c1;
   C c2;
   c1.Test(100);
   c2.Test(100);
}
```

```Output
var != value
var == value
```

Od verze C ++ 11, statické lokální proměnné inicializace je zaručena bezpečné pro vlákna. Tato funkce se někdy označuje jako *statické objekty magic*. Nicméně ve vícevláknových aplikacích musí být synchronizovány všechny následné úlohy. Statická inicializace bezpečná pro vlákno funkci můžete zakázat s použitím [/Zc: threadsafeinit](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) příznak vyhnete se tak závislosti na CRT.

## <a name="extern"></a> extern

Objekty a proměnné deklarované jako **extern** deklarovat objekt, který je definován v jiné jednotce překladu nebo v ohraničujícím rozsahu, jako kdyby měly vnější propojení.

Deklarace **const** proměnné **extern** třídu úložiště vynutí vnější propojení u proměnné. Inicializace proměnné **extern const** proměnná je povolený v definici jednotky překladu. Inicializace v jednotkách překladu, které jsou jiné než definující jednotka překladu, vytvářejí nedefinované výsledky. Další informace najdete v tématu [používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)

[/Zc: externconstexpr](../build/reference/zc-externconstexpr.md) – možnost kompilátoru způsobí, že kompilátor použije [vnější propojení]() k proměnné deklarované s použitím `extern constexpr`. V dřívějších verzích sady Visual Studio a ve výchozím nastavení nebo pokud **/Zc:externConstexpr-** není zadána, Visual Studio použije vnitřní propojení k **constexpr** i pokud proměnné **extern** klíčové slovo se používá. **/Zc: externconstexpr** možnost je k dispozici od verze Visual Studio 2017 Update 15.6. a je vypnuto ve výchozím nastavení. /Permissive-option/Zc: externconstexpr nepovolí.

Následující kód ukazuje dva **extern** deklarace, `DefinedElsewhere` (odkazuje na název definovaný v jiné jednotce překladu) a `DefinedHere` (odkazuje na název definovaný v ohraničujícím oboru):

```cpp
// external.cpp
// DefinedElsewhere is defined in another translation unit
extern int DefinedElsewhere;
int main() {
   int DefinedHere;
   {
      // refers to DefinedHere in the enclosing scope
      extern int DefinedHere;
   }
}
```

## <a name="thread_local"></a> možnost thread_local (C ++ 11)

Proměnná deklarovaná pomocí `thread_local` specifikátor je přístupný jenom ve vlákně, ke kterému se vytvoří. Proměnná se vytvoří při vlákna je vytvořen a zničen při zničení vlákna. Každé vlákno má svou vlastní kopii proměnné. Na Windows `thread_local` je funkčně srovnatelný s specifické pro Microsoft [__declspec (vlákno)](../cpp/thread.md) atribut.

```cpp
thread_local float f = 42.0; // Global namespace. Not implicitly static.

struct S // cannot be applied to type definition
{
    thread_local int i; // Illegal. The member must be static.
    thread_local static char buf[10]; // OK
};

void DoSomething()
{
    // Apply thread_local to a local variable.
    // Implicitly "thread_local static S my_struct".
    thread_local S my_struct;
}
```

Co je třeba mít na paměti `thread_local` specifikátor:

- Dynamicky inicializovaná místní proměnné vlákna v knihovnách DLL nemusí být správně inicializován na všechna vlákna volání. Další informace najdete v tématu [vlákno](thread.md).

- `thread_local` Lze kombinovat se specifikátorem **statické** nebo **extern**.

- Můžete použít `thread_local` jenom pro deklarace a definice; dat `thread_local` nelze použít v deklaracích nebo definicích funkce.

- Můžete zadat `thread_local` pouze na položky dat s trváním statického úložiště. To zahrnuje globální datové objekty (obojí **statické** a **extern**), místní statické objekty a statické datové členy třídy. Všechny místní proměnná deklarovaná `thread_local` je implicitně statická, není-li zadána žádná jiná třída úložiště; jinými slovy, v oboru bloku `thread_local` je ekvivalentní `thread_local static`.

- Je nutné zadat `thread_local` pro deklarace a definice místního objektu vlákna, zda deklarace a definice objeví ve stejný soubor nebo samostatné soubory.

Na Windows `thread_local` je funkčně srovnatelný s [__declspec(thread)](../cpp/thread.md) s tím rozdílem, že **__declspec(thread)** lze použít s definicí typu a je platný v kódu jazyka C. Kdykoli je to možné, použijte `thread_local` vzhledem k tomu, že je součástí standardu C++ a proto je větší přenositelnost.

##  <a name="register"></a>  Registrace

**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): **zaregistrovat** – klíčové slovo již není podporovanou třídou úložiště. Klíčové slovo je stále vyhrazené ve standardu pro budoucí použití.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Příklad: automatické a statická inicializace

Místní automatický objekt nebo proměnná je inicializována pokaždé, když se tok řízení dosáhne jeho definici. Lokálního statického objektu nebo proměnné je inicializován při prvním tok řízení dosáhne jeho definici.

Podívejte se na následující příklad definuje třídu, která zaznamenává inicializace a zničení objektů a pak definuje tři objekty, `I1`, `I2`, a `I3`:

```cpp
// initialization_of_objects.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>
using namespace std;

// Define a class that logs initializations and destructions.
class InitDemo {
public:
    InitDemo( const char *szWhat );
    ~InitDemo();

private:
    char *szObjName;
    size_t sizeofObjName;
};

// Constructor for class InitDemo
InitDemo::InitDemo( const char *szWhat ) :
    szObjName(NULL), sizeofObjName(0) {
    if ( szWhat != 0 && strlen( szWhat ) > 0 ) {
        // Allocate storage for szObjName, then copy
        // initializer szWhat into szObjName, using
        // secured CRT functions.
        sizeofObjName = strlen( szWhat ) + 1;

        szObjName = new char[ sizeofObjName ];
        strcpy_s( szObjName, sizeofObjName, szWhat );

        cout << "Initializing: " << szObjName << "\n";
    }
    else {
        szObjName = 0;
    }
}

// Destructor for InitDemo
InitDemo::~InitDemo() {
    if( szObjName != 0 ) {
        cout << "Destroying: " << szObjName << "\n";
        delete szObjName;
    }
}

// Enter main function
int main() {
    InitDemo I1( "Auto I1" ); {
        cout << "In block.\n";
        InitDemo I2( "Auto I2" );
        static InitDemo I3( "Static I3" );
    }
    cout << "Exited block.\n";
}
```

```Output
Initializing: Auto I1
In block.
Initializing: Auto I2
Initializing: Static I3
Destroying: Auto I2
Exited block.
Destroying: Auto I1
Destroying: Static I3
```

Tento příklad ukazuje, jak a kdy objekty `I1`, `I2`, a `I3` jsou inicializovány a kdy jsou zničeny.

Existuje několik bodů vědět o program:

- Nejprve je potřeba `I1` a `I2` se automaticky odstraní, když tok řízení opustí blok ve které jsou definovány.

- Za druhé v jazyce C++, není nutné deklarovat objekty a proměnné na začátku bloku. Kromě toho tyto objekty jsou inicializovány pouze v případě, že tok řízení dosáhne jejich definice. (`I2` a `I3` jsou příkladem definicemi takovýchto.) Ukazuje výstup, přesně, když jsou inicializovány.

- Nakonec statické lokální proměnné jako `I3` zachovat jejich hodnoty doby trvání programu, ale jsou zničeny při ukončení programu.

## <a name="see-also"></a>Viz také:

[Deklarace a definice](../cpp/declarations-and-definitions-cpp.md)