---
title: numeric_limits – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- limits/std::numeric_limits
- limits/std::numeric_limits::denorm_min
- limits/std::numeric_limits::digits
- limits/std::numeric_limits::digits10
- limits/std::numeric_limits::epsilon
- limits/std::numeric_limits::has_denorm
- limits/std::numeric_limits::has_denorm_loss
- limits/std::numeric_limits::has_infinity
- limits/std::numeric_limits::has_quiet_NaN
- limits/std::numeric_limits::has_signaling_NaN
- limits/std::numeric_limits::infinity
- limits/std::numeric_limits::is_bounded
- limits/std::numeric_limits::is_exact
- limits/std::numeric_limits::is_iec559
- limits/std::numeric_limits::is_integer
- limits/std::numeric_limits::is_modulo
- limits/std::numeric_limits::is_signed
- limits/std::numeric_limits::is_specialized
- limits/std::numeric_limits::lowest
- limits/std::numeric_limits::max
- limits/std::numeric_limits::max_digits10
- limits/std::numeric_limits::max_exponent
- limits/std::numeric_limits::max_exponent10
- limits/std::numeric_limits::min
- limits/std::numeric_limits::min_exponent
- limits/std::numeric_limits::min_exponent10
- limits/std::numeric_limits::quiet_NaN
- limits/std::numeric_limits::radix
- limits/std::numeric_limits::round_error
- limits/std::numeric_limits::round_style
- limits/std::numeric_limits::signaling_NaN
- limits/std::numeric_limits::tinyness_before
- limits/std::numeric_limits::traps
dev_langs:
- C++
helpviewer_keywords:
- std::numeric_limits [C++]
- std::numeric_limits [C++], denorm_min
- std::numeric_limits [C++], digits
- std::numeric_limits [C++], digits10
- std::numeric_limits [C++], epsilon
- std::numeric_limits [C++], has_denorm
- std::numeric_limits [C++], has_denorm_loss
- std::numeric_limits [C++], has_infinity
- std::numeric_limits [C++], has_quiet_NaN
- std::numeric_limits [C++], has_signaling_NaN
- std::numeric_limits [C++], infinity
- std::numeric_limits [C++], is_bounded
- std::numeric_limits [C++], is_exact
- std::numeric_limits [C++], is_iec559
- std::numeric_limits [C++], is_integer
- std::numeric_limits [C++], is_modulo
- std::numeric_limits [C++], is_signed
- std::numeric_limits [C++], is_specialized
- std::numeric_limits [C++], lowest
- std::numeric_limits [C++], max
- std::numeric_limits [C++], max_digits10
- std::numeric_limits [C++], max_exponent
- std::numeric_limits [C++], max_exponent10
- std::numeric_limits [C++], min
- std::numeric_limits [C++], min_exponent
- std::numeric_limits [C++], min_exponent10
- std::numeric_limits [C++], quiet_NaN
- std::numeric_limits [C++], radix
- std::numeric_limits [C++], round_error
- std::numeric_limits [C++], round_style
- std::numeric_limits [C++], signaling_NaN
- std::numeric_limits [C++], tinyness_before
- std::numeric_limits [C++], traps
ms.assetid: 9e817177-0e91-48e6-b680-0531c4b26625
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4f241ebad20cccb0bf37618e5b169df410e4b944
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="numericlimits-class"></a>numeric_limits – třída

