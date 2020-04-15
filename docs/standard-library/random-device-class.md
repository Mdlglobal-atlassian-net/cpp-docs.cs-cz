---
title: random_device – třída
ms.date: 11/04/2016
f1_keywords:
- random/std::random_device
- random/std::random_device::min
- random/std::random_device::max
- random/std::random_device::entropy
- random/std::random_device::operator()
helpviewer_keywords:
- std::random_device [C++]
- std::random_device [C++], min
- std::random_device [C++], max
- std::random_device [C++], entropy
- std::random_device [C++], entropy
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
ms.openlocfilehash: 396f172d6a7f9fed72e19917a528f561d0110470
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320274"
---
# <a name="random_device-class"></a>random_device – třída

Generuje náhodnou sekvenci z externího zařízení.

## <a name="syntax"></a>Syntaxe

```cpp
class random_device {
public:
   typedef unsigned int result_type;

   // constructor
   explicit random_device(const std::string& token = "");

   // properties
   static result_type min();
   static result_type max();
   double entropy() const;

   // generate
   result_type operator()();

   // no-copy functions
   random_device(const random_device&) = delete;
   void operator=(const random_device&) = delete;
   };
```

## <a name="members"></a>Členové

|||
|-|-|
|[random_device](#random_device)|[entropy](#entropy)|
|[random_device::operátor()](#op_call)||

## <a name="remarks"></a>Poznámky

Třída popisuje zdroj náhodných čísel a je povolena, ale nemusí být nedeterministická nebo kryptograficky zabezpečená standardem ISO C++. V implementaci sady Visual Studio jsou vytvořené hodnoty nedeterministické a kryptograficky zabezpečené, ale běží pomaleji než generátory vytvořené z motorů a adaptérů motoru (například [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md), vysoce kvalitní a rychlý modul volby pro většinu aplikací).

`random_device`výsledky jsou rovnoměrně rozloženy v `0, 2`uzavřeném rozmezí [ <sup>32</sup>).

`random_device`není zaručeno, že výsledkem je neblokující volání.

Obecně `random_device` platí, že se používá k osivu jiných generátorů vytvořených s motory nebo adaptéry motoru. Další informace naleznete [ \< ](../standard-library/random.md)v tématu random>.

## <a name="example"></a>Příklad

Následující kód ukazuje základní funkce této třídy a příklad výsledků. Z důvodu nedeterministické povahy `random_device`aplikace nebudou náhodné hodnoty zobrazené v části **Výstup** odpovídat výsledkům. To je normální a očekávané.

```cpp
// random_device_engine.cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <random>
#include <iostream>
using namespace std;

int main()
{
    random_device gen;

    cout << "entropy == " << gen.entropy() << endl;
    cout << "min == " << gen.min() << endl;
    cout << "max == " << gen.max() << endl;

    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
}
```

```Output
entropy == 32
min == 0
max == 4294967295
a random value == 2378414971
a random value == 3633694716
a random value == 213725214
```

Tento příklad je zjednodušující a není reprezentativní pro obecné případ použití pro tento generátor. Reprezentativnější příklad kódu naleznete [ \<v tématu random>](../standard-library/random.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné>

**Obor názvů:** std

## <a name="random_devicerandom_device"></a><a name="random_device"></a>random_device::random_device

Konstruuje generátor.

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Poznámky

Konstruktor inicializuje generátor podle potřeby a ignoruje parametr řetězce. Vyvolá hodnotu typu definovaného implementací odvozený `random_device` z [výjimky,](../standard-library/exception-class.md) pokud nelze inicializovat.

## <a name="random_deviceentropy"></a><a name="entropy"></a>random_device::entropie

Odhaduje náhodnost zdroje.

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odhad náhodnosti zdroje měřeného v bitech.

## <a name="random_deviceoperator"></a><a name="op_call"></a>random_device::operátor()

Vrátí náhodnou hodnotu.

```cpp
result_type operator()();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnoty rovnoměrně rozložené v `min, max`uzavřeném intervalu `min()` `max()`[ ] určené majestátně a . Vyvolá hodnotu typu definovaného implementací odvozenou z [výjimky,](../standard-library/exception-class.md) pokud nebylo možné získat náhodné číslo.

## <a name="see-also"></a>Viz také

[\<náhodné>](../standard-library/random.md)
