---
title: Obory názvů (C++)
ms.date: 08/30/2017
f1_keywords:
- namespace_CPP
- using_CPP
helpviewer_keywords:
- namespaces [C++]
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
ms.openlocfilehash: 4957ec5a5face860d2e39861eddc8f7e5abe9370
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367915"
---
# <a name="namespaces-c"></a>Obory názvů (C++)

Obor názvů je deklarativní oblast, která poskytuje rozsah identifikátorů (názvy typů, funkcí, proměnných atd.) uvnitř. Obory názvů se používají k uspořádání kódu do logických skupin a k zabránění kolizím názvů, ke kterým může dojít zejména v případě, že základ kódu obsahuje více knihoven. Všechny identifikátory v oboru názvů jsou viditelné navzájem bez kvalifikace. Identifikátory mimo obor názvů mohou přistupovat k členům pomocí plně `std::vector<std::string> vec;`kvalifikovaného názvu pro každý identifikátor,`using std::string`například pomocí [deklarace](../cpp/using-declaration.md) pro jeden identifikátor`using namespace std;`( ) nebo pomocí [směrnice](../cpp/namespaces-cpp.md#using_directives) pro všechny identifikátory v oboru názvů ( ). Kód v souborech hlaviček by měl vždy používat plně kvalifikovaný název oboru názvů.

Následující příklad ukazuje deklaraci oboru názvů a tři způsoby, které kód mimo obor názvů může přistupovat ke svým členům.

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

Pomocí deklarace using přenesete jeden identifikátor do oboru:

```cpp
using ContosoData::ObjectManager;
ObjectManager mgr;
mgr.DoSomething();
```

Pomocí direktivy using můžete přenést vše v oboru názvů do oboru:

```cpp
using namespace ContosoData;

ObjectManager mgr;
mgr.DoSomething();
Func(mgr);
```

## <a name="using-directives"></a><a id="using_directives"></a>používání směrnic

Direktiva **using** umožňuje použití všech názvů v **oboru názvů** bez *názvu oboru názvů* jako explicitníkvalikvalifikace. Pokud v oboru názvů používáte direktivu using v souboru implementace (tj. *.cpp), použijte v oboru názvů několik různých identifikátorů. Pokud používáte pouze jeden nebo dva identifikátory, zvažte using declaration pouze přenést tyto identifikátory do oboru a ne všechny identifikátory v oboru názvů. Pokud má lokální proměnná stejný název jako proměnná oboru názvů, je proměnná oboru názvů skryta. Jedná se o chybu, pokud má proměnná oboru názvů stejný název jako globální proměnná.

> [!NOTE]
> Direktiva using může být umístěna v horní části souboru CPP (v oboru souboru) nebo uvnitř definice třídy nebo funkce.
>
> Obecně se vyhněte vkládání direktiv do souborů hlaviček (*.h), protože jakýkoli soubor, který obsahuje tuto hlavičku, přenese vše v oboru názvů do oboru, což může způsobit skrytí názvů a problémy s kolizí názvů, které je velmi obtížné ladit. V souboru záhlaví vždy používejte plně kvalifikované názvy. Pokud se tyto názvy příliš dlouho, můžete použít alias oboru názvů k jejich zkrácení. (Viz níže.)

## <a name="declaring-namespaces-and-namespace-members"></a>Deklarování oborů názvů a členů oboru názvů

Obvykle deklarujete obor názvů v souboru záhlaví. Pokud jsou implementace vaší funkce v samostatném souboru, zakvali názvy funkcí, jako v tomto příkladu.

```cpp
//contosoData.h
#pragma once
namespace ContosoDataServer
{
    void Foo();
    int Bar();
}
```

Implementace funkcí v souboru contosodata.cpp by měly používat plně kvalifikovaný název, i když umístíte **direktivu using** v horní části souboru:

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

Obor názvů lze deklarovat ve více blocích v jednom souboru a ve více souborech. Kompilátor spojuje součásti společně během předběžného zpracování a výsledný obor názvů obsahuje všechny členy deklarované ve všech částech. Příkladem je obor názvů STD, který je deklarován v každém ze souborů hlaviček ve standardní knihovně.

Členy pojmenovaného oboru názvů lze definovat mimo obor názvů, ve kterém jsou deklarovány explicitní kvalifikací definovaného názvu. Definice se však musí objevit za bodem deklarace v oboru názvů, který obklopuje obor názvů deklarace. Příklad:

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

K této chybě může dojít, pokud jsou členové oboru názvů deklarováni ve více souborech hlaviček a tyto hlavičky jste nezahrnuli ve správném pořadí.

## <a name="the-global-namespace"></a>Globální obor názvů

Pokud identifikátor není deklarován v explicitní obor názvů, je součástí implicitní globální obor názvů. Obecně se snažte vyhnout vytváření deklarací v globálním oboru, pokud je to možné, s výjimkou [hlavní funkce](../c-language/main-function-and-program-execution.md)vstupního bodu , která musí být v globálním oboru názvů. Chcete-li explicitně kvalifikovat globální identifikátor, použijte operátor `::SomeFunction(x);`rozlišení oboru bez názvu, jako v . Tím se odliší identifikátor od cokoli se stejným názvem v jiném oboru názvů a také pomůže usnadnit váš kód pro ostatní pochopit.

## <a name="the-std-namespace"></a>Obor názvů std

Všechny typy a funkce standardní knihovny `std` jazyka C++ jsou `std`deklarovány v oboru názvů nebo oborech názvů vnořených uvnitř .

## <a name="nested-namespaces"></a>Vnořené obory názvů

Obory názvů mohou být vnořené. Běžný vnořený obor názvů má neúplný přístup k členům nadřazených členů, ale nadřazené členy nemají neomezený přístup k vnořenému oboru názvů (pokud není deklarován jako vložký), jak je znázorněno v následujícím příkladu:

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

Běžné vnořené obory názvů lze použít k zapouzdření podrobnosti vnitřní implementace, které nejsou součástí veřejného rozhraní nadřazeného oboru názvů.

## <a name="inline-namespaces-c-11"></a>Inline obory názvů (C++ 11)

Na rozdíl od běžného vnořeného oboru názvů jsou členové oboru názvů v řádku považováni za členy nadřazeného oboru názvů. Tato charakteristika umožňuje vyhledávání závislých argumentů na přetížených funkcích pracovat na funkcích, které mají přetížení v nadřazeném a vnořeném oboru názvů v řádku. Umožňuje také deklarovat specializaci v nadřazeném oboru názvů pro šablonu, která je deklarována v oboru názvů v řádku. Následující příklad ukazuje, jak se externí kód ve výchozím nastavení váže k oboru názvů v řádku:

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

Následující příklad ukazuje, jak můžete deklarovat specializaci v nadřazené šabloně, která je deklarována v oboru názvů v řádku:

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

Obory názvů v řádku můžete použít jako mechanismus správy verzí ke správě změn veřejného rozhraní knihovny. Můžete například vytvořit jeden nadřazený obor názvů a zapouzdřit každou verzi rozhraní do vlastního oboru názvů vnořeného uvnitř nadřazeného oboru. Obor názvů, který obsahuje nejnovější nebo upřednostňovanou verzi, je kvalifikován jako vřadný a je proto vystaven, jako by byl přímým členem nadřazeného oboru názvů. Klientský kód, který vyvolá Parent::Class se automaticky váže na nový kód. Klienti, kteří dávají přednost použití starší verze stále přístup pomocí plně kvalifikovanou cestu do vnořeného oboru názvů, který má tento kód.

Klíčové slovo válčné musí být použito pro první deklaraci oboru názvů v jednotce kompilace.

Následující příklad ukazuje dvě verze rozhraní, každá v vnořené oboru názvů. Obor `v_20` názvů má některé `v_10` změny z rozhraní a je označen jako vřadit. Klientský kód, který používá `Contoso::Funcs::Add` novou knihovnu a volání vyvolá v_20 verzi. Kód, který se `Contoso::Funcs::Divide` pokusí o volání nyní dostane chybu času kompilace. Pokud tuto funkci skutečně potřebují, mohou `v_10` stále přistupovat k verzi explicitním voláním `Contoso::v_10::Funcs::Divide`.

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

## <a name="namespace-aliases"></a><a id="namespace_aliases"></a>Aliasy oboru názvů

Názvy oborů názvů musí být jedinečné, což znamená, že často by neměly být příliš krátké. Pokud délka názvu ztěžuje čtení kódu nebo je zdlouhavé zadávat do souboru záhlaví, kde nelze použít direktivy pomocí direktiv, můžete vytvořit alias oboru názvů, který slouží jako zkratka pro skutečný název. Příklad:

```cpp
namespace a_very_long_namespace_name { class Foo {}; }
namespace AVLNN = a_very_long_namespace_name;
void Bar(AVLNN::Foo foo){ }
```

## <a name="anonymous-or-unnamed-namespaces"></a>anonymní nebo nepojmenované obory názvů

Můžete vytvořit explicitní obor názvů, ale nepojmenovat jej:

```cpp
namespace
{
    int MyFunc(){}
}
```

To se nazývá nepojmenovaný nebo anonymní obor názvů a je užitečné, pokud chcete, aby deklarace proměnných byly neviditelné pro kód v jiných souborech (tj. dát jim vnitřní propojení), aniž byste museli vytvořit pojmenovaný obor názvů. Veškerý kód ve stejném souboru může zobrazit identifikátory v nepojmenovaném oboru názvů, ale identifikátory spolu se samotným oborem názvů nejsou viditelné mimo tento soubor – nebo přesněji mimo jednotku překladu.

## <a name="see-also"></a>Viz také

[Prohlášení a definice](declarations-and-definitions-cpp.md)