Šablony třídy popisuje aritmetické vlastnosti vestavěné číselné typy.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class numeric_limits
```

### <a name="parameters"></a>Parametry

`Type` Datový typ základní element, jehož vlastnosti jsou právě testována dotaz nebo nastavit.

## <a name="remarks"></a>Poznámky

Záhlaví definuje explicitní specializací pro typy `wchar_t`, `bool`, `char`, `signed char`, `unsigned char`, `short`, `unsigned short`, `int`, `unsigned int`, `long`, `unsigned long`, `float`, `double`, `long double` **,** `long long`, `unsigned long long`, `char16_t`, a `char32_t`. Pro tyto explicitní specializací člen [numeric_limits::is_specialized](#is_specialized) je `true`, a všechny relevantní členy mít smysl hodnoty. Program může poskytovat další explicitní specializací. Většina členské funkce třídy popisují nebo testovací možné implementace `float`.

Pro libovolný specializace mají žádní členové smysluplný hodnoty. Objekt člena, který nemá hodnotu smysluplný ukládá nula (nebo `false`) a vrátí členské funkce, která nevrátí hodnotu smysluplný `Type(0)`.

### <a name="static-functions-and-constants"></a>Statické funkce a konstant

|||
|-|-|
|[denorm_min](#denorm_min)|Vrátí nejmenší nenulové nenormalizovanou hodnotu.|
|[číslice](#digits)|Vrátí počet číslic základ –, představující typ bez ztrátu přesnosti.|
|[digits10 –](#digits10)|Vrátí počet desetinných míst reprezentující typ bez ztrátu přesnosti.|
|[Epsilon –](#epsilon)|Vrátí rozdíl mezi 1 a nejmenší hodnota větší než 1, která představuje datového typu.|
|[has_denorm](#has_denorm)|Testy, jestli typ umožňuje nenormalizovanou hodnoty.|
|[has_denorm_loss](#has_denorm_loss)|Ověřuje, zda je ztráta přesnosti zjištěna jako ztrátu denormalization a nikoli jako nepřesný výsledek.|
|[has_infinity –](#has_infinity)|Ověřuje, zda má typ reprezentaci pro kladné nekonečno.|
|[has_quiet_NaN](#has_quiet_nan)|Ověřuje, zda typ má reprezentaci pro tichý nečíselné (NAN), což je nonsignaling.|
|[has_signaling_NaN](#has_signaling_nan)|Ověřuje, zda má typ reprezentaci pro signalizace nečíselné (NAN).|
|[Infinity](#infinity)|Reprezentace pro kladné nekonečno pro typ, pokud je k dispozici.|
|[is_bounded –](#is_bounded)|Testy, pokud sada hodnot, které může představovat typ je omezený.|
|[is_exact](#is_exact)|Testy, pokud jsou výpočty provést na typ zaokrouhlení chyby.|
|[is_iec559](#is_iec559)|Testy, pokud typ vyhovuje standardům IEC 559.|
|[is_integer](#is_integer)|Testy, pokud má typ reprezentaci celé číslo.|
|[is_modulo](#is_modulo)|Testuje, pokud má typ modulo reprezentace.|
|[is_signed](#is_signed)|Testy, pokud má typ znázornění podepsaný držitelem.|
|[is_specialized –](#is_specialized)|Testuje, pokud má explicitní specializace definovaný ve třídě šablony typu `numeric_limits`.|
|[Nejnižší](#lowest)|Vrátí největší omezenou zápornou hodnotu.|
|[max](#max)|Vrátí typ na maximální hodnotu omezené.|
|[max_digits10](#max_digits10)|Vrátí počet desetinných míst, vyžaduje se pro zajištění, že dvě odlišné hodnoty typu mají odlišné decimal reprezentace.|
|[max_exponent](#max_exponent)|Vrátí maximální kladné integrální exponent, která představuje typ s plovoucí desetinnou čárkou jako hodnotu konečné po vyvolání základ základ – této možnosti.|
|[max_exponent10](#max_exponent10)|Vrátí maximální kladné integrální exponent, která představuje typ s plovoucí desetinnou čárkou jako hodnotu konečné po vyvolání základ deset této možnosti.|
|[Min.](#min)|Vrátí minimální hodnotu normalizovaný typu.|
|[min_exponent](#min_exponent)|Vrátí maximální záporné integrální exponent, která představuje typ s plovoucí desetinnou čárkou jako hodnotu konečné po vyvolání základ základ – této možnosti.|
|[min_exponent10](#min_exponent10)|Vrátí maximální záporné integrální exponent, která představuje typ s plovoucí desetinnou čárkou jako hodnotu konečné po vyvolání základ deset této možnosti.|
|[quiet_NaN](#quiet_nan)|Vrátí reprezentaci tichý pro daný typ není číslo (NAN).|
|[radix](#radix)|Vrátí integrální základ, označuje jako základ –, použít pro reprezentaci typu.|
|[round_error –](#round_error)|Vrátí maximální zaokrouhlení chyba typu.|
|[round_style –](#round_style)|Vrátí hodnotu, která popisuje různé metody, které můžete vybrat implementace pro zaokrouhlení hodnotu s plovoucí desetinnou čárkou na celočíselnou hodnotu.|
|[signaling_NaN](#signaling_nan)|Vrátí reprezentaci signalizace nečíselné (NAN) pro typ.|
|[tinyness_before –](#tinyness_before)|Ověřuje, zda typu můžete určit, že je hodnota představující jako normalizovanou hodnotu před zaokrouhlení je příliš malá.|
|[depeše](#traps)|Jestli soutisku, která hlásí aritmetické výjimky je implementovaný pro typ testy.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<omezení >

**Namespace:** – std

## <a name="denorm_min"></a>  numeric_limits::denorm_min

Vrátí nejmenší nenulové nenormalizovanou hodnotu.

```cpp
static Type denorm_min() throw();
```

### <a name="return-value"></a>Návratová hodnota

Nejmenší nenulové hodnoty nenormalizované hodnotu.

### <a name="remarks"></a>Poznámky

`long double` je stejný jako **dvojité** pro C++ compiler.

Vrátí minimální hodnotu pro typ, který je stejný jako [min](#min) Pokud [has_denorm –](#has_denorm) se nerovná **denorm_present**.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_denorm_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The smallest nonzero denormalized value\n for float "
        << "objects is: " << numeric_limits<float>::denorm_min( )
        << endl;
   cout << "The smallest nonzero denormalized value\n for double "
        << "objects is: " << numeric_limits<double>::denorm_min( )
        << endl;
   cout << "The smallest nonzero denormalized value\n for long double "
        << "objects is: " << numeric_limits<long double>::denorm_min( )
        << endl;

   // A smaller value will round to zero
   cout << numeric_limits<float>::denorm_min( )/2 <<endl;
   cout << numeric_limits<double>::denorm_min( )/2 <<endl;
   cout << numeric_limits<long double>::denorm_min( )/2 <<endl;
}
```

```Output
The smallest nonzero denormalized value
 for float objects is: 1.4013e-045
The smallest nonzero denormalized value
 for double objects is: 4.94066e-324
The smallest nonzero denormalized value
 for long double objects is: 4.94066e-324
0
0
0
```

## <a name="digits"></a>  numeric_limits::digits

