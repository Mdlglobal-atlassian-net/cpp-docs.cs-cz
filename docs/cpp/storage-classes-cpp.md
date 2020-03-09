---
title: Třídy úložiště (C++)
description: V C++nástroji, klíčová slova static, extern a thread_local určují dobu života, propojení a umístění paměti proměnné nebo funkce.
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- extern_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: ab00a5c64a32dc1dab5fef4bc15b722587bc2d6b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856895"
---
# <a name="storage-classes"></a>Třídy úložiště

*Třída úložiště* v kontextu deklarací C++ proměnných je specifikátor typu, který určuje životnost, propojení a umístění paměti objektů. Předaný objekt může mít pouze jednu třídu úložiště. Proměnné definované v rámci bloku mají automatické úložiště, pokud není určeno jinak pomocí specifikátorů **extern**, **static**nebo **thread_local** . Automatické objekty a proměnné nemají žádné propojení. nejsou viditelné pro kód mimo blok. K automatickému přidělování paměti dojde, když spuštění vstoupí do bloku a zruší přidělení při ukončení bloku.

**Poznámky**

1. Klíčové slovo [mutable](../cpp/mutable-data-members-cpp.md) může být považováno za specifikátor třídy úložiště. Je však pouze k dispozici v sezamu členů definice třídy.

1. **Visual Studio 2010 a novější:** Klíčové slovo **auto** již není specifikátorem C++ třídy úložiště a klíčové slovo **Register** je zastaralé. **Visual Studio 2017 verze 15,7 a novější:** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): klíčové slovo **Register** je odebráno z C++ jazyka.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a>tras

Klíčové slovo **static** lze použít k deklarování proměnných a funkcí v globálním oboru, oboru názvů a oboru třídy. Statické proměnné lze také deklarovat v místním oboru.

Statická doba trvání znamená, že objekt nebo proměnná je přidělena při spuštění programu a je uvolněna při ukončení programu. Externí propojení znamená, že název proměnné je viditelný mimo soubor, ve kterém je proměnná deklarována. V opačném případě interní propojení znamená, že název není viditelný vně souboru, ve kterém je proměnná deklarována. Ve výchozím nastavení má objekt nebo proměnná, která je definována v globálním oboru názvů, statickou dobu trvání a vnější propojení. Klíčové slovo **static** lze použít v následujících situacích.

1. Pokud deklarujete proměnnou nebo funkci v rozsahu souboru (globální nebo obor názvů oboru názvů), klíčové slovo **static** určuje, že proměnná nebo funkce má vnitřní propojení. Pokud deklarujete proměnnou, má proměnná statickou dobu trvání a kompilátor ji inicializuje na hodnotu 0, pokud nezadáte jinou hodnotu.

1. Pokud deklarujete proměnnou ve funkci, klíčové slovo **static** určuje, že proměnná zachovává svůj stav mezi voláními této funkce.

1. Pokud deklarujete datový člen v deklaraci třídy, klíčové slovo **static** určuje, že jedna kopie člena je sdílena všemi instancemi třídy. Statický datový člen musí být definován v rozsahu souboru. Celočíselný datový člen, který deklarujete jako **const static** , může mít inicializátor.

1. Pokud deklarujete členskou funkci v deklaraci třídy, klíčové slovo **static** určuje, že funkce je sdílena všemi instancemi třídy. Statická členská funkce nemůže získat přístup k členu instance, protože funkce nemá implicitní **Tento** ukazatel. Chcete-li získat přístup k členu instance, Deklarujte funkci s parametrem, který je ukazatelem instance nebo odkazem.

1. Členy sjednocení nelze deklarovat jako statické. Globálně deklarovaný anonymní sjednocení se však musí explicitně deklarovat jako **static**.

Tento příklad ukazuje, jak proměnná, která je deklarována jako **statická** ve funkci, zachovává svůj stav mezi voláními této funkce.

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

Tento příklad ukazuje místní proměnnou deklarovanou jako **static** v členské funkci. Statická proměnná je k dispozici pro celý program. všechny instance typu sdílejí stejnou kopii statické proměnné.

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

