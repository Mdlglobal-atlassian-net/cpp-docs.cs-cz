---
title: Třídy úložiště (C++)
description: V jazyce C++ určují klíčová slova statické, extern a thread_local životnost, propojení a umístění paměti proměnné nebo funkce.
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: 75ccb11689b4863d2d0df5edd6d066be6bd3858c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365349"
---
# <a name="storage-classes"></a>Třídy úložiště

*Třída úložiště* v kontextu deklarací proměnných jazyka C++ je specifikátor typu, který řídí životnost, propojení a umístění paměti objektů. Předaný objekt může mít pouze jednu třídu úložiště. Proměnné definované v bloku mají automatické ukládání, pokud není určeno jinak pomocí **specifikátorů extern**, **static**nebo **thread_local.** Automatické objekty a proměnné nemají žádné propojení; nejsou viditelné pro kód mimo blok. Paměť je přidělena pro ně automaticky při provádění zadá blok a de-přidělena při ukončení bloku.

**Poznámky**

1. [Proměnlivé](../cpp/mutable-data-members-cpp.md) klíčové slovo může být považováno za specifikátor třídy úložiště. Je však pouze k dispozici v sezamu členů definice třídy.

1. **Visual Studio 2010 a novější:** Klíčové slovo **auto** již není specifikátorem třídy úložiště jazyka C++ a klíčové slovo **register** je zastaralé. **Visual Studio 2017 verze 15.7 a novější:** (k dispozici s [/std:c++17):](../build/reference/std-specify-language-standard-version.md)Klíčové slovo **register** je odebráno z jazyka C++.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a><a name="static"></a>Statické

**Statické** klíčové slovo lze deklarovat proměnné a funkce v globálním oboru, oboru oboru názvů a oboru třídy. Statické proměnné lze také deklarovat v místním oboru.

Statická doba trvání znamená, že objekt nebo proměnná je přidělena při spuštění programu a je při ukončení programu přidělena. Externí propojení znamená, že název proměnné je viditelný z mimo soubor, ve kterém je proměnná deklarována. Naopak vnitřní propojení znamená, že název není viditelný mimo soubor, ve kterém je proměnná deklarována. Ve výchozím nastavení má objekt nebo proměnná definovaná v globálním oboru názvů statickou dobu trvání a externí propojení. **Statické** klíčové slovo lze použít v následujících situacích.

1. Když deklarujete proměnnou nebo funkci v oboru souboru (globální a/nebo obor oboru oboru názvů), **statické** klíčové slovo určuje, že proměnná nebo funkce má vnitřní propojení. Když deklarujete proměnnou, proměnná má statickou dobu trvání a kompilátor ji inicializuje na 0, pokud nezadáte jinou hodnotu.

1. Když deklarujete proměnnou ve funkci, **statické** klíčové slovo určuje, že proměnná si zachová svůj stav mezi voláními této funkce.

1. Když deklarujete datový člen v deklaraci třídy, **statické** klíčové slovo určuje, že jedna kopie člena je sdílena všemi instancemi třídy. Statický datový člen musí být definován v oboru souborů. Integrální datový člen, který deklarujete jako **const static,** může mít inicializátor.

1. Když deklarujete členskou funkci v deklaraci třídy, **statické** klíčové slovo určuje, že funkce je sdílena všemi instancemi třídy. Statická členská funkce nemůže získat přístup k členu instance, protože funkce nemá implicitní **tento** ukazatel. Chcete-li získat přístup k členu instance, deklarujte funkci s parametrem, který je ukazatelem instance nebo odkazem.

1. Členy unie nelze deklarovat jako statické. Globálně deklarované anonymní unie však musí být explicitně deklarována **statické**.

Tento příklad ukazuje, jak proměnná deklarovaná **statická** ve funkci zachovává svůj stav mezi voláními této funkce.

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

Tento příklad ukazuje místní proměnnou deklarovanou **statickou** v členské funkci. Statická proměnná je k dispozici pro celý program; všechny instance typu sdílejí stejnou kopii statické proměnné.

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

Počínaje C++ 11 je zaručeno, že inicializace statické lokální proměnné je bezpečná pro přístup z více vláken. Tato funkce se někdy nazývá *magická statika*. V aplikaci s více vlákny však musí být synchronizována všechna následující přiřazení. Funkce statické inicializace bezpečná pro přístup z více vláken může být zakázána pomocí příznaku [/Zc:threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) aby se zabránilo závislosti na CRT.