Vrátí počet číslic základ –, představující typ bez ztrátu přesnosti.

```cpp
static const int digits = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet číslic základ –, představující typ bez ztrátu přesnosti.

### <a name="remarks"></a>Poznámky

Člen ukládá počet číslic základ –, představující typ beze změny, což je počet bitů než žádné přihlašovací bit pro typ předdefinované celé číslo, nebo počet číslic mantisa pro předdefinovaný typ s plovoucí desetinnou čárkou.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_digits_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::digits <<endl;
   cout << numeric_limits<double>::digits <<endl;
   cout << numeric_limits<long double>::digits <<endl;
   cout << numeric_limits<int>::digits <<endl;
   cout << numeric_limits<__int64>::digits <<endl;
}
```

```Output
24
53
53
31
63
```

## <a name="digits10"></a>  numeric_limits::digits10

Vrátí počet desetinných míst reprezentující typ bez ztrátu přesnosti.

```cpp
static const int digits10 = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet desetinných míst reprezentující typ bez ztrátu přesnosti.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_digits10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::digits10 <<endl;
   cout << numeric_limits<double>::digits10 <<endl;
   cout << numeric_limits<long double>::digits10 <<endl;
   cout << numeric_limits<int>::digits10 <<endl;
   cout << numeric_limits<__int64>::digits10 <<endl;
   float f = (float)99999999;
   cout.precision ( 10 );
   cout << "The float is; " << f << endl;
}
```

```Output
6
15
15
9
18
The float is; 100000000
```

## <a name="epsilon"></a>  numeric_limits::epsilon

Funkce vrátí rozdíl mezi 1 a nejmenší hodnota větší než 1, který je pro datový typ reprezentovat.

```cpp
static Type epsilon() throw();
```

### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi 1 a nejmenší hodnota větší než 1, který je pro datový typ reprezentovat.

### <a name="remarks"></a>Poznámky

Hodnota je flt_epsilon – pro typ **float**. `epsilon` pro typ je nejmenší kladné číslo s plovoucí desetinnou čárkou *N* tak, aby *N* + `epsilon` + *N* je reprezentovat.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_epsilon.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The difference between 1 and the smallest "
        << "value greater than 1\n for float objects is: "
        << numeric_limits<float>::epsilon( )
        << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1\n for double objects is: "
        << numeric_limits<double>::epsilon( )
        << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1\n for long double objects is: "
        << numeric_limits<long double>::epsilon( )
        << endl;
}
```

```Output
The difference between 1 and the smallest value greater than 1
 for float objects is: 1.19209e-007
The difference between 1 and the smallest value greater than 1
 for double objects is: 2.22045e-016
The difference between 1 and the smallest value greater than 1
 for long double objects is: 2.22045e-016
```

## <a name="has_denorm"></a>  numeric_limits::has_denorm

Testy, jestli typ umožňuje nenormalizovanou hodnoty.

```cpp
static const float_denorm_style has_denorm = denorm_absent;
```

### <a name="return-value"></a>Návratová hodnota

Hodnotu výčtu typu **const**`float_denorm_style`, což značí zda typ umožňuje nenormalizované hodnoty.

### <a name="remarks"></a>Poznámky

Člen úložiště **denorm_present** pro typ s plovoucí desetinnou čárkou, který má nenormalizovanou efektivně hodnoty proměnné počet exponentu bitů.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_has_denorm.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects allow denormalized values: "
        << numeric_limits<float>::has_denorm
        << endl;
   cout << "Whether double objects allow denormalized values: "
        << numeric_limits<double>::has_denorm
        << endl;
   cout << "Whether long int objects allow denormalized values: "
        << numeric_limits<long int>::has_denorm
        << endl;
}
```

```Output
Whether float objects allow denormalized values: 1
Whether double objects allow denormalized values: 1
Whether long int objects allow denormalized values: 0
```

## <a name="has_denorm_loss"></a>  numeric_limits::has_denorm_loss

Ověřuje, zda je ztráta přesnosti zjištěna jako ztrátu denormalization a nikoli jako nepřesný výsledek.

```cpp
static const bool has_denorm_loss = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud se detekuje ztrátu přesnosti jako ztrátu denormalization; **false** není-li.

### <a name="remarks"></a>Poznámky

Člen ukládá hodnotu true pro typ, který určuje, zda hodnota ztratil přesnost, protože je dodávána jako výsledku nenormalizované (příliš malá, aby představují jako normalizovanou hodnotu), nebo protože je nepřesný (není stejný jako v důsledku není předmětem omezení exponent rozsah a přesnost), možnost s IEC 559 reprezentace s plovoucí desetinnou čárkou, které můžou ovlivnit některé výsledky.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_has_denorm_loss.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects can detect denormalized loss: "
        << numeric_limits<float>::has_denorm_loss
        << endl;
   cout << "Whether double objects can detect denormalized loss: "
        << numeric_limits<double>::has_denorm_loss
        << endl;
   cout << "Whether long int objects can detect denormalized loss: "
        << numeric_limits<long int>::has_denorm_loss
        << endl;
}
```

```Output
Whether float objects can detect denormalized loss: 1
Whether double objects can detect denormalized loss: 1
Whether long int objects can detect denormalized loss: 0
```

## <a name="has_infinity"></a>  numeric_limits::has_infinity

Ověřuje, zda má typ reprezentaci pro kladné nekonečno.

