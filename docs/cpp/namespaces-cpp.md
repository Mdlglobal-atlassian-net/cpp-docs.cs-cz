---
title: Obory názvů (C++)
ms.date: 08/30/2017
f1_keywords:
- namespace_CPP
- using_CPP
helpviewer_keywords:
- namespaces [C++]
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
ms.openlocfilehash: ae3006dd1b17ec38240a318af6cfcac5c7d6bf49
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418424"
---
# <a name="namespaces-c"></a>Obory názvů (C++)

Obor názvů je deklarativní oblast, která poskytuje obor k identifikátorům (názvy typů, funkcí, proměnných atd.) uvnitř ní. Obory názvů slouží k uspořádání kódu do logických skupin a k zabránění kolizím názvů, ke kterým může dojít hlavně v případě, že váš základní kód obsahuje více knihoven. Všechny identifikátory v oboru názvů jsou viditelné vedle sebe bez kvalifikace. Identifikátory mimo obor názvů mají přístup ke členům pomocí plně kvalifikovaného názvu pro každý identifikátor, například `std::vector<std::string> vec;`, nebo jinak pomocí [deklarace](../cpp/using-declaration.md) pro jeden identifikátor (`using std::string`) nebo [direktivy using](../cpp/namespaces-cpp.md#using_directives) pro všechny identifikátory v oboru názvů (`using namespace std;`). Kód v hlavičkových souborech by měl vždycky používat plně kvalifikovaný název oboru názvů.

Následující příklad ukazuje deklaraci oboru názvů a tři způsoby, které kód mimo obor názvů má přístup ke svým členům.

```cpp
namespace ContosoData
{
    class ObjectManager
    {
    public:
        void DoSomething() {}
    };
    void Func(ObjectManager) {}
}
```

Použijte plně kvalifikovaný název:

```cpp
ContosoData::ObjectManager mgr;
mgr.DoSomething();
ContosoData::Func(mgr);
```

Použijte deklaraci using k uvedení jednoho identifikátoru do oboru:

```cpp
using ContosoData::ObjectManager;
ObjectManager mgr;
mgr.DoSomething();
```

Použijte direktivu using k uvedení všeho v oboru názvů do rozsahu:

```cpp
using namespace ContosoData;

ObjectManager mgr;
mgr.DoSomething();
Func(mgr);
```

## <a id="using_directives"></a>direktivy using

Direktiva **using** povoluje použití všech názvů v **názvovém prostoru** bez *názvu oboru názvů* jako explicitního kvalifikátoru. Použijte direktivu using v implementačním souboru (například *. cpp), pokud používáte několik různých identifikátorů v oboru názvů; Pokud jste právě používali jeden nebo dva identifikátory, zvažte použití deklarace deklarací, aby se tyto identifikátory přenesly do oboru, a ne do všech identifikátorů v oboru názvů. Pokud má lokální proměnná stejný název jako proměnná oboru názvů, je proměnná oboru názvů skryta. Jedná se o chybu, pokud má proměnná oboru názvů stejný název jako globální proměnná.

> [!NOTE]
>  Direktiva using se dá umístit na začátek souboru. cpp (v rozsahu souboru) nebo uvnitř definice třídy nebo funkce.
>
>  Obecně platí, že Nezahrnovat direktivy using v hlavičkových souborech (*. h), protože každý soubor, který obsahuje tuto hlavičku, přenese vše v oboru názvů do oboru, což může způsobit skrývání názvů a problémy kolize názvů, které jsou velmi obtížné ladit. V hlavičkovém souboru vždy používejte plně kvalifikované názvy. Pokud se tyto názvy dostanou příliš dlouho, můžete k jejich zkrácení použít alias oboru názvů. (Viz níže)

## <a name="declaring-namespaces-and-namespace-members"></a>Deklarace oborů názvů a členů oboru názvů

Obvykle deklarujete obor názvů v hlavičkovém souboru. Pokud jsou vaše implementace funkcí v samostatném souboru, pak kvalifikováním názvů funkcí, jako v tomto příkladu.

```cpp
//contosoData.h
#pragma once
namespace ContosoDataServer
{
    void Foo();
    int Bar();
}
```

Implementace funkcí v contosodata. cpp by měly používat plně kvalifikovaný název, i když do horní části souboru umístíte direktivu **using** :

```cpp
#include "contosodata.h"
using namespace ContosoDataServer;

void ContosoDataServer::Foo() // use fully-qualified name here
{
   // no qualification needed for Bar()
   Bar();
}

int ContosoDataServer::Bar(){return 0;}
```

Obor názvů lze deklarovat ve více blocích v jednom souboru a ve více souborech. Kompilátor spojuje části společně během předběžného zpracování a výsledný obor názvů obsahuje všechny členy deklarované ve všech částech. Příkladem je standardní obor názvů, který je deklarován v každém hlavičkovém souboru ve standardní knihovně.

Členy pojmenovaného oboru názvů lze definovat mimo obor názvů, v němž jsou deklarovány, pomocí explicitní kvalifikace definovaného názvu. Definice se však musí objevit za bodem deklarace v oboru názvů, který je ohraničující obor názvů deklarace. Příklad:

```cpp
// defining_namespace_members.cpp
// C2039 expected
namespace V {
    void f();
}

void V::f() { }        // ok
void V::g() { }        // C2039, g() is not yet a member of V

namespace V {
    void g();
}
```

K této chybě může dojít, pokud jsou členy oboru názvů deklarovány napříč více hlavičkových souborů a nezahrnuli jste tyto hlavičky ve správném pořadí.

## <a name="the-global-namespace"></a>Globální obor názvů

Pokud identifikátor není deklarován v explicitním oboru názvů, je součástí implicitního globálního oboru názvů. Obecně se snažte vyhnout vytváření deklarací v globálním rozsahu, pokud je to možné, s výjimkou [hlavní funkce](../c-language/main-function-and-program-execution.md)vstupního bodu, která musí být v globálním oboru názvů. K explicitnímu zařazení globálního identifikátoru použijte operátor rozlišení oboru bez názvu, jak je uvedeno v `::SomeFunction(x);`. Tím se identifikátor odlišuje od cokoli se stejným názvem v jakémkoli jiném oboru názvů, a pomůže vám to usnadnit pochopení kódu ostatním.

## <a name="the-std-namespace"></a>Obor názvů std

Všechny C++ standardní typy a funkce knihovny jsou deklarovány v oboru názvů `std` nebo obory názvů vnořené v rámci `std`.

## <a name="nested-namespaces"></a>Vnořené obory názvů

Obory názvů můžou být vnořené. Běžný vnořený obor názvů má neoprávněný přístup ke svým nadřazeným členům, ale nadřazené členy nemají neúplný přístup k vnořenému oboru názvů (Pokud není deklarován jako inline), jak je znázorněno v následujícím příkladu:

```cpp
namespace ContosoDataServer
{
    void Foo();

    namespace Details
    {
        int CountImpl;
        void Ban() { return Foo(); }
    }

    int Bar(){...};
    int Baz(int i) { return Details::CountImpl; }
}
```

Běžné vnořené obory názvů lze použít k zapouzdření podrobností interní implementace, které nejsou součástí veřejného rozhraní nadřazeného oboru názvů.

## <a name="inline-namespaces-c-11"></a>Vložené oboryC++ názvů (11)

Na rozdíl od obyčejného vnořeného oboru názvů se členové vloženého oboru názvů považují za členy nadřazeného oboru názvů. Tato vlastnost umožňuje vyhledávání závislých na argumentu u přetížených funkcí pro práci s funkcemi, které mají přetížení nadřazeného a vnořeného oboru názvů. Umožňuje také deklarovat specializaci v nadřazeném oboru názvů pro šablonu, která je deklarována v rámci vloženého oboru názvů. Následující příklad ukazuje, jak se externí kód váže k vloženému oboru názvů standardně:

```cpp
//Header.h
#include <string>

namespace Test
{
    namespace old_ns
    {
        std::string Func() { return std::string("Hello from old"); }
    }

    inline namespace new_ns
    {
        std::string Func() { return std::string("Hello from new"); }
    }
}

#include "header.h"
#include <string>
#include <iostream>

int main()
{
    using namespace Test;
    using namespace std;

    string s = Func();
    std::cout << s << std::endl; // "Hello from new"
    return 0;
}
```

Následující příklad ukazuje, jak lze deklarovat specializaci v nadřazené šabloně šablony, která je deklarována v rámci vloženého oboru názvů:

```cpp
namespace Parent
{
    inline namespace new_ns
    {
         template <typename T>
         struct C
         {
             T member;
         };
    }
     template<>
     class C<int> {};
}
```

Můžete použít vložené obory názvů jako mechanismus správy verzí ke správě změn ve veřejném rozhraní knihovny. Můžete například vytvořit jeden nadřazený obor názvů a zapouzdřit každou verzi rozhraní ve vlastním oboru názvů vnořeném do nadřazeného objektu. Obor názvů, který obsahuje nejnovější nebo upřednostňovanou verzi, je kvalifikován jako inline a je proto vystaven, jako by byl přímým členem nadřazeného oboru názvů. Kód klienta, který vyvolá nadřazenou třídu::, bude automaticky svázán s novým kódem. Klienti, kteří preferují použití starší verze, k němu stále mají přístup pomocí plně kvalifikované cesty k vnořenému oboru názvů, který má tento kód.

Klíčové slovo inline se musí použít na první deklaraci oboru názvů v kompilační jednotce.

Následující příklad ukazuje dvě verze rozhraní, každý ve vnořeném oboru názvů. `v_20` obor názvů obsahuje nějaké úpravy z rozhraní `v_10` a je označený jako inline. Klientský kód, který používá novou knihovnu a volání `Contoso::Funcs::Add`, vyvolá v_20 verzi. Kód, který se pokouší volat `Contoso::Funcs::Divide`, teď získá chybu při kompilaci. Pokud tyto funkce skutečně potřebují, můžou stále přistupovat k `v_10` verzi tím, že explicitně zavolá `Contoso::v_10::Funcs::Divide`.

```cpp
namespace Contoso
{
    namespace v_10
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            T Divide(T a, T b);
        };
    }

    inline namespace v_20
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            std::vector<double> Log(double);
            T Accumulate(std::vector<T> nums);
      };
    }
}
```

## <a id="namespace_aliases"></a>Aliasy oboru názvů

Názvy názvových prostorů musí být jedinečné, což znamená, že by obvykle neměly být příliš krátké. Pokud je délka názvu obtížná pro čtení kódu nebo je únavné zadat v hlavičkovém souboru, kde nelze použít direktivy using, pak můžete vytvořit alias oboru názvů, který slouží jako zkratka pro skutečný název. Příklad:

```cpp
namespace a_very_long_namespace_name { class Foo {}; }
namespace AVLNN = a_very_long_namespace_name;
void Bar(AVLNN::Foo foo){ }
```

## <a name="anonymous-or-unnamed-namespaces"></a>anonymní nebo nepojmenované obory názvů

Můžete vytvořit explicitní obor názvů, ale nemusíte mu dát název:

```cpp
namespace
{
    int MyFunc(){}
}
```

Tento postup se nazývá nepojmenovaný nebo anonymní obor názvů a je užitečný, pokud chcete, aby deklarace proměnných byly neviditelné pro kód v jiných souborech (tj. přidávají interní propojení) bez nutnosti vytvořit pojmenovaný obor názvů. Veškerý kód ve stejném souboru může zobrazit identifikátory v nenázvovém oboru názvů, ale identifikátory spolu s samotným oborem názvů nejsou viditelné vně tohoto souboru – nebo přesněji mimo jednotku překladu.

## <a name="see-also"></a>Viz také

[Deklarace a definice](declarations-and-definitions-cpp.md)
