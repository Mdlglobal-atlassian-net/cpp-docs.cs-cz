---
title: Soubory hlaviček (C++)
ms.date: 04/20/2018
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: ea163f4d47022d886e40a09c47c252ffa186aee0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588809"
---
# <a name="header-files-c"></a>Soubory hlaviček (C++)

Před použitím musí být deklarované názvy prvků programu, jako jsou proměnné, funkce, třídy a tak dále. Například je nelze zapsat `x = 42` bez první deklarace "x".

```cpp
int x; // declaration
x = 42; // use x
```

Deklarace instruuje kompilátor, zda je **int**, **double**, **funkce**, **třída** nebo některé další věc, kterou.  Kromě toho musí být každý název deklarován (přímo nebo nepřímo) v každém souboru .cpp, ve kterém se používá. Při kompilaci programu, každý soubor .cpp nezávisle na sobě zkompilován kompilační jednotky. Kompilátor nezná názvy, které jsou deklarovány v jiných jednotkách kompilace. To znamená, pokud definujete třídu nebo funkci nebo globální proměnné, je nutné zadat deklaraci celou věc nepropojili v každém souboru Další .cpp, která ji používá. Každou deklaraci celou věc nepropojili musí být přesně shodovat ve všech souborech. Mírné nekonzistence způsobí chyby nebo nežádoucí chování, když se pokusí linkeru sloučit do jedné programu kompilačních jednotek.

Chcete-li minimalizovat potenciální chyby C++ přijala konvence použití *hlavičkové soubory* obsahující deklarace. Ujistěte se, deklarace v hlavičkovém souboru a pak použít #include – direktiva v každém souboru .cpp nebo jiný soubor záhlaví vyžaduje tuto deklaraci. #Include kopii souboru hlaviček direktiv vloží přímo do souboru .cpp před kompilací.

## <a name="example"></a>Příklad

Následující příklad ukazuje běžný způsob, jak deklarovat třídu a používat ho v odlišném zdrojovém souboru. Začneme s souboru hlaviček `my_class.h`. Obsahuje definice třídy, ale mějte na paměti, že definice je neúplný; Členská funkce `do_something` není definován:

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

Dále vytvořte soubor implementace (obvykle s .cpp nebo podobné rozšíření). Vytvoříme volání my_class.cpp soubor a poskytnout definici pro deklarace člena. Přidáme `#include` směrnice pro soubor "my_class.h" aby bylo možné mít deklaraci my_class vložen v tuto chvíli ve .cpp soubor a patří `<iostream>` aby se načetla deklarace `std::cout`. Všimněte si, že uvozovky se používají pro hlavičkové soubory ve stejném adresáři jako zdrojový soubor a ostré závorky se používají pro záhlaví standardní knihovny. Navíc mnoho hlavičky standardní knihovny nemají .h nebo jiných příponu souboru.

V souboru implementace jsme můžete volitelně použít **pomocí** příkaz, aby se nemusela kvalifikovat každý zmínka o "my_class" nebo "cout" s "N::" nebo "std::".  Neumisťujte **pomocí** příkazy v záhlaví souborů!

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

Teď můžeme použít `my_class` do jiného souboru .cpp. Jsme #include hlavičku souboru tak, aby kompilátor si vyžádá deklarace. Všechny musí kompilátor vědět, je tento my_class je třída, která má veřejný člen funkci s názvem `do_something()`.

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

Po dokončení sestavování každý soubor .cpp do souborů obj kompilátor předá linkeru soubory .obj. Když linker sloučení souborů objektů najde přesně jednu definici my_class; je v souboru .obj vytvořeného pro my_class.cpp a sestavení úspěšné.

## <a name="include-guards"></a>Zahrnout ochrany

Obvykle, třeba soubory hlaviček *zahrnují guard* nebo `#pragma once` směrnice a ujistěte se, že není více než jednou vložili do souboru s příponou .cpp jeden.

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

## <a name="what-to-put-in-a-header-file"></a>Co se má vložit do hlavičky souboru

Protože soubor hlaviček může můžou být zahrnuté více soubory, nesmí obsahovat definice, které mohou vytvořit několik definic se stejným názvem. Následující nejsou povolené, nebo jsou považovány za velmi špatný postup:

- předdefinovaný typ definice v oboru názvů nebo globálního rozsahu
- definice jiných než vložených funkcí
- Definice proměnných nekonstantní
- agregační definice
- nepojmenované obory názvů
- direktivy using

Použití **pomocí** nutně nezpůsobí chybu, ale může potenciálně způsobit potíže, protože obor názvů přináší do rozsahu v každém souboru .cpp, který přímo nebo nepřímo obsahuje tuto hlavičku.

## <a name="sample-header-file"></a>Ukázkový soubor záhlaví

Následující příklad ukazuje různé druhy deklarace a definice, které jsou povoleny v hlavičkovém souboru:

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