## <a name="extern"></a><a name="extern"></a>Externí

Objekty a proměnné deklarované jako **extern** deklarují objekt, který je definován v jiné jednotce překladu nebo v ohraničujícím oboru jako objekt s externím propojením. Další informace naleznete v [odděleních](program-and-linkage-cpp.md) [extern](extern-cpp.md) a Translation a propojení .

## <a name="thread_local-c11"></a><a name="thread_local"></a>thread_local (C++11)

Proměnná deklarovaná s **specifikátorem thread_local** je přístupná pouze ve vlákně, ve kterém je vytvořena. Proměnná je vytvořena při vytvoření vlákna a zničena při zničení vlákna. Každé vlákno má svou vlastní kopii proměnné. V systému Windows **je thread_local** funkčně ekvivalentní atributu [__declspec specifické](../cpp/thread.md) pro společnost Microsoft.

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

Co je třeba poznamenat, o **specifikátoru thread_local:**

- Dynamicky inicializované proměnné místního vlákna v knihovnách DLL nemusí být správně inicializovány ve všech volajících vláknech. Další informace naleznete [v tématu thread](thread.md).

- Specifikátor **thread_local** lze kombinovat se **statickým** nebo **extern**.

- **Thread_local** můžete použít pouze na deklarace dat a definice; **thread_local** nelze použít na deklaracích funkcí nebo definicích.

- Můžete zadat **thread_local** pouze u datových položek s dobou trvání statického úložiště. To zahrnuje globální datové objekty **(statické** i **extern),** místní statické objekty a statické datové členy tříd. Všechny místní proměnné deklarované **thread_local** je implicitně statické, pokud není k dispozici žádná jiná třída úložiště; jinými slovy, v **thread_local** rozsahu bloku `thread_local static`thread_local je ekvivalentní .

- Je nutné zadat **thread_local** pro deklaraci i definici místního objektu vlákna, zda se deklarace a definice vyskytují ve stejném souboru nebo samostatných souborech.

V systému Windows **je thread_local** funkčně ekvivalentní [__declspec(vlákno)](../cpp/thread.md) s tím rozdílem, že **__declspec(vlákno)** lze použít pro definici typu a je platný v kódu C. Kdykoli je to možné, použijte **thread_local** protože je součástí standardu C++, a proto je přenosnější.

## <a name="register"></a><a name="register"></a>Registrace

**Visual Studio 2017 verze 15.3 a novější** (k dispozici s [/std:c++17):](../build/reference/std-specify-language-standard-version.md)Klíčové slovo **register** již není podporovanou třídou úložiště. Klíčové slovo je stále vyhrazeno ve standardu pro budoucí použití.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Příklad: automatická vs. statická inicializace

Místní automatický objekt nebo proměnná je inicializována pokaždé, když tok řízení dosáhne své definice. Místní statický objekt nebo proměnná je inicializována při prvním toku řízení dosáhne jeho definice.

Vezměme si následující příklad, který definuje třídu, která zaznamenává inicializaci `I2`a `I3`zničení objektů a pak definuje tři objekty, `I1`, a :

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

Tento příklad ukazuje, jak `I1`a `I2`kdy `I3` jsou objekty , a jsou inicializovány a kdy jsou zničeny.

Existuje několik bodů na vědomí, o programu:

- Za `I1` prvé `I2` a jsou automaticky zničeny, když tok řízení ukončí blok, ve kterém jsou definovány.

- Za druhé v jazyce C++ není nutné deklarovat objekty nebo proměnné na začátku bloku. Kromě toho tyto objekty jsou inicializovány pouze v případě, že tok řízení dosáhne jejich definice. (`I2` `I3` a jsou příklady těchto definic.) Výstup přesně ukazuje, kdy jsou inicializovány.

- Nakonec statické místní proměnné, `I3` jako je například zachovat jejich hodnoty po dobu trvání programu, ale jsou zničeny jako program ukončí.

## <a name="see-also"></a>Viz také

[Prohlášení a definice](../cpp/declarations-and-definitions-cpp.md)
