---
title: random_device – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- random/std::random_device
- random/std::random_device::min
- random/std::random_device::max
- random/std::random_device::entropy
- random/std::random_device::operator()
dev_langs:
- C++
helpviewer_keywords:
- std::random_device [C++]
- std::random_device [C++], min
- std::random_device [C++], max
- std::random_device [C++], entropy
- std::random_device [C++], entropy
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cfd0f33d3191f2524df8dc106fb99e80beede7ec
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="randomdevice-class"></a>random_device – třída

Generuje náhodné pořadí z externí zařízení.

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
|[random_device](#random_device)|[šifrování](#entropy)|
|[random_device::operator()](#op_call)||

## <a name="remarks"></a>Poznámky

Třída popisuje zdroj náhodných čísel a je povolená ale nevyžaduje Nedeterministický nebo kryptograficky zabezpečené pomocí standardní C++ ISO. V sadě Visual Studio implementace hodnoty vytvořeného jsou nedeterministické a kryptograficky zabezpečená, ale pracuje pomaleji než generátory vytvořené z motorů a modul adaptéry (například [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md), vysoké kvality a rychlé modul výběru pro většinu aplikací).

`random_device` výsledky jsou rovnoměrně rozložen v rozsahu uzavřené [ `0, 2` <sup>32</sup>).

`random_device` není zaručeno, aby výsledkem volání neblokující.

Obecně platí `random_device` slouží k další generátory vytvořen s moduly nebo modul adaptéry počáteční hodnoty. Další informace najdete v tématu [ \<náhodných >](../standard-library/random.md).

## <a name="example"></a>Příklad

Následující kód ukazuje základní funkce této třídy a příklad výsledků. Z důvodu Nedeterministický povaha `random_device`, náhodné hodnoty zobrazené v **výstup** části nebude odpovídat výsledky. To je normální a očekávané.

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

V tomto příkladu je zneužívající vlastností prohlížeče a není reprezentativní obecné případu použití pro tento generátor. Více reprezentativní příklad kódu najdete v tématu [ \<náhodných >](../standard-library/random.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<náhodných >

**Namespace:** – std

## <a name="random_device"></a>  random_device::random_device

Vytvoří generátor.

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Poznámky

Konstruktor inicializuje generátor podle potřeby, ignoruje parametr řetězce. Vrátí hodnotu typu definované implementací odvozené od [výjimka](../standard-library/exception-class.md) Pokud `random_device` nebylo možné inicializovat.

## <a name="entropy"></a>  random_device::entropy

Odhadne náhodnost zdroje.

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odhad náhodnost zdroje, jako je měřen v bitech.

## <a name="op_call"></a>  random_device::Operator()

Vrátí náhodná hodnota.

```cpp
result_type operator()();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnoty rovnoměrně rozložen v intervalu uzavřené [ `min, max`] určeného členské funkce `min()` a `max()`. Vrátí hodnotu typu definované implementací odvozené od [výjimka](../standard-library/exception-class.md) Pokud nebylo možné získat náhodné číslo.

## <a name="see-also"></a>Viz také

[\<náhodné >](../standard-library/random.md)<br/>
