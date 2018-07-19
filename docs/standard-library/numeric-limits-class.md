---
title: numeric_limits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a14d5012e1db8dec0f1aa6c39d8764232169dec2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954874"
---
# <a name="numericlimits-class"></a>numeric_limits – třída

Třída šablony popisuje aritmetické vlastnosti předdefinovaných číselných typů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class numeric_limits
```

### <a name="parameters"></a>Parametry

*Typ* základní prvek datový typ, jehož vlastnosti jsou právě testováno nebo dotazovat nebo nastavit.

## <a name="remarks"></a>Poznámky

Záhlaví definuje explicitní specializace pro typy **wchar_t**, **bool**, **char**, **podepsané char**, **bez znaménka Char**, **krátký**, **unsigned short**, **int**, **unsigned int**, **dlouho**, **unsigned long**, **float**, **double**, **long double ***,** **long long**, **unsigned long long.**, `char16_t`, a `char32_t`. Pro tyto explicitní specializace členu [numeric_limits::is_specialized](#is_specialized) je **true**, a všechny relevantní členy mají smysluplné hodnoty. Program můžete zadat další explicitní specializace. Většina členské funkce třídy popisují nebo testování je to možné implementace **float**.

Pro libovolné specializace mít žádné členy smysluplné hodnoty. Uloží objekt člena, který nemá smysluplnou hodnotu nula (nebo **false**) a vrátí členskou funkci, která nevrací hodnotu smysluplné `Type(0)`.

### <a name="static-functions-and-constants"></a>Statické funkce a konstanty

|||
|-|-|
|[denorm_min](#denorm_min)|Vrátí nejmenší nenulovou denormalizovaný hodnotu.|
|[číslice](#digits)|Vrátí počet číslic základ číselné soustavy, představující typ bez ztráty přesnosti.|
|[digits10 –](#digits10)|Vrátí počet desetinných míst, představující typ bez ztráty přesnosti.|
|[Epsilon –](#epsilon)|Vrátí rozdíl mezi 1 a nejmenší hodnotu větší než 1, které mohou představovat datového typu.|
|[has_denorm](#has_denorm)|Testuje, zda typ umožňuje denormalizovaný hodnoty.|
|[has_denorm_loss](#has_denorm_loss)|Ověřuje, zda ztrátou přesnosti se detekuje jako denormalizace ztrátu, nikoli jako nepřesné výsledky.|
|[has_infinity –](#has_infinity)|Ověřuje, zda typ má reprezentaci pro kladné nekonečno.|
|[has_quiet_NaN](#has_quiet_nan)|Ověřuje, zda typ má reprezentaci pro tichý nečíselné (NAN), což je nonsignaling.|
|[has_signaling_NaN](#has_signaling_nan)|Ověřuje, zda typ má reprezentaci pro signalizaci nečíselné (NAN).|
|[Infinity](#infinity)|Reprezentace pro kladné nekonečno pro typ, pokud je k dispozici.|
|[is_bounded](#is_bounded)|Testuje, zda je sada hodnot, které mohou představovat typ je omezené.|
|[is_exact](#is_exact)|Testuje, zda jsou zdarma předešlo chybám při zaokrouhlování výpočty provést u typu.|
|[is_iec559](#is_iec559)|Testuje, zda je typ odpovídá IEC 559 standardy.|
|[is_integer](#is_integer)|Testuje, zda je typ má reprezentaci celého čísla.|
|[is_modulo](#is_modulo)|Testuje, zda má typ modulo reprezentace.|
|[is_signed –](#is_signed)|Testuje, zda je typ má reprezentaci podepsaný držitelem.|
|[is_specialized –](#is_specialized)|Testuje, zda typ má explicitní specializace definované v šabloně třídy `numeric_limits`.|
|[Nejnižší](#lowest)|Vrátí největší omezenou zápornou hodnotu.|
|[max](#max)|Vrátí maximální konečná hodnota typu.|
|[max_digits10](#max_digits10)|Vrátí počet desetinných míst, které jsou potřeba k tomu, že dvě odlišné hodnoty typu mají odlišné reprezentace decimal.|
|[max_exponent](#max_exponent)|Vrátí maximální kladný celočíselný exponent, který typ s plovoucí desetinnou čárkou mohou představovat jako konečnou hodnotu po její základní základ číselné soustavy je vyvolávána s cílem, které stojí za.|
|[max_exponent10](#max_exponent10)|Vrátí maximální kladné celočíselné exponent, který typ s plovoucí desetinnou čárkou mohou představovat jako konečnou hodnotu při vyvolání třídou base deset na výkon.|
|[min](#min)|Vrátí minimální Normalizovaná hodnota typu.|
|[min_exponent](#min_exponent)|Vrátí maximální negativní integrální exponent, který typ s plovoucí desetinnou čárkou mohou představovat jako konečnou hodnotu po její základní základ číselné soustavy je vyvolávána s cílem, které stojí za.|
|[min_exponent10](#min_exponent10)|Vrátí maximální negativní integrální exponent, který typ s plovoucí desetinnou čárkou mohou představovat jako konečnou hodnotu při vyvolání třídou base deset na výkon.|
|[quiet_NaN](#quiet_nan)|Vrátí reprezentaci tichý pro typ není číslo (NAN).|
|[radix](#radix)|Vrátí integrální base označovány jako základ, použitý pro reprezentaci typu.|
|[round_error –](#round_error)|Vrátí maximální zaokrouhlení typ v podrobnostech o chybě.|
|[round_style –](#round_style)|Vrátí hodnotu, která popisuje různé metody, které můžete vybrat implementace zaokrouhlení s plovoucí desetinnou čárkou na celočíselnou hodnotu.|
|[signaling_NaN](#signaling_nan)|Pro typ, vrátí reprezentaci signalizace nečíselné (NAN).|
|[tinyness_before –](#tinyness_before)|Ověřuje, zda typ můžete určit, že hodnota je příliš malá, aby reprezentovala normalizovanou hodnotu před jeho zaokrouhlení.|
|[depeše](#traps)|Testuje, zda soutisku, která informuje o aritmetické výjimky je implementován pro typ.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<omezení >

**Namespace:** std

## <a name="denorm_min"></a>  numeric_limits::denorm_min

Vrátí nejmenší nenulovou denormalizovaný hodnotu.

```cpp
static Type denorm_min() throw();
```

### <a name="return-value"></a>Návratová hodnota

Nejmenší nenulovou Nenormalizovaná hodnotu.

### <a name="remarks"></a>Poznámky

**long double** je stejný jako **double** pro kompilátor jazyka C++.

Vrátí minimální hodnotu pro typ, který je stejný jako [min](#min) Pokud [has_denorm –](#has_denorm) není roven `denorm_present`.

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

Vrátí počet číslic základ číselné soustavy, představující typ bez ztráty přesnosti.

```cpp
static const int digits = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet číslic základ číselné soustavy, představující typ bez ztráty přesnosti.

