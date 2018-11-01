---
title: Inicializace tříd a struktur bez konstruktorů (C++)
ms.date: 10/17/2018
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 4f696f4fc8862b953e40a03c96b88d1a0b7f720b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547326"
---
# <a name="initializing-classes-and-structs-without-constructors-c"></a>Inicializace tříd a struktur bez konstruktorů (C++)

Není vždy nutné definovat konstruktor pro třídu, zejména těch, které je poměrně jednoduchá. Uživatelé můžou inicializace objektů třídy nebo struktury pomocí jednotnou inicializaci, jak je znázorněno v následujícím příkladu:

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

Všimněte si, že při třídě nebo struktuře nemá žádný konstruktor, zadáte seznam prvky v pořadí, členů jsou deklarovány ve třídě. Pokud třída nemá konstruktor, poskytují prvky v pořadí parametrů.

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Konstruktory](../cpp/constructors-cpp.md)