```cpp
static const bool has_infinity = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud má typ reprezentaci pro kladné nekonečno; **false** není-li.

### <a name="remarks"></a>Poznámky

Vrací člena **true** Pokud [is_iec559 –](#is_iec559) je **true**.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_has_infinity.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have infinity: "
        << numeric_limits<float>::has_infinity
        << endl;
   cout << "Whether double objects have infinity: "
        << numeric_limits<double>::has_infinity
        << endl;
   cout << "Whether long int objects have infinity: "
        << numeric_limits<long int>::has_infinity
        << endl;
}
```

```Output
Whether float objects have infinity: 1
Whether double objects have infinity: 1
Whether long int objects have infinity: 0
```

## <a name="has_quiet_nan"></a>  numeric_limits::has_quiet_NaN

Ověřuje, zda typ má reprezentaci pro tichý nečíselné (NAN), což je nonsignaling.

```cpp
static const bool has_quiet_NaN = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud **typ** má znázornění quiet NaN; **false** není-li.

### <a name="remarks"></a>Poznámky

Quiet NAN je kódování pro není číslo, které nevydá signál své přítomnosti ve výrazu. Vrácená hodnota je **true** Pokud [is_iec559 –](#is_iec559) hodnotu true.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_has_quiet_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have quiet_NaN: "
        << numeric_limits<float>::has_quiet_NaN
        << endl;
   cout << "Whether double objects have quiet_NaN: "
        << numeric_limits<double>::has_quiet_NaN
        << endl;
   cout << "Whether long int objects have quiet_NaN: "
        << numeric_limits<long int>::has_quiet_NaN
        << endl;
}
```

```Output
Whether float objects have quiet_NaN: 1
Whether double objects have quiet_NaN: 1
Whether long int objects have quiet_NaN: 0
```

## <a name="has_signaling_nan"></a>  numeric_limits::has_signaling_NaN

Ověřuje, zda má typ reprezentaci pro signalizace nečíselné (NAN).

```cpp
static const bool has_signaling_NaN = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud má typ znázornění signalizační NaN; **false** není-li.

### <a name="remarks"></a>Poznámky

Signalizační NAN je kódování pro není číslo, která signalizuje své přítomnosti ve výrazu. Vrácená hodnota je **true** Pokud [is_iec559 –](#is_iec559) hodnotu true.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_has_signaling_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a signaling_NaN: "
        << numeric_limits<float>::has_signaling_NaN
        << endl;
   cout << "Whether double objects have a signaling_NaN: "
        << numeric_limits<double>::has_signaling_NaN
        << endl;
   cout << "Whether long int objects have a signaling_NaN: "
        << numeric_limits<long int>::has_signaling_NaN
        << endl;
}
```

```Output
Whether float objects have a signaling_NaN: 1
Whether double objects have a signaling_NaN: 1
Whether long int objects have a signaling_NaN: 0
```

## <a name="infinity"></a>  numeric_limits::Infinity

Reprezentace kladné nekonečno pro typ, pokud je k dispozici.

```cpp
static Type infinity() throw();
```

### <a name="return-value"></a>Návratová hodnota

Reprezentace kladné nekonečno pro typ, pokud je k dispozici.

### <a name="remarks"></a>Poznámky

Návratová hodnota má smysl pouze v případě [has_infinity –](#has_infinity) je **true**.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_infinity.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::has_infinity <<endl;
   cout << numeric_limits<double>::has_infinity<<endl;
   cout << numeric_limits<long double>::has_infinity <<endl;
   cout << numeric_limits<int>::has_infinity <<endl;
   cout << numeric_limits<__int64>::has_infinity <<endl;

   cout << "The representation of infinity for type float is: "
        << numeric_limits<float>::infinity( ) <<endl;
   cout << "The representation of infinity for type double is: "
        << numeric_limits<double>::infinity( ) <<endl;
   cout << "The representation of infinity for type long double is: "
        << numeric_limits<long double>::infinity( ) <<endl;
}
```

```Output
1
1
1
0
0
The representation of infinity for type float is: inf
The representation of infinity for type double is: inf
The representation of infinity for type long double is: inf
```

## <a name="is_bounded"></a>  numeric_limits::is_bounded

Testy, pokud sada hodnot, které může představovat typ je omezený.

```cpp
static const bool is_bounded = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud má typ ohraničené sadu reprezentovat hodnot; **false** není-li.

### <a name="remarks"></a>Poznámky

Všechny předdefinovaných typů mají ohraničené sadu reprezentovat hodnoty a vrátit **true**.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_is_bounded.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have bounded set "
        << "of representable values: "
        << numeric_limits<float>::is_bounded
        << endl;
   cout << "Whether double objects have bounded set "
        << "of representable values: "
        << numeric_limits<double>::is_bounded
        << endl;
   cout << "Whether long int objects have bounded set "
        << "of representable values: "
        << numeric_limits<long int>::is_bounded
        << endl;
   cout << "Whether unsigned char objects have bounded set "
        << "of representable values: "
        << numeric_limits<unsigned char>::is_bounded
        << endl;
}
```

```Output
Whether float objects have bounded set of representable values: 1
Whether double objects have bounded set of representable values: 1
Whether long int objects have bounded set of representable values: 1
Whether unsigned char objects have bounded set of representable values: 1
```

## <a name="is_exact"></a>  numeric_limits::is_exact

Testy, pokud jsou výpočty provést na typ zaokrouhlení chyby.

```cpp
static const bool is_exact = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud výpočty jsou zadarmo zaokrouhlení chyby; **false** není-li.

