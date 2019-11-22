---
title: Životnost objektů a Správa prostředků (RAII)
description: Postupujte podle principu RAII v moderním C++ , abyste se vyhnuli nevracení prostředků.
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
ms.openlocfilehash: 01867ec0a71ba54bb6534da1b408cb0610d652a7
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303369"
---
# <a name="object-lifetime-and-resource-management-raii"></a>Životnost objektů a Správa prostředků (RAII)

Na rozdíl od spravovaných C++ jazyků nemá automatické *uvolňování paměti*. To je interní proces, který uvolní paměť haldy a další prostředky při spuštění programu. C++ Program zodpovídá za vrácení všech pořízených prostředků do operačního systému. Selhání uvolnění nepoužívaného prostředku se nazývá *netěsnost*. Nevrácené prostředky nejsou k dispozici ostatním programům, dokud se proces neukončí. Konkrétně nevracení paměti je běžné příčinou chyb v programování ve stylu C.

Moderní C++ Vyhněte se použití paměti haldy co nejvíc tím, že deklarujete objekty v zásobníku. Pokud je prostředek pro zásobník příliš velký, měl by být *vlastněn* objektem. Jakmile se objekt inicializuje, získá prostředek, který vlastní. Objekt je pak zodpovědný za uvolnění prostředku ve svém destruktoru. Vlastnící objekt je deklarován v zásobníku. Princip, kdy jsou *objekty vlastní prostředky* , se také označují jako "získávání prostředků je inicializace" nebo RAII.

Když se objekt zásobníku vlastnícího prostředky dostane mimo rozsah, jeho destruktor se automaticky vyvolá. Tímto způsobem uvolňování paměti v C++ nástroji úzce souvisí s životností objektu a je deterministické. Prostředek je vždy vydán ve známém bodě v programu, který lze ovládat. Pouze deterministické destruktory, jako jsou C++ v, mohou zpracovávat prostředky paměti a nepaměťových prostředků stejně.

Následující příklad ukazuje jednoduchý objekt `w`. Je deklarována v zásobníku v oboru funkce a je zničena na konci bloku funkce. Objekt `w` nevlastní žádné *prostředky* (například paměť přidělené haldě). Jeho jediný členský `g` je sám o sobě deklarovaný v zásobníku a jednoduše se předává mimo rozsah spolu s `w`. V destruktoru `widget` není vyžadován žádný speciální kód.

```cpp
class widget {
private:
    gadget g;   // lifetime automatically tied to enclosing object
public:
    void draw();
};

void functionUsingWidget () {
    widget w;   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.g gadget member
    // ...
    w.draw();
    // ...
} // automatic destruction and deallocation for w and w.g
  // automatic exception safety,
  // as if "finally { w.dispose(); w.g.dispose(); }"
```

V následujícím příkladu `w` vlastní prostředek paměti, takže aby bylo možné paměť odstranit, musí mít ve svém destruktoru kód.
 
```cpp
class widget
{
private:
    int* data;
public:
    widget(const int size) { data = new int[size]; } // acquire
    ~widget() { delete[] data; } // release
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                        // constructs w, including the w.data member
    w.do_something();

} // automatic destruction and deallocation for w and w.data

```

Od verze C++ 11 existuje lepší způsob, jak napsat předchozí příklad: pomocí inteligentního ukazatele ze standardní knihovny. Inteligentní ukazatel zpracovává přidělování a odstraňování paměti, kterou vlastní. Použití inteligentního ukazatele eliminuje nutnost explicitního destruktoru ve třídě `widget`.

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

Pomocí inteligentních ukazatelů pro přidělení paměti můžete eliminovat potenciál nevracení paměti. Tento model funguje pro jiné prostředky, jako jsou popisovače souborů nebo sokety. Můžete spravovat vlastní prostředky podobným způsobem ve svých třídách. Další informace najdete v tématu [inteligentní ukazatele](smart-pointers-modern-cpp.md).

Návrh C++ zajistí, že objekty budou zničeny, když dostanou mimo rozsah. To znamená, že jsou zničeny při ukončení bloků, v opačném pořadí konstrukce. Když je objekt zničen, jeho základy a členy jsou zničeny v určitém pořadí. Objekty deklarované mimo libovolný blok v globálním rozsahu mohou vést k problémům. Může být obtížné ladit, pokud konstruktor globálního objektu vyvolá výjimku.

## <a name="see-also"></a>Viz také:

[Vítejte zpět naC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