Počínaje verzí C++ 11 je statická místní proměnná inicializaci zaručena jako bezpečná pro přístup z více vláken. Tato funkce se někdy nazývá *Magic static*. V aplikaci s více vlákny je však nutné synchronizovat všechna další přiřazení. Statickou inicializační funkci bezpečnou pro přístup z více vláken lze zakázat pomocí příznaku [/Zc: threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) Flag, aby nedošlo k závislosti na CRT.

## <a name="extern"></a>extern

Objekty a proměnné deklarované jako **extern** deklarují objekt, který je definován v jiné jednotce překladu nebo v nadřazeném oboru jako s vnějším propojením. Další informace naleznete v tématu [externí](extern-cpp.md) a [jednotky překladu a propojení](program-and-linkage-cpp.md).

## <a name="thread_local"></a>thread_local (C++ 11)

Proměnná deklarovaná pomocí specifikátoru **thread_local** je přístupná pouze ve vlákně, ve kterém je vytvořena. Proměnná je vytvořena při vytvoření vlákna a zničena při zničení vlákna. Každé vlákno má svou vlastní kopii proměnné. V systému Windows je **thread_local** funkčně ekvivalentní s atributem __declspec specifickým pro Microsoft [(vlákno)](../cpp/thread.md) .

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

Co je třeba si uvědomit o specifikátoru **thread_local** :

- Dynamicky inicializované proměnné místního vlákna v knihovnách DLL nemusí být správně inicializovány na všech volajících vláknech. Další informace naleznete v tématu [thread](thread.md).

- Specifikátor **thread_local** může být kombinován se **statickým** nebo **externým**.

- **Thread_local** můžete použít jenom pro deklarace a definice dat; **thread_local** nelze použít pro deklarace funkce nebo definice.

- Můžete zadat **thread_local** jenom pro datové položky s trváním statického úložiště. To zahrnuje globální datové objekty ( **static** i **extern**), místní statické objekty a statické datové členy tříd. Jakákoli místní Proměnná deklarovaná **thread_local** je implicitně statická, pokud není k dispozici žádná jiná třída úložiště. Jinými slovy, v rozsahu bloku **thread_local** je ekvivalentem `thread_local static`.

- Je nutné zadat **thread_local** pro deklaraci a definici objektu Thread Local, zda se deklarace a definice vyskytují ve stejném souboru nebo v samostatných souborech.

Ve Windows je **thread_local** funkčně ekvivalentní [__declspec (vlákno)](../cpp/thread.md) s tím rozdílem, že **__declspec (vlákno)** lze použít pro definici typu a je platný v kódu jazyka C. Kdykoli je to možné, použijte **thread_local** , protože je součástí C++ standardu a je proto lépe přenosná.

##  <a name="register"></a>Registrace

**Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): klíčové slovo **Register** již není podporovanou třídou úložiště. Klíčové slovo je stále rezervované ve standardu pro budoucí použití.

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Příklad: automatické vs. Statická inicializace

Místní automatický objekt nebo proměnná se inicializuje pokaždé, když tok řízení dosáhne své definice. Místní statický objekt nebo proměnná se inicializuje při prvním průchodu toku řízení s jeho definicí.

Vezměte v úvahu následující příklad, který definuje třídu, která zaznamená inicializaci a zničení objektů a poté definuje tři objekty, `I1`, `I2`a `I3`:

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

Tento příklad ukazuje, jak a kdy objekty `I1`, `I2`a `I3` jsou inicializovány a kdy jsou zničeny.

K programu je třeba si uvědomit několik bodů:

- První `I1` a `I2` jsou automaticky zničeny, když tok řízení ukončí blok, ve kterém jsou definovány.

- Za druhé, C++v není nutné deklarovat objekty nebo proměnné na začátku bloku. Kromě toho jsou tyto objekty inicializovány pouze v případě, že tok řízení dosáhne jejich definice. (příklady takových definic jsou`I2` a `I3`.) Výstup se zobrazí přesně při inicializaci.

- Nakonec statické lokální proměnné, například `I3` uchovávají jejich hodnoty po dobu trvání programu, ale jsou zničeny při ukončení programu.

## <a name="see-also"></a>Viz také

[Deklarace a definice](../cpp/declarations-and-definitions-cpp.md)