### <a name="remarks"></a>Poznámky

Všechny typy integer s předdefinované mít přesný reprezentace pro jejich hodnoty a vrátit **false**. Znázornění s pevnou desetinnou čárkou nebo rozumné považuje také přesný, ale není reprezentace plovoucí desetinné čárky.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_is_exact.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<float>::is_exact
        << endl;
   cout << "Whether double objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<double>::is_exact
        << endl;
   cout << "Whether long int objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<long int>::is_exact
        << endl;
   cout << "Whether unsigned char objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<unsigned char>::is_exact
        << endl;
}
```

```Output
Whether float objects have calculations free of rounding errors: 0
Whether double objects have calculations free of rounding errors: 0
Whether long int objects have calculations free of rounding errors: 1
Whether unsigned char objects have calculations free of rounding errors: 1
```

## <a name="is_iec559"></a>  numeric_limits::is_iec559

Testy, pokud typ vyhovuje standardům IEC 559.

```cpp
static const bool is_iec559 = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud typ vyhovuje standardům IEC 559; **false** není-li.

### <a name="remarks"></a>Poznámky

IEC 559 je mezinárodní standard pro představující hodnoty s plovoucí desetinnou čárkou a je také označován jako IEEE 754 v USA.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_is_iec559.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects conform to iec559 standards: "
        << numeric_limits<float>::is_iec559
        << endl;
   cout << "Whether double objects conform to iec559 standards: "
        << numeric_limits<double>::is_iec559
        << endl;
   cout << "Whether int objects conform to iec559 standards: "
        << numeric_limits<int>::is_iec559
        << endl;
   cout << "Whether unsigned char objects conform to iec559 standards: "
        << numeric_limits<unsigned char>::is_iec559
        << endl;
}
```

```Output
Whether float objects conform to iec559 standards: 1
Whether double objects conform to iec559 standards: 1
Whether int objects conform to iec559 standards: 0
Whether unsigned char objects conform to iec559 standards: 0
```

## <a name="is_integer"></a>  numeric_limits::is_integer

Testy, pokud má typ reprezentaci celé číslo.

```cpp
static const bool is_integer = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud má typ reprezentaci celé číslo; **false** není-li.

### <a name="remarks"></a>Poznámky

Všechny typy předdefinované celé číslo mají reprezentaci celé číslo.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_is_integer.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have an integral representation: "
        << numeric_limits<float>::is_integer
        << endl;
   cout << "Whether double objects have an integral representation: "
        << numeric_limits<double>::is_integer
        << endl;
   cout << "Whether int objects have an integral representation: "
        << numeric_limits<int>::is_integer
        << endl;
   cout << "Whether unsigned char objects have an integral representation: "
        << numeric_limits<unsigned char>::is_integer
        << endl;
}
```

```Output
Whether float objects have an integral representation: 0
Whether double objects have an integral representation: 0
Whether int objects have an integral representation: 1
Whether unsigned char objects have an integral representation: 1
```

## <a name="is_modulo"></a>  numeric_limits::is_modulo

Testuje, pokud **typ** má modulo reprezentace.

```cpp
static const bool is_modulo = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud má typ modulo reprezentace; **false** není-li.

### <a name="remarks"></a>Poznámky

A modulo reprezentace je reprezentace, kde jsou všechny výsledky omezeny modulo některá z hodnot. Všechny typy předdefinované celé číslo bez znaménka mají modulo reprezentace.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_is_modulo.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a modulo representation: "
        << numeric_limits<float>::is_modulo
        << endl;
   cout << "Whether double objects have a modulo representation: "
        << numeric_limits<double>::is_modulo
        << endl;
   cout << "Whether signed char objects have a modulo representation: "
        << numeric_limits<signed char>::is_modulo
        << endl;
   cout << "Whether unsigned char objects have a modulo representation: "
        << numeric_limits<unsigned char>::is_modulo
        << endl;
}
```

```Output
Whether float objects have a modulo representation: 0
Whether double objects have a modulo representation: 0
Whether signed char objects have a modulo representation: 1
Whether unsigned char objects have a modulo representation: 1
```

## <a name="is_signed"></a>  numeric_limits::is_signed

Testy, pokud má typ znázornění podepsaný držitelem.

```cpp
static const bool is_signed = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud má typ znázornění podepsaný; **false** není-li.

### <a name="remarks"></a>Poznámky

Člen ukládá hodnotu true pro typ, který má znázornění podepsaný držitelem, které platí pro všechny předdefinovaných typů s plovoucí desetinnou čárkou a podepsaný celé číslo.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_is_signaled.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a signed representation: "
        << numeric_limits<float>::is_signed
        << endl;
   cout << "Whether double objects have a signed representation: "
        << numeric_limits<double>::is_signed
        << endl;
   cout << "Whether signed char objects have a signed representation: "
        << numeric_limits<signed char>::is_signed
        << endl;
   cout << "Whether unsigned char objects have a signed representation: "
        << numeric_limits<unsigned char>::is_signed
        << endl;
}
```

```Output
Whether float objects have a signed representation: 1
Whether double objects have a signed representation: 1
Whether signed char objects have a signed representation: 1
Whether unsigned char objects have a signed representation: 0
```

## <a name="is_specialized"></a>  numeric_limits::is_specialized

Testuje, pokud má explicitní specializace definovaný ve třídě šablony typu `numeric_limits`.

```cpp
static const bool is_specialized = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud má typ explicitní specializace definovaný ve třídě šablony; **false** není-li.

