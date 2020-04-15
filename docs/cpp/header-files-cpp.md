---
title: Soubory hlaviček (C++)
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 4ab6a2b2626cde94f35678bc9ec789b80d493b8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367234"
---
# <a name="header-files-c"></a>Soubory hlaviček (C++)

Názvy prvků programu, jako jsou proměnné, funkce, třídy a tak dále, musí být deklarovány před jejich použitím. Například nemůžete jen psát, `x = 42` aniž byste nejprve deklarovali 'x'.

```cpp
int x; // declaration
x = 42; // use x
```

Deklarace říká kompilátoru, zda je prvek **int**, **double**, **funkce**, **třída** nebo nějaká jiná věc.  Kromě toho musí být každý název deklarován (přímo nebo nepřímo) v každém souboru CPP, ve kterém se používá. Při kompilaci programu je každý soubor CPP kompilován nezávisle do jednotky kompilace. Kompilátor nemá žádné znalosti o tom, jaké názvy jsou deklarovány v jiných jednotkách kompilace. To znamená, že pokud definujete třídu nebo funkci nebo globální proměnnou, musíte zadat deklaraci této věci v každém dalším souboru CPP, který ji používá. Každé prohlášení o té věci musí být přesně totožné ve všech souborech. Mírná nekonzistence způsobí chyby nebo neúmyslné chování, když se propojovací program pokusí sloučit všechny jednotky kompilace do jednoho programu.

Chcete-li minimalizovat potenciál pro chyby, C++ přijala konvence pomocí *soubory hlaviček* obsahovat deklarace. Provedete deklarace v souboru záhlaví a potom použijete direktivu #include v každém souboru CPP nebo jiném souboru záhlaví, který vyžaduje tuto deklaraci. Direktiva #include vloží kopii souboru záhlaví přímo do souboru CPP před kompilací.

> [!NOTE]
> V sadě Visual Studio 2019 je funkce *modulů* C++ 20 zavedena jako vylepšení a případná náhrada za soubory hlaviček. Další informace naleznete [v tématu Přehled modulů v jazyce C++](modules-cpp.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje běžný způsob deklarování třídy a potom ji použít v jiném zdrojovém souboru. Začneme se souborem záhlaví, `my_class.h`. Obsahuje definici třídy, ale všimněte si, že definice je neúplná; členská `do_something` funkce není definována:

```cpp
// my_class.h
namespace N
{
    class my_class
    {
    public:
        void do_something();
    };

}
```

Dále vytvořte implementační soubor (obvykle s příponou CPP nebo podobnou příponou). Zavoláme soubor my_class.cpp a poskytneme definici deklarace člena. Přidáme `#include` direktivu pro soubor "my_class.h", aby byla v tomto okamžiku vložena `<iostream>` deklarace my_class do `std::cout`souboru CPP, a zahrneme ji v ytažením v deklaraci pro . Všimněte si, že uvozovky se používají pro soubory hlaviček ve stejném adresáři jako zdrojový soubor a úhlové závorky se používají pro standardní záhlaví knihovny. Mnoho standardních záhlaví knihovny také nemá příponu H ani jinou příponu.

V souboru implementace můžeme volitelně použít **using** prohlášení, aby chomáč každý zmínka o "my_class" nebo "cout" s "N::" nebo "std::".  Nevkládat **pomocí** příkazů v záhlaví souborů!

```cpp
// my_class.cpp
#include "my_class.h" // header in local directory
#include <iostream> // header in standard library

using namespace N;
using namespace std;

void my_class::do_something()
{
    cout << "Doing something!" << endl;
}
```

Nyní můžeme `my_class` použít v jiném souboru .cpp. #include soubor hlavičky tak, aby kompilátor natáhne v deklaraci. Všechny kompilátor potřebuje vědět, je, že my_class je `do_something()`třída, která má veřejné členské funkce s názvem .

```cpp
// my_program.cpp
#include "my_class.h"

using namespace N;

int main()
{
    my_class mc;
    mc.do_something();
    return 0;
}
```

Po dokončení kompilace každého souboru CPP do souborů OBJ předá soubory OBJ propojovacímu systému. Když propojovací systém sloučí soubory objektů, najde přesně jednu definici pro my_class; je v souboru OBJ vyrobeném pro soubor my_class.cpp a sestavení je úspěšné.

## <a name="include-guards"></a>Zahrnout stráže

Soubory hlaviček mají obvykle zahrnout `#pragma once` *stráž* nebo směrnice, aby bylo zajištěno, že nejsou vloženy vícekrát do jednoho souboru CPP.

```cpp
// my_class.h
#ifndef MY_CLASS_H // include guard
#define MY_CLASS_H

namespace N
{
    class my_class
    {
    public:
        void do_something();
    };
}

#endif /* MY_CLASS_H */
```

## <a name="what-to-put-in-a-header-file"></a>Co vložit do souboru záhlaví

Vzhledem k tomu, že soubor záhlaví může být potenciálně zahrnut do více souborů, nemůže obsahovat definice, které mohou vytvářet více definic se stejným názvem. Následující nejsou povoleny nebo jsou považovány za velmi špatné praxe:

- vestavěné definice typů v oboru názvů nebo globálním oboru
- definice neinline funkcí
- definice proměnných, které nejsou const
- souhrnné definice
- nepojmenované obory názvů
- používání směrnic

Použití **using** směrnice nemusí nutně způsobit chybu, ale může potenciálně způsobit problém, protože přináší obor názvů do oboru v každém souboru CPP, který přímo nebo nepřímo obsahuje toto záhlaví.

## <a name="sample-header-file"></a>Ukázkový soubor záhlaví

Následující příklad ukazuje různé druhy deklarací a definic, které jsou povoleny v souboru záhlaví:

```cpp
// sample.h
#pragma once
#include <vector> // #include directive
#include <string>

namespace N  // namespace declaration
{
    inline namespace P
    {
        //...
    }

    enum class colors : short { red, blue, purple, azure };

    const double PI = 3.14;  // const and constexpr definitions
    constexpr int MeaningOfLife{ 42 };
    constexpr int get_meaning()
    {
        static_assert(MeaningOfLife == 42, "unexpected!"); // static_assert
        return MeaningOfLife;
    }
    using vstr = std::vector<int>;  // type alias
    extern double d; // extern variable

#define LOG   // macro definition

#ifdef LOG   // conditional compilation directive
    void print_to_log();
#endif

    class my_class   // regular class definition,
    {                // but no non-inline function definitions

        friend class other_class;
    public:
        void do_something();   // definition in my_class.cpp
        inline void put_value(int i) { vals.push_back(i); } // inline OK

    private:
        vstr vals;
        int i;
    };

    struct RGB
    {
        short r{ 0 };  // member initialization
        short g{ 0 };
        short b{ 0 };
    };

    template <typename T>  // template definition
    class value_store
    {
    public:
        value_store<T>() = default;
        void write_value(T val)
        {
            //... function definition OK in template
        }
    private:
        std::vector<T> vals;
    };

    template <typename T>  // template declaration
    class value_widget;
}
```
