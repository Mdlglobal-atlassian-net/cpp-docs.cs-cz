---
title: Hlavičkové souboryC++()
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: ca5036ee53372f44e53b5a6452d4ab220fc3977d
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301480"
---
# <a name="header-files-c"></a>Hlavičkové souboryC++()

Názvy prvků programu, jako jsou proměnné, funkce, třídy a tak dále, musí být deklarovány dříve, než mohou být použity. Například nemůžete napsat `x = 42` bez první deklarace ' x '.

```cpp
int x; // declaration
x = 42; // use x
```

Deklarace instruuje kompilátor, zda je prvek typu **int**, **Double**, **funkce**, **třídy** nebo jiné věci.  Kromě toho musí být každý název deklarován (přímo nebo nepřímo) v každém souboru. cpp, ve kterém je použit. Při kompilaci programu je každý soubor. cpp zkompilován nezávisle na kompilační jednotce. Kompilátor nemá žádné znalosti o tom, jaké názvy jsou deklarovány v jiných jednotkách kompilace. To znamená, že pokud definujete třídu nebo funkci nebo globální proměnnou, je nutné zadat deklaraci této věci v každém dalším souboru. cpp, který ji používá. Každá deklarace této věci musí být přesně shodná se všemi soubory. Lehká nekonzistence způsobí chyby nebo nezamýšlené chování, když se linker pokusí sloučit všechny kompilační jednotky do jednoho programu.

Pro minimalizaci potenciálu chyb C++ přijala konvenci použití *hlavičkových souborů* k zahrnutí deklarací. Deklarace provedete v hlavičkovém souboru a pak použijete direktivu #include v každém souboru. cpp nebo jiném hlavičkovém souboru, který vyžaduje tuto deklaraci. Direktiva #include vloží kopii hlavičkového souboru přímo do souboru. cpp před kompilací.

> [!NOTE]
> V aplikaci Visual Studio 2019 se funkce C++ 20 *modulů* zavedla jako vylepšení a při konečném nahrazení hlavičkových souborů. Další informace najdete v tématu [Přehled modulů v C++ ](modules-cpp.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje běžný způsob, jak deklarovat třídu a pak ji použít v jiném zdrojovém souboru. Začneme souborem hlaviček, `my_class.h`. Obsahuje definici třídy, ale Všimněte si, že definice není kompletní; `do_something` členské funkce nejsou definovány:

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

Dále vytvořte implementační soubor (obvykle s příponou. cpp nebo podobným rozšířením). Zavoláme soubor my_class. cpp a poskytneme definici deklarace členů. Přidáme direktivu `#include` pro soubor my_class. h, aby se v tomto okamžiku v souboru. cpp vložila deklarace my_class. do této chvíle patří i `<iostream>`, které by bylo možné načíst do deklarace pro `std::cout`. Všimněte si, že se používají uvozovky pro hlavičkové soubory ve stejném adresáři jako zdrojový soubor a lomené závorky se používají pro hlavičky standardních knihoven. Mnoho hlaviček standardních knihoven navíc nemá příponu. h ani jinou příponu souboru.

V implementačním souboru můžeme volitelně použít příkaz **using** , abyste se vyhnuli nutnosti kvalifikovat každou zmínku "my_class" nebo "cout" s "N::" nebo "std::".  Nevkládejte příkazy **using** do souborů hlaviček!

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

Nyní můžeme použít `my_class` v jiném souboru. cpp. #Include hlavičkového souboru, takže kompilátor vyžádá v deklaraci. Všechny kompilátory musí znát, že my_class je třída, která má veřejnou členskou funkci nazvanou `do_something()`.

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

Poté, co kompilátor dokončí kompilaci každého souboru. cpp do souborů. obj, předá do linkeru soubory. obj. Když linker sloučí soubory objektů, najde přesně jednu definici pro my_class; je v souboru. obj vytvořeném pro my_class. cpp a sestavení je úspěšné.

## <a name="include-guards"></a>Zahrnutí Guard

Soubory hlaviček mají obvykle direktivu *include Guard* nebo `#pragma once`, aby bylo zajištěno, že nejsou vloženy vícekrát do jednoho souboru. cpp.

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

## <a name="what-to-put-in-a-header-file"></a>Co umístit do hlavičkového souboru

Vzhledem k tomu, že hlavičkový soubor může být potenciálně zahrnutý více soubory, nemůže obsahovat definice, které by mohly vytvořit více definic se stejným názvem. Následující nejsou povoleny, nebo se považují za velmi špatný postup:

- předdefinované definice typu v oboru názvů nebo globálním oboru
- Definice funkcí, které nejsou vložené
- Definice proměnných, které nejsou const
- agregované definice
- nepojmenované obory názvů
- direktivy using

Použití direktivy **using** nebude nutně způsobovat chybu, ale může potenciálně způsobit problém, protože obor názvů přiřadí do oboru v každém souboru. cpp, který je přímo nebo nepřímo obsahuje tuto hlavičku.

## <a name="sample-header-file"></a>Ukázkový hlavičkový soubor

Následující příklad ukazuje různé druhy deklarací a definic, které jsou povoleny v hlavičkovém souboru:

```cpp
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