### <a name="remarks"></a>Poznámky

Všechny Skalární typy než ukazatele mají explicitní specializace definovaný pro třídu šablony `numeric_limits`.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_is_specialized.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<float>::is_specialized
        << endl;
   cout << "Whether float* objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<float*>::is_specialized
        << endl;
   cout << "Whether int objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<int>::is_specialized
        << endl;
   cout << "Whether int* objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<int*>::is_specialized
        << endl;
}
```

```Output
Whether float objects have an explicit specialization in the class: 1
Whether float* objects have an explicit specialization in the class: 0
Whether int objects have an explicit specialization in the class: 1
Whether int* objects have an explicit specialization in the class: 0
```

## <a name="lowest"></a>  numeric_limits::lowest

Vrátí největší omezenou zápornou hodnotu.

```cpp
static Type lowest() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí největší omezenou zápornou hodnotu.

### <a name="remarks"></a>Poznámky

Vrátí konečný nejvíce zápornou hodnotu pro typ (což obvykle představuje `min()` pro typy celého čísla a `-max()` pro typy s plovoucí desetinnou čárkou). Návratová hodnota má smysl Pokud `is_bounded` je `true`.

## <a name="max"></a>  numeric_limits::max

Vrátí typ na maximální hodnotu omezené.

```cpp
static Type max() throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální hodnota konečné typu.

### <a name="remarks"></a>Poznámky

Maximální hodnota konečné je INT_MAX – pro typ `int` a flt_max – pro typ **float**. Návratová hodnota má smysl Pokud [is_bounded –](#is_bounded) je **true**.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_max.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main() {
   cout << "The maximum value for type float is:  "
        << numeric_limits<float>::max( )
        << endl;
   cout << "The maximum value for type double is:  "
        << numeric_limits<double>::max( )
        << endl;
   cout << "The maximum value for type int is:  "
        << numeric_limits<int>::max( )
        << endl;
   cout << "The maximum value for type short int is:  "
        << numeric_limits<short int>::max( )
        << endl;
}
```

## <a name="max_digits10"></a>  numeric_limits::max_digits10

Vrátí počet desetinných míst, které jsou potřebné k ověření, zda dva odlišné hodnoty typu distinct decimal reprezentace.

```cpp
static int max_digits10 = 0;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet desetinných míst, které jsou požadovány pro ověření, zda dva odlišné hodnoty typu distinct decimal reprezentace.

### <a name="remarks"></a>Poznámky

Člen ukládá počet desetinných míst, které jsou potřebné k ověření, zda dva odlišné hodnoty typu distinct decimal reprezentace.

## <a name="max_exponent"></a>  numeric_limits::max_exponent

Vrátí maximální kladné integrální exponent, která představuje typ s plovoucí desetinnou čárkou jako hodnotu konečné po vyvolání základ základ – této možnosti.

```cpp
static const int max_exponent = 0;
```

### <a name="return-value"></a>Návratová hodnota

Maximální integrální na základě základ – exponent reprezentovat podle typu.

### <a name="remarks"></a>Poznámky

Návratový – členská funkce má smysl jenom pro typy s plovoucí desetinnou čárkou. `max_exponent` Je hodnota flt_max_exp – pro typ **float**.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_max_exponent.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum radix-based exponent for type float is:  "
        << numeric_limits<float>::max_exponent
        << endl;
   cout << "The maximum radix-based exponent for type double is:  "
        << numeric_limits<double>::max_exponent
        << endl;
   cout << "The maximum radix-based exponent for type long double is:  "
        << numeric_limits<long double>::max_exponent
        << endl;
}
```

```Output
The maximum radix-based exponent for type float is:  128
The maximum radix-based exponent for type double is:  1024
The maximum radix-based exponent for type long double is:  1024
```

## <a name="max_exponent10"></a>  numeric_limits::max_exponent10

Vrátí maximální kladné integrální exponent, která představuje typ s plovoucí desetinnou čárkou jako hodnotu konečné po vyvolání základ deset této možnosti.

```cpp
static const int max_exponent10 = 0;
```

### <a name="return-value"></a>Návratová hodnota

Exponent reprezentovat maximální integrální se základem 10 podle typu.

### <a name="remarks"></a>Poznámky

