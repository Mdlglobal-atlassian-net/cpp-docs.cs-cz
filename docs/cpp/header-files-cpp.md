---
title: Soubory hlaviček (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- header files [C++]
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b571cd2836e66ebef21898af27cf2a6d7082e0e5
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238754"
---
# <a name="header-files-c"></a>Soubory hlaviček (C++)

Před použitím musí být deklarován názvy elementů programu, například proměnné, funkce, třídy a tak dále. Například nelze právě zapisovat `x = 42` bez první deklarace "x". 

```cpp
int x; // declaration
x = 42; // use x
```

 Deklaraci říká kompilátoru, jestli je **int**, **dvojité**, **funkce**, **třídy** nebo některých jiných věcí.  Kromě toho musí být deklarován každý název (přímo ani nepřímo) v každém sada souboru, ve kterém se používá. Při kompilaci program každého souboru nezávisle zkompilován jednotku kompilace. Kompilátor nemá žádné informace o názvy, které jsou deklarované v jiných kompilačních jednotek. To znamená, pokud definujete třídu nebo funkce nebo – globální proměnná, je nutné zadat deklaraci této věc do každého souboru další sada, která jej používá. Každá deklarace této věc musí být ve všech souborů přesně shodovat. Mírné nekonzistence způsobí chyby nebo nežádoucí chování, když se pokusí sloučit všechny kompilace jednotky do jednoho programu linkeru.

Chcete-li minimalizovat potenciální chyby, C++ přijal konvence pomocí *soubory hlaviček* tak, aby obsahovala deklarace. Proveďte deklarací v záhlaví souboru, potom použijte #include – direktiva v každém sada souboru nebo jiné hlavičkový soubor vyžaduje tuto deklaraci. #Include kopii soubor hlaviček direktivy vloží přímo do souboru před kompilace. 

## <a name="example"></a>Příklad

Následující příklad ukazuje běžný způsob deklarování třídy a použít ho v různých zdrojového souboru. Začneme s soubor hlaviček **my_class.h**. Obsahuje definice třídy, ale Všimněte si, že definice neúplné; Členská funkce `do_something` není definován:

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

Dále vytvořte soubor implementace (obvykle s sada nebo podobné rozšíření). Jsme budete volat my_class.cpp souboru a zadejte definici deklarace členů. Přidáme `#include` direktivy pro soubor "my_class.h", aby bylo možné používat deklarace my_class vložit v tomto okamžiku v sada souborů a My zahrnují  **\<iostream >** stáhnout deklaraci pro `std::cout`. Upozorňujeme, že uvozovky se používají pro soubory hlaviček ve stejném adresáři jako zdrojový soubor a lomené závorky se používají pro standardní knihovna hlavičky. Navíc mnoho hlavičky standardní knihovna nemají .h nebo jiných příponu souboru.

V souboru implementace jsme můžete volitelně použít **pomocí** příkaz, abyste nemuseli pro kvalifikaci každých zmínky "my_class" nebo "cout" s "N::" nebo "– std::".  Umístěte **pomocí** příkazy v vaše soubory hlaviček!

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

Teď můžete používáme `my_class` v jiném souboru sada. Jsme #include soubor hlaviček, tak, aby kompilátor vrátí v deklaraci. Všechny potřeby kompilátoru vědět, je, že my_class je třída, která má funkci veřejné člen s názvem `do_something()`.

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

Po dokončení kompilace každého souboru do soubory .obj kompilátor předává soubory .obj linkeru. Když linkeru sloučí soubory objektů najde přesně jednu definici pro my_class; je v souboru .obj vrácená pro my_class.cpp a sestavení úspěšné.

## <a name="include-guards"></a>Zahrnout ochranná zařízení

Obvykle mají soubory hlaviček *zahrnují ochrana* nebo **#pragma jednou** – direktiva zajistit, že nejsou vložen vícekrát do jednoho sada souboru. 

my_class.h
#<a name="ifndef-myclassh--include-guard"></a>ifndef – MY_CLASS_H / / include ochrana
#<a name="define-myclassh"></a>definování MY_CLASS_H


obor názvů N {třídy my_class {veřejné: void do_something();};

}

#<a name="endif--myclassh-"></a>endif / * MY_CLASS_H * /

## <a name="what-to-put-in-a-header-file"></a>Co chcete umístit do soubor hlaviček

Protože soubor hlaviček může potenciálně zahrnuta ve více souborů, nemůže obsahovat definice, které může být několik definic se stejným názvem. Následující nejsou povolené, nebo jsou považovány za velmi chybný postup:

- předdefinovaný typ definice v oboru názvů nebo globální obor
- definice bez vložené funkce 
- definice proměnné bez const
- agregační definice
- nepojmenované obory názvů
- Pomocí direktiv

Použití **pomocí** – direktiva nebude nutně způsobit chybu, ale může potenciálně způsobit problém, protože přináší oboru názvů do oboru v každé sada soubor, který přímo nebo nepřímo zahrnuje této hlavičky. 

## <a name="sample-header-file"></a>Ukázkový soubor hlaviček

Následující příklad ukazuje různé druhy deklarace a definice, které jsou povoleny v záhlaví souboru:

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
