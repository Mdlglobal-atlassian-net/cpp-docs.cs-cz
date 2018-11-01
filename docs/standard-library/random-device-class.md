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
ms.openlocfilehash: 783b8f587094c6d603cc02f41b516ebd7b1e9a08
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580645"
---
# <a name="randomdevice-class"></a>random_device – třída

Generuje náhodné pořadí z externího zařízení.

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
|[random_device](#random_device)|[entropie](#entropy)|
|[random_device::operator()](#op_call)||

## <a name="remarks"></a>Poznámky

Třída popisuje zdroj náhodných čísel a je povoleno ale není třeba, aby nedeterministické a kryptograficky zabezpečené podle standardu ISO C++. V sadě Visual Studio implementaci hodnoty vytvořené jsou nedeterministické a kryptograficky zabezpečené, ale pracuje pomaleji než generátorů vytvořené z modulů a adaptéry stroj (například [mersenne_twister_engine –](../standard-library/mersenne-twister-engine-class.md), vysoce kvalitní a rychlé enginu podle výběru pro většinu aplikací).

`random_device` výsledky jsou rovnoměrně rozloženy v uzavřeném intervalu [ `0, 2` <sup>32</sup>).

`random_device` není zaručeno, že za následek neblokující volání.

Obecně platí `random_device` se používá pro jiné generátorů vytvořené pomocí modulů nebo modul adaptéry. Další informace najdete v tématu [ \<náhodné >](../standard-library/random.md).

## <a name="example"></a>Příklad

Následující kód ukazuje základní funkce této třídy a Příkladové výsledky. Vzhledem k Nedeterministický povaze `random_device`, náhodné hodnoty zobrazené v **výstup** části nebudou odpovídat výsledkům. To je normální a očekávané.

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

V tomto příkladu je zjednodušenou a ne shodovat s obecné případ použití pro tento generátor. Více reprezentativní příklad kódu naleznete v tématu [ \<náhodné >](../standard-library/random.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodné >

**Namespace:** std

## <a name="random_device"></a>  random_device::random_device

Vytvoří generátor kódu.

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Poznámky

Konstruktor inicializuje generátor podle potřeby a ignoruje parametr řetězce. Vyvolá hodnotu odvozen od typu definované implementací [výjimka](../standard-library/exception-class.md) Pokud `random_device` se nepovedlo inicializovat.

## <a name="entropy"></a>  random_device::entropy

Odhady náhodnosti zdroje.

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odhadu náhodnosti zdroje měřený v bitech.

## <a name="op_call"></a>  random_device::Operator()

Vrací náhodnou hodnota.

```cpp
result_type operator()();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnoty, které jsou rovnoměrně rozloženy v uzavřeném intervalu [ `min, max`] podle členské funkce `min()` a `max()`. Vyvolá hodnotu odvozen od typu definované implementací [výjimka](../standard-library/exception-class.md) Pokud nebylo možné získat náhodné číslo.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)<br/>