### <a name="remarks"></a>Poznámky

Člen ukládá počet číslic základ číselné soustavy, představující typ beze změny, což je počet bitů než všechny bit znaménka pro předdefinované celočíselný typ, nebo počet číslic mantisa pro předdefinovaný typ s plovoucí desetinnou čárkou.

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

Vrátí počet desetinných míst, představující typ bez ztráty přesnosti.

```cpp
static const int digits10 = 0;
```

### <a name="return-value"></a>Návratová hodnota

Počet desetinných míst, které mohou představovat typ bez ztráty přesnosti.

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

Funkce vrátí rozdíl mezi 1 a nejmenší hodnotu větší než 1, který je reprezentovat podle datového typu.

```cpp
static Type epsilon() throw();
```

### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi 1 a nejmenší hodnotu větší než 1, který je reprezentovat podle datového typu.

### <a name="remarks"></a>Poznámky

Hodnota je typu FLT_EPSILON **float**. `epsilon` pro typ je nejmenší kladné číslo s plovoucí desetinnou čárkou *N* tak, aby *N* + `epsilon` + *N* je reprezentovatelné.

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

Testuje, zda typ umožňuje denormalizovaný hodnoty.

```cpp
static const float_denorm_style has_denorm = denorm_absent;
```

### <a name="return-value"></a>Návratová hodnota

