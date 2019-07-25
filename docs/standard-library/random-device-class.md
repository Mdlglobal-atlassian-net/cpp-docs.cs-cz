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
ms.openlocfilehash: 184513bc63975bd8eaaf0e53300e5a6be7986389
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448539"
---
# <a name="randomdevice-class"></a>random_device – třída

Vygeneruje náhodnou posloupnost z externího zařízení.

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

Třída popisuje zdroj náhodných čísel a je povolená, ale není nutná k nedeterministickému nebo kryptografickému zabezpečení standardem ISO C++ . V implementaci sady Visual Studio jsou vytvářené hodnoty nedeterministické a kryptograficky zabezpečené, ale jsou pomalejší než generátory vytvořené z modulů a adaptérů motorů (například [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md), vysoká kvalita a rychlé. zvolený modul pro většinu aplikací.

`random_device`výsledky jsou rovnoměrně rozloženy v uzavřeném rozsahu [ `0, 2` <sup>32</sup>].

`random_device`není zaručeno mít za následek neblokující volání.

`random_device` Obecně se používá k osazení dalších generátorů vytvořených pomocí motorů nebo adaptérů motorů. Další informace najdete v tématu [ \<náhodné >](../standard-library/random.md).

## <a name="example"></a>Příklad

Následující kód ukazuje základní funkce této třídy a příklady výsledků. Z důvodu nedeterministické povahy `random_device`, náhodné hodnoty uvedené v oddílu **Output** nebudou odpovídat vašim výsledkům. To je normální a očekává se.

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

Tento příklad je zjednodušený a není zástupcem obecného případu použití pro tento generátor. Další reprezentativní příklad kódu naleznete v tématu [ \<Random >](../standard-library/random.md).

## <a name="requirements"></a>Požadavky

**Hlavička:** \<náhodné >

**Obor názvů:** std

## <a name="random_device"></a>random_device::random_device

Sestaví generátor.

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Poznámky

Konstruktor inicializuje generátor podle potřeby a ignoruje parametr řetězce. Vyvolá hodnotu uživatelsky definovaného typu odvozeného z [výjimky](../standard-library/exception-class.md) , `random_device` Pokud nelze inicializovat.

## <a name="entropy"></a>random_device:: entropie

Odhadne náhodnost zdroje.

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odhad náhodnosti zdroje, jak je měřeno v bitech.

## <a name="op_call"></a>random_device:: operator () – operátor ()

Vrací náhodnou hodnotu.

```cpp
result_type operator()();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnoty rovnoměrně distribuované v uzavřeném intervalu [ `min, max`] podle určení členských funkcí `min()` a `max()`. Vyvolá hodnotu typu definovaného implementací odvozenou od [výjimky](../standard-library/exception-class.md) , pokud nelze získat náhodné číslo.

## <a name="see-also"></a>Viz také:

[\<náhodné >](../standard-library/random.md)