Návratový – členská funkce má smysl jenom pro typy s plovoucí desetinnou čárkou. `max_exponent` Je hodnota FLT_MAX_10 pro typ **float**.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_max_exponent10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum base 10 exponent for type float is:  "
           << numeric_limits<float>::max_exponent10
           << endl;
   cout << "The maximum base 10 exponent for type double is:  "
           << numeric_limits<double>::max_exponent10
           << endl;
   cout << "The maximum base 10 exponent for type long double is:  "
           << numeric_limits<long double>::max_exponent10
           << endl;
}
```

```Output
The maximum base 10 exponent for type float is:  38
The maximum base 10 exponent for type double is:  308
The maximum base 10 exponent for type long double is:  308
```

## <a name="min"></a>  numeric_limits::min

Vrátí minimální hodnotu normalizovaný typu.

```cpp
static Type min() throw();
```

### <a name="return-value"></a>Návratová hodnota

Minimální Normalizovaná hodnota pro typ.

### <a name="remarks"></a>Poznámky

Minimální hodnota normalizovaný je int_min – pro typ `int` a flt_min – pro typ `float`. Návratová hodnota má smysl Pokud [is_bounded –](#is_bounded) je `true` nebo, pokud [is_signed](#is_signed) je `false`.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum value for type float is:  "
        << numeric_limits<float>::min( )
        << endl;
   cout << "The minimum value for type double is:  "
        << numeric_limits<double>::min( )
        << endl;
   cout << "The minimum value for type int is:  "
        << numeric_limits<int>::min( )
        << endl;
   cout << "The minimum value for type short int is:  "
        << numeric_limits<short int>::min( )
        << endl;
}
```

```Output
The minimum value for type float is:  1.17549e-038
The minimum value for type double is:  2.22507e-308
The minimum value for type int is:  -2147483648
The minimum value for type short int is:  -32768
```

## <a name="min_exponent"></a>  numeric_limits::min_exponent

Vrátí maximální záporné integrální exponent, která představuje typ s plovoucí desetinnou čárkou jako hodnotu konečné po vyvolání základ základ – této možnosti.

```cpp
static const int min_exponent = 0;
```

### <a name="return-value"></a>Návratová hodnota

Minimální celočíselné na základě základ – exponent reprezentovat podle typu.

### <a name="remarks"></a>Poznámky

Členská funkce má smysl jenom pro typy s plovoucí desetinnou čárkou. `min_exponent` Je hodnota flt_min_exp – pro typ **float**.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_min_exponent.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum radix-based exponent for type float is:  "
        << numeric_limits<float>::min_exponent
        << endl;
   cout << "The minimum radix-based exponent for type double is:  "
        << numeric_limits<double>::min_exponent
        << endl;
   cout << "The minimum radix-based exponent for type long double is:  "
         << numeric_limits<long double>::min_exponent
        << endl;
}
```

```Output
The minimum radix-based exponent for type float is:  -125
The minimum radix-based exponent for type double is:  -1021
The minimum radix-based exponent for type long double is:  -1021
```

## <a name="min_exponent10"></a>  numeric_limits::min_exponent10

Vrátí maximální záporné integrální exponent, která představuje typ s plovoucí desetinnou čárkou jako hodnotu konečné po vyvolání základ deset této možnosti.

```cpp
static const int min_exponent10 = 0;
```

### <a name="return-value"></a>Návratová hodnota

Exponent reprezentovat minimální celočíselné se základem 10 podle typu.

### <a name="remarks"></a>Poznámky

Členská funkce má smysl jenom pro typy s plovoucí desetinnou čárkou. `min_exponent10` Je hodnota flt_min_10_exp – pro typ **float**.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_min_exponent10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum base 10 exponent for type float is:  "
        << numeric_limits<float>::min_exponent10
        << endl;
   cout << "The minimum base 10 exponent for type double is:  "
        << numeric_limits<double>::min_exponent10
        << endl;
   cout << "The minimum base 10 exponent for type long double is:  "
        << numeric_limits<long double>::min_exponent10
        << endl;
}
```

```Output
The minimum base 10 exponent for type float is:  -37
The minimum base 10 exponent for type double is:  -307
The minimum base 10 exponent for type long double is:  -307
```

## <a name="quiet_nan"></a>  numeric_limits::quiet_NaN

Vrátí reprezentaci tichý pro daný typ není číslo (NAN).

```cpp
static Type quiet_NaN() throw();
```

### <a name="return-value"></a>Návratová hodnota

Reprezentace quiet NAN pro typ.

### <a name="remarks"></a>Poznámky

Návratová hodnota má smysl pouze v případě [has_quiet_nan –](#has_quiet_nan) je **true**.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_quiet_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The quiet NaN for type float is:  "
        << numeric_limits<float>::quiet_NaN( )
        << endl;
   cout << "The quiet NaN for type int is:  "
        << numeric_limits<int>::quiet_NaN( )
        << endl;
   cout << "The quiet NaN for type long double is:  "
        << numeric_limits<long double>::quiet_NaN( )
        << endl;
}
```

```Output
The quiet NaN for type float is:  1.#QNAN
The quiet NaN for type int is:  0
The quiet NaN for type long double is:  1.#QNAN
```

## <a name="radix"></a>  numeric_limits::radix

Vrátí integrální základ, označuje jako základ –, použít pro reprezentaci typu.

```cpp
static const int radix = 0;
```

### <a name="return-value"></a>Návratová hodnota

Integrální základ pro reprezentaci typu.

### <a name="remarks"></a>Poznámky

Základní je 2 pro typy předdefinované celé číslo a základní, ke které se vyvolá exponent nebo flt_radix –, předdefinovaných typů s plovoucí desetinnou čárkou.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_radix.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The base for type float is:  "
        << numeric_limits<float>::radix
        << endl;
   cout << "The base for type int is:  "
        << numeric_limits<int>::radix
        << endl;
   cout << "The base for type long double is:  "
        << numeric_limits<long double>::radix
        << endl;
}
```

```Output
The base for type float is:  2
The base for type int is:  2
The base for type long double is:  2
```