Hodnotu výčtu typu **const**`float_denorm_style`, která udává, zda typ umožňuje Nenormalizovaná hodnoty.

### <a name="remarks"></a>Poznámky

Člen úložišť `denorm_present` pro typ s plovoucí desetinnou čárkou, který obsahuje Nenormalizovaná hodnoty efektivně proměnný počet bitů exponentu.

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

Ověřuje, zda ztrátou přesnosti se detekuje jako denormalizace ztrátu, nikoli jako nepřesné výsledky.

```cpp
static const bool has_denorm_loss = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud se zjistí ztrátou přesnosti denormalizace ztrátu; **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Člen ukládá hodnotu true pro typ, který určuje, zda hodnotu ztratil přesnost, protože je dodávána jako Nenormalizovaná výsledek (příliš malá, aby reprezentovala normalizovanou hodnotu) nebo je nepřesný (není stejný jako výsledek nevztahují se k omezení exponent rozsah a přesnost), možnost s IEC 559 s plovoucí desetinnou čárkou záruky, které mohou ovlivnit některé výsledky.

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

Ověřuje, zda typ má reprezentaci pro kladné nekonečno.

```cpp
static const bool has_infinity = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud má typ reprezentaci pro kladné nekonečno; **false** Pokud tomu tak není.

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

