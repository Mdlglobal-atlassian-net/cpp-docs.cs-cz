---
title: "Třídy úložiště (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- thread_local_cpp
- external_cpp
- static_cpp
dev_langs: C++
helpviewer_keywords: storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3830f91683399eba4784b5348ca252e9caa22d57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="storage-classes-c"></a>Třídy úložiště (C++)  
  
A *třídy úložiště* v kontextu C++ deklarace proměnných je specifikátor typu, který řídí životnost, propojení a paměti umístění objektů. Předaný objekt může mít pouze jednu třídu úložiště. Proměnné definované v rámci bloku mají automatické úložiště, pokud není uvedeno jinak, pomocí `extern`, `static`, nebo `thread_local` specifikátory. Bez propojení; mít automaticky objektů a proměnné nejsou viditelné pro kód mimo blok.  
  
**Poznámky**  
  
1.  [Měnitelný](../cpp/mutable-data-members-cpp.md) – klíčové slovo lze považovat za specifikátor třídy úložiště. Je však pouze k dispozici v sezamu členů definice třídy.  
  
2.  **Visual C++ 2010 a novější:** `auto` – klíčové slovo již není C++ – specifikátor třídy úložiště a `register` – klíčové slovo je zastaralý. **Visual Studio 2017 verze 15.3 a novější:** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): `register` – klíčové slovo je už třída podporované úložiště. Klíčové slovo je stále vyhrazené ve verzi standard pro budoucí použití. 
```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="in-this-section"></a>V této části:
  
-   [statické](#static)  
-   [extern](#extern)  
-   [thread_local](#thread_local)

<a name="static"></a>
  
## <a name="static"></a>static  
  
`static` – Klíčové slovo lze deklarovat proměnné a funkce v globálním oboru, obor názvů a rozsah třídy. Statické proměnné lze deklarovat také na místní obor.  
  
Statické trvání znamená, že objekt nebo proměnná je přidělená při spuštění programu a je deallocated při ukončení programu. Externí propojení znamená, že je název proměnné viditelné z vnějšku souboru, ve kterém je deklarovaná proměnnou. Vnitřní propojení naopak znamená, že název není viditelné mimo souboru, ve kterém je deklarovaná proměnnou. Ve výchozím nastavení má objektu nebo proměnné, který je definován v oboru názvů globální statické doba trvání a externí propojení. `static` – Klíčové slovo lze použít v následujících situacích.  
  
1.  Když deklarovat proměnné nebo funkce v rozsahu souboru (globální nebo oboru názvů), `static` – klíčové slovo určí, že se proměnné nebo funkce má vnitřní propojení. Když je deklarovat proměnnou, proměnná má statické doba trvání a kompilátor inicializuje ji na 0, pokud neurčíte jinou hodnotu.  
  
2.  Když je deklarovat proměnnou ve funkci, `static` – klíčové slovo určuje, že proměnná zůstane stavu mezi volání této funkce.  
  
3.  Když Deklarujte datového člena v deklaraci třídy `static` – klíčové slovo určuje, že jedna kopie člena, je sdílen všechny instance třídy. Člen statických dat musí být definován v oboru souboru. Integrální datové člena, který je deklarovat jako `const static` může mít inicializátoru.  
  
4.  Když je deklarovat členské funkce v deklaraci třídy `static` – klíčové slovo určuje, že funkce je sdílen všechny instance třídy. Statické členské funkce nemá přístup k instanci členu, protože funkce nemá implicitní `this` ukazatel. Pro přístup k instanci členu, deklarujte funkce se parametr, který je ukazatel instance nebo odkaz.  
  
5.  Nelze deklarovat členů sjednocení jako statické. Ale globálně deklarované anonymní sjednocení musí být explicitně deklarován `static`.  
  
Tento příklad ukazuje, jak deklarovat proměnnou `static` ve funkci zůstane stavu mezi volání této funkce.  
  
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
  
Tento příklad ukazuje použití `static` v třídě.  
  
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
  
Tento příklad ukazuje, místní proměnné deklarovány `static` v členské funkce. Statické proměnné je k dispozici celý programu; všechny instance typu sdílejí stejnou kopii statické proměnné.  
  
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
  
Počínaje C ++ 11, statické místní proměnné inicializace záruku, že se jako bezpečné pro přístup z více vláken. Tato funkce se někdy nazývá *kouzelná statické objekty*. Ale v Vícevláknová aplikace musí být synchronizovány všechny následné přiřazení. Funkce statický inicializace vláken se dá vypnout pomocí [/Zc:threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) příznak vyhnout se závislost na CRT.  
  
<a name="extern"></a>  
  
## <a name="extern"></a>extern  
  
Objekty a proměnné deklarované jako `extern` deklarují objekt, který je definován v jiné jednotce překladu nebo v ohraničujícím rozsahu, jako kdyby měly vnější propojení.  
  
Prohlášení o `const` proměnné s `extern` třídy úložiště vynutí proměnné tak, aby měl externí propojení. Inicializaci `extern const` proměnné je povolena v jednotce definující překlad. Inicializace v jednotkách překladu, které jsou jiné než definující jednotka překladu, vytvářejí nedefinované výsledky. Další informace najdete v tématu [používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)  
  
Následující kód zobrazuje dvě deklarace `extern`, `DefinedElsewhere` (odkazuje na název definovaný v jiné jednotce překladu) a `DefinedHere` (odkazuje na název definovaný v ohraničujícím oboru):  
  
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
  
<a name="thread_local"></a>  
  
## <a name="threadlocal-c11"></a>thread_local (C ++ 11)  
  
Proměnná definovaná s `thread_local` specifikátor je dostupné jenom na vlákno, ve které je vytvořena. Proměnná se vytvoří při vlákno je vytvořen a zničen při vlákno zničena. Každé vlákno má svou vlastní kopii proměnnou. V systému Windows `thread_local` je funkčně srovnatelný Microsoft specifické [__declspec (vlákno)](../cpp/thread.md) atribut.  
  
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
  
Všimněte o `thread_local` specifikátor:  
  
-  `thread_local` Specifikátor mohou být kombinovány s `static` nebo `extern`.  
  
-  Můžete použít `thread_local` pouze na data deklarace a definice; `thread_local` nelze použít na funkce deklarace nebo definice.  
  
-  Použití `thread_local` mohou ovlivňovat [zpoždění načítání](../build/reference/linker-support-for-delay-loaded-dlls.md) knihovny DLL importuje. 
  
-  V systémech XP `thread_local` nemusí fungovat správně, pokud knihovnu DLL používá `thread_local` dat a je načtena dynamicky prostřednictvím `LoadLibrary`.  
  
-  Můžete zadat `thread_local` pouze na datové položky s úložiště se statickými doba trvání. To zahrnuje globální datové objekty (obojí `static` a `extern`), místní statické objekty a členy statických dat tříd. Všechny místní proměnné deklarovány `thread_local` je implicitně statické, pokud je k dispozici žádné další třídy úložiště; jinými slovy, v oboru bloku `thread_local` je ekvivalentní `thread_local static`. 
  
-  Je nutné zadat `thread_local` pro deklaraci a definice objektu místní vlákno, jestli deklarace a definice se provádějí v stejný soubor nebo samostatné soubory.  
  
V systému Windows `thread_local` je funkčně srovnatelný [__declspec(thread)](../cpp/thread.md) s tím rozdílem, že `__declspec(thread)` lze použít pro definici typu a je platný v kódu jazyka C. Pokud je to možné, použijte `thread_local` protože je součástí standardní C++ a je proto obecnější.  
  
##  <a name="register"></a>Registrace  
**Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): `register` – klíčové slovo je už třída podporované úložiště. Klíčové slovo je stále vyhrazené ve verzi standard pro budoucí použití. 

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>Příklad: automatické a statické inicializace  
  
Místní automatické objekt nebo proměnná je inicializován. pokaždé, když se dosáhne jeho definice toku řízení. Místní statický objekt nebo proměnná je inicializován prvním toku řízení dosáhne jeho definice.  
  
Podívejte se na následující příklad, který definuje třídu, která zaznamenává inicializace a odstraňování objektů a pak definuje tři objekty, `I1`, `I2`, a `I3`:  
  
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
  
Tento příklad ukazuje, jak a kdy objekty `I1`, `I2`, a `I3` jsou inicializovány a když jsou zničena.  
  
Existuje několik bodů si informace o programu:  
  
- První, `I1` a `I2` automaticky odstraní při ukončení bloku toku řízení ve které jsou definovány.  
  
- Za druhé v jazyce C++, není potřeba deklarovat objekty nebo proměnné na začátku bloku. Kromě toho tyto objekty jsou inicializovány jenom v případě, že tok řízení dosáhne jejich definice. (`I2` a `I3` jsou příklady takových definice.) Výstup ukazuje přesně při své inicializaci.  
  
- Nakonec statické místní proměnné, jako `I3` zachovat jejich hodnoty pro dobu spuštění programu, ale jsou zničený, protože program se ukončí.  
  
## <a name="see-also"></a>Viz také  
  
 [Deklarace a definice](../cpp/declarations-and-definitions-cpp.md)