## <a name="round_error"></a>  numeric_limits::round_error

Vrátí maximální zaokrouhlení chyba typu.

```cpp
static Type round_error() throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet zaokrouhlení chyba typu.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_round_error.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum rounding error for type float is:  "
        << numeric_limits<float>::round_error( )
        << endl;
   cout << "The maximum rounding error for type int is:  "
        << numeric_limits<int>::round_error( )
        << endl;
   cout << "The maximum rounding error for type long double is:  "
        << numeric_limits<long double>::round_error( )
        << endl;
}
```

```Output
The maximum rounding error for type float is:  0.5
The maximum rounding error for type int is:  0
The maximum rounding error for type long double is:  0.5
```

## <a name="round_style"></a>  numeric_limits::round_style

Vrátí hodnotu, která popisuje různé metody, které můžete vybrat implementace pro zaokrouhlení hodnotu s plovoucí desetinnou čárkou na celočíselnou hodnotu.

```cpp
static const float_round_style round_style = round_toward_zero;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota z `float_round_style` styl výčet, který popisuje zaokrouhlení.

### <a name="remarks"></a>Poznámky

Člen ukládá hodnotu, která popisuje různé metody, které můžete vybrat implementace pro zaokrouhlení hodnotu s plovoucí desetinnou čárkou na celočíselnou hodnotu.

Styl zaokrouhlí je pevný programového v této implementaci, tak i, že pokud se program spustí s jiný režim zaokrouhlení, nedojde ke změně této hodnotě.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_round_style.cpp
// compile with: /EHsc
#include <iostream>
#include <float.h>
#include <limits>

using namespace std;

int main( )
{
   cout << "The rounding style for a double type is: "
        << numeric_limits<double>::round_style << endl;
   _controlfp_s(NULL,_RC_DOWN,_MCW_RC );
   cout << "The rounding style for a double type is now: "
        << numeric_limits<double>::round_style << endl;
   cout << "The rounding style for an int type is: "
        << numeric_limits<int>::round_style << endl;
}
```

```Output
The rounding style for a double type is: 1
The rounding style for a double type is now: 1
The rounding style for an int type is: 0
```

## <a name="signaling_nan"></a>  numeric_limits::signaling_NaN

Vrátí reprezentaci signalizace nečíselné (NAN) pro typ.

```cpp
static Type signaling_NaN() throw();
```

### <a name="return-value"></a>Návratová hodnota

Reprezentace signalizační NAN pro typ.

### <a name="remarks"></a>Poznámky

Návratová hodnota má smysl pouze v případě [has_signaling_nan –](#has_signaling_nan) je **true**.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_signaling_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The signaling NaN for type float is:  "
        << numeric_limits<float>::signaling_NaN( )
        << endl;
   cout << "The signaling NaN for type int is:  "
        << numeric_limits<int>::signaling_NaN( )
        << endl;
   cout << "The signaling NaN for type long double is:  "
        << numeric_limits<long double>::signaling_NaN( )
        << endl;
}
```

## <a name="tinyness_before"></a>  numeric_limits::tinyness_before

Ověřuje, zda typu můžete určit, že je hodnota představující jako normalizovanou hodnotu před zaokrouhlení je příliš malá.

```cpp
static const bool tinyness_before = false;
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud typ může zjistit jen nepatrnou hodnoty před zaokrouhlení; `false` pokud ji nelze.

### <a name="remarks"></a>Poznámky

Typy, které může zjistit tinyness byly zahrnuty i s IEC 559 reprezentace plovoucí desetinné čárky a jeho implementace může ovlivnit některé výsledky.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_tinyness_before.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float types can detect tinyness before rounding: "
        << numeric_limits<float>::tinyness_before
        << endl;
   cout << "Whether double types can detect tinyness before rounding: "
        << numeric_limits<double>::tinyness_before
        << endl;
   cout << "Whether long int types can detect tinyness before rounding: "
        << numeric_limits<long int>::tinyness_before
        << endl;
   cout << "Whether unsigned char types can detect tinyness before rounding: "
        << numeric_limits<unsigned char>::tinyness_before
        << endl;
}
```

```Output
Whether float types can detect tinyness before rounding: 1
Whether double types can detect tinyness before rounding: 1
Whether long int types can detect tinyness before rounding: 0
Whether unsigned char types can detect tinyness before rounding: 0
```

## <a name="traps"></a>  numeric_limits::traps

Jestli soutisku, která hlásí aritmetické výjimky je implementovaný pro typ testy.

```cpp
static const bool traps = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE,** Pokud zachytávání je implementovaný pro typ; **false** Pokud není.

### <a name="example"></a>Příklad

```cpp
// numeric_limits_traps.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float types have implemented trapping: "
        << numeric_limits<float>::traps
        << endl;
   cout << "Whether double types have implemented trapping: "
        << numeric_limits<double>::traps
        << endl;
   cout << "Whether long int types have implemented trapping: "
        << numeric_limits<long int>::traps
        << endl;
   cout << "Whether unsigned char types have implemented trapping: "
        << numeric_limits<unsigned char>::traps
        << endl;
}
```

```Output
Whether float types have implemented trapping: 1
Whether double types have implemented trapping: 1
Whether long int types have implemented trapping: 0
Whether unsigned char types have implemented trapping: 0
```

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