**Hodnota TRUE** Pokud **typ** má reprezentaci tichý NaN; **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Tichý NAN je kódování není číslo, které nevydá signál své přítomnosti ve výrazu. Vrácená hodnota je **true** Pokud [is_iec559 –](#is_iec559) má hodnotu true.

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

Ověřuje, zda typ má reprezentaci pro signalizaci nečíselné (NAN).

```cpp
static const bool has_signaling_NaN = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud typ má reprezentaci signalizační NaN; **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Signalizace NAN je kódování není číslo, která signalizuje své přítomnosti ve výrazu. Vrácená hodnota je **true** Pokud [is_iec559 –](#is_iec559) má hodnotu true.

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

Reprezentuje kladné nekonečno pro typ, pokud je k dispozici.

```cpp
static Type infinity() throw();
```

### <a name="return-value"></a>Návratová hodnota

Reprezentuje kladné nekonečno pro typ, pokud je k dispozici.

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

Testuje, zda je sada hodnot, které mohou představovat typ je omezené.

```cpp
static const bool is_bounded = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud má typ omezená sada hodnot reprezentovatelných; **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Máte omezená sada hodnot reprezentovatelných všechny předdefinované typy a vrátit **true**.

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

Testuje, zda jsou zdarma předešlo chybám při zaokrouhlování výpočty provést u typu.

```cpp
static const bool is_exact = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud výpočty jsou zdarma zaokrouhlení chyby; **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Všechny předdefinované celočíselnými typy mají přesnou reprezentací pro jejich hodnoty a vrátí **false**. Znázornění s pevnou desetinnou čárkou nebo racionální bude také považován za přesný, ale je reprezentace plovoucí desetinné čárky.

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

Testuje, zda je typ odpovídá IEC 559 standardy.

```cpp
static const bool is_iec559 = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud typ splňuje standardy IEC 559; **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

IEC 559 je mezinárodní standard pro reprezentování hodnot s plovoucí desetinnou čárkou a je také označován jako IEEE 754 v USA.

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

Testuje, zda je typ má reprezentaci celého čísla.

```cpp
static const bool is_integer = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud má typ reprezentaci celé číslo; **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Všechny předdefinované celočíselnými typy mají reprezentaci celého čísla.

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

Testuje, zda **typ** má modulo reprezentace.

```cpp
static const bool is_modulo = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud má typ modulo reprezentace; **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

A modulo reprezentace je nakreslené schéma, kde jsou všechny výsledky zmenšeny modulo některá z hodnot. Všechny typy předdefinované celé číslo bez znaménka mají modulo reprezentace.

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

Testuje, zda je typ má reprezentaci podepsaný držitelem.

```cpp
static const bool is_signed = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud má typ podepsaný reprezentace; **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Člen ukládá hodnotu true pro typ, který má reprezentaci podepsaný držitelem, které platí pro všechny předdefinované typy celých čísel s plovoucí desetinnou čárkou a podepsaný držitelem.

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

Testuje, zda typ má explicitní specializace definované v šabloně třídy `numeric_limits`.

```cpp
static const bool is_specialized = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud typ má explicitní specializace definované v šabloně třídy; **false** Pokud tomu tak není.

### <a name="remarks"></a>Poznámky

Explicitní specializace definován pro šablony třídy mají všechny Skalární typy jiné než ukazatele `numeric_limits`.

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

Vrátí největší omezenou zápornou hodnotu pro typ (což je obvykle `min()` pro celočíselné typy a `-max()` pro typy s plovoucí desetinnou čárkou). Návratová hodnota má smysl Pokud `is_bounded` je **true**.

## <a name="max"></a>  numeric_limits::max

Vrátí maximální konečná hodnota typu.

```cpp
static Type max() throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální konečná hodnota typu.

### <a name="remarks"></a>Poznámky

Maximální konečná hodnota je pro typ INT_MAX **int** a FLT_MAX pro typ **float**. Návratová hodnota má smysl Pokud [is_bounded](#is_bounded) je **true**.

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

Vrátí počet desetinných míst vyžaduje, abyste měli jistotu, že dvě odlišné hodnoty typu mají odlišné reprezentace decimal.

```cpp
static int max_digits10 = 0;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet desetinných míst, které jsou potřeba, abyste měli jistotu, že dvě odlišné hodnoty typu mají odlišné reprezentace desítkové.

### <a name="remarks"></a>Poznámky

Člen ukládá počet desetinných míst vyžaduje, abyste měli jistotu, že dvě odlišné hodnoty typu mají odlišné reprezentace decimal.

## <a name="max_exponent"></a>  numeric_limits::max_exponent

Vrátí maximální kladný celočíselný exponent, který typ s plovoucí desetinnou čárkou mohou představovat jako konečnou hodnotu po její základní základ číselné soustavy je vyvolávána s cílem, které stojí za.

```cpp
static const int max_exponent = 0;
```

### <a name="return-value"></a>Návratová hodnota

Maximální integrální založené na základ číselné soustavy exponent reprezentovatelných typem.

### <a name="remarks"></a>Poznámky

Členská funkce, návratový má smysl pouze pro typy s plovoucí desetinnou čárkou. `max_exponent` Je hodnota FLT_MAX_EXP pro typ **float**.

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

Vrátí maximální kladné celočíselné exponent, který typ s plovoucí desetinnou čárkou mohou představovat jako konečnou hodnotu při vyvolání třídou base deset na výkon.

```cpp
static const int max_exponent10 = 0;
```

### <a name="return-value"></a>Návratová hodnota

Exponent reprezentovatelné maximální celočíselný základní 10 podle typu.

### <a name="remarks"></a>Poznámky

Členská funkce, návratový má smysl pouze pro typy s plovoucí desetinnou čárkou. `max_exponent` Je hodnota FLT_MAX_10 pro typ **float**.

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

Vrátí minimální Normalizovaná hodnota typu.

```cpp
static Type min() throw();
```

### <a name="return-value"></a>Návratová hodnota

Minimální Normalizovaná hodnota typu.

### <a name="remarks"></a>Poznámky

Minimální Normalizovaná hodnota je pro typ INT_MIN **int** a FLT_MIN pro typ **float**. Návratová hodnota má smysl Pokud [is_bounded](#is_bounded) je **true** nebo, pokud [is_signed –](#is_signed) je **false**.

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

Vrátí maximální negativní integrální exponent, který typ s plovoucí desetinnou čárkou mohou představovat jako konečnou hodnotu po její základní základ číselné soustavy je vyvolávána s cílem, které stojí za.

```cpp
static const int min_exponent = 0;
```

### <a name="return-value"></a>Návratová hodnota

Minimální celočíselné založené na základ číselné soustavy exponent reprezentovat typem.

### <a name="remarks"></a>Poznámky

Členská funkce má smysl pouze pro typy s plovoucí desetinnou čárkou. `min_exponent` Je hodnota FLT_MIN_EXP pro typ **float**.

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

Vrátí maximální negativní integrální exponent, který typ s plovoucí desetinnou čárkou mohou představovat jako konečnou hodnotu při vyvolání třídou base deset na výkon.

```cpp
static const int min_exponent10 = 0;
```

### <a name="return-value"></a>Návratová hodnota

Exponent reprezentovatelné minimální celočíselný základní 10 podle typu.

### <a name="remarks"></a>Poznámky

Členská funkce má smysl pouze pro typy s plovoucí desetinnou čárkou. `min_exponent10` Je hodnota FLT_MIN_10_EXP pro typ **float**.

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

Vrátí reprezentaci tichý pro typ není číslo (NAN).

```cpp
static Type quiet_NaN() throw();
```

### <a name="return-value"></a>Návratová hodnota

Reprezentace typu tichý NAN.

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

Vrátí integrální base označovány jako základ, použitý pro reprezentaci typu.

```cpp
static const int radix = 0;
```

### <a name="return-value"></a>Návratová hodnota

Integrální základ pro reprezentaci typu.

### <a name="remarks"></a>Poznámky

Základ je 2 pro předdefinované celočíselnými typy a základní třídy, do které se vyvolá exponent nebo FLT_RADIX, předdefinovaných typů s plovoucí desetinnou čárkou.

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

Vrátí maximální zaokrouhlení typ v podrobnostech o chybě.

```cpp
static Type round_error() throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální zaokrouhlení typ v podrobnostech o chybě.

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

Vrátí hodnotu, která popisuje různé metody, které můžete vybrat implementace zaokrouhlení s plovoucí desetinnou čárkou na celočíselnou hodnotu.

```cpp
static const float_round_style round_style = round_toward_zero;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota z `float_round_style` výčet, který popisuje zaokrouhlování stylu.

### <a name="remarks"></a>Poznámky

Člen ukládá hodnotu, která popisuje různé metody, které můžete vybrat implementace zaokrouhlení s plovoucí desetinnou čárkou na celočíselnou hodnotu.

Round style je obtížné zakódované v této implementaci, takže i že pokud program spustí s jiný režim zaokrouhlení, nedojde ke změně této hodnoty.

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

Pro typ, vrátí reprezentaci signalizace nečíselné (NAN).

```cpp
static Type signaling_NaN() throw();
```

### <a name="return-value"></a>Návratová hodnota

Reprezentuje signalizační NAN typu.

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

Ověřuje, zda typ můžete určit, že hodnota je příliš malá, aby reprezentovala normalizovanou hodnotu před jeho zaokrouhlení.

```cpp
static const bool tinyness_before = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud typ dokáže malý hodnoty před zaokrouhlení; **false** v případě nedostupnosti.

### <a name="remarks"></a>Poznámky

Typy, které dokáží detekovat tinyness byly zahrnuty jako možnost s IEC 559 reprezentace plovoucí desetinné čárky a jeho implementace může mít vliv na některé výsledky.

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

Testuje, zda soutisku, která informuje o aritmetické výjimky je implementován pro typ.

```cpp
static const bool traps = false;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud zachytávání je implementován pro typ; **false** nesplnění.

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

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
