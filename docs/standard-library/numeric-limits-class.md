---
title: numeric_limits – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 5373bd6a99605f5a63fb6aa2ed6de50c12b1c8f1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876023"
---
# <a name="numeric_limits-class"></a>numeric_limits – třída

Šablona třídy popisuje aritmetické vlastnosti předdefinovaných číselných typů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
    class numeric_limits
```

### <a name="parameters"></a>Parametry

*Zadejte*\
Základní datový typ prvku, jehož vlastnosti jsou testovány nebo dotazovány nebo nastaveny. *Typ* může být také deklarovaný jako **const**, **volatile**nebo **const volatile**.

## <a name="remarks"></a>Poznámky

Záhlaví Definuje explicitní specializace pro typy **wchar_t**, **bool**, **char**, **signed char**, **unsigned char**, **short**, **unsigned short**, **int**, **unsigned int**, **Long**, unsigned **Long,** **float**, **Double**, **Long Double**, **Long Long**, Long **Long,** Long, **char16_t**a **char32_t**. Pro tyto explicitní specializace má člen [numeric_limits:: is_specialized](#is_specialized) **hodnotu true**a všechny relevantní členy mají smysluplné hodnoty. Program může poskytovat další explicitní specializace. Většina členských funkcí třídy popisuje nebo testuje možné implementace **typu float**.

Pro libovolnou specializaci nemají žádné členy smysluplné hodnoty. Členský objekt, který nemá smysluplnou hodnotu, ukládá hodnotu nula (nebo **false**) a členskou funkci, která nevrací smysluplnou hodnotu, vrátí `Type(0)`.

## <a name="static-functions-and-constants"></a>Statické funkce a konstanty

|||
|-|-|
|[denorm_min](#denorm_min)|Vrátí nejmenší nenulovou hodnotu nenulové normalizované hodnoty.|
|[znak](#digits)|Vrátí počet číslic základu, které typ může představovat bez ztráty přesnosti.|
|[digits10](#digits10)|Vrátí počet desítkových číslic, které typ může představovat bez ztráty přesnosti.|
|[kurzív](#epsilon)|Vrátí rozdíl mezi 1 a nejmenší hodnotou větší než 1, který může datový typ představovat.|
|[has_denorm](#has_denorm)|Testuje, zda typ umožňuje denormalizované hodnoty.|
|[has_denorm_loss](#has_denorm_loss)|Testuje, zda je zjištěna ztráta přesnosti jako Denormalizovaná ztráta, nikoli jako nepřesný výsledek.|
|[has_infinity](#has_infinity)|Testuje, zda typ obsahuje reprezentace pro kladné nekonečno.|
|[has_quiet_NaN](#has_quiet_nan)|Testuje, zda typ obsahuje reprezentace pro tiché číslo (NAN), které nesignalizuje.|
|[has_signaling_NaN](#has_signaling_nan)|Testuje, zda typ obsahuje reprezentace pro signalizaci, že není číslo (NAN).|
|[konečný](#infinity)|Reprezentace pro kladné nekonečno pro typ, je-li k dispozici.|
|[is_bounded](#is_bounded)|Testuje, zda sada hodnot, které typ může představovat, je konečná.|
|[is_exact](#is_exact)|Testuje, zda jsou výpočty prováděné u typu bez chyb zaokrouhlení.|
|[is_iec559](#is_iec559)|Testuje, jestli typ vyhovuje standardům IEC 559.|
|[is_integer](#is_integer)|Testuje, zda typ obsahuje celočíselnou reprezentaci.|
|[is_modulo](#is_modulo)|Testuje, zda má typ reprezentaci modulo.|
|[is_signed](#is_signed)|Testuje, zda má typ podepsaná reprezentace.|
|[is_specialized](#is_specialized)|Testuje, zda má typ explicitní specializaci definovanou v šabloně třídy `numeric_limits`.|
|[menší](#lowest)|Vrátí největší omezenou zápornou hodnotu.|
|[počet](#max)|Vrátí maximální konečnou hodnotu pro typ.|
|[max_digits10](#max_digits10)|Vrátí počet desítkových číslic, které jsou požadovány pro zajištění, že dvě odlišné hodnoty typu mají rozdílové reprezentace v desítkové soustavě.|
|[max_exponent](#max_exponent)|Vrátí maximální kladný celočíselný exponent, který typ s plovoucí desetinnou čárkou může představovat jako konečnou hodnotu, když je k tomuto výkonu vyvolána základní hodnota základu.|
|[max_exponent10](#max_exponent10)|Vrátí maximální kladný celočíselný exponent, který typ s plovoucí desetinnou čárkou může představovat jako konečnou hodnotu, když se k tomuto výkonu vyvolá základ 10.|
|[dlouhé](#min)|Vrátí minimální normalizovanou hodnotu pro typ.|
|[min_exponent](#min_exponent)|Vrátí maximální záporný celočíselný exponent, který typ s plovoucí desetinnou čárkou může představovat jako konečnou hodnotu, když je k tomuto výkonu vyvolána základní hodnota základu.|
|[min_exponent10](#min_exponent10)|Vrátí maximální záporný celočíselný exponent, který typ s plovoucí desetinnou čárkou může představovat jako konečnou hodnotu, když se k tomuto výkonu vyvolá základ 10.|
|[quiet_NaN](#quiet_nan)|Vrací reprezentace ticha není číslo (NAN) pro typ.|
|[Číselná](#radix)|Vrací základ integrálu, označovaný jako základ, který se používá pro reprezentaci typu.|
|[round_error](#round_error)|Vrátí maximální chybu zaokrouhlení pro daný typ.|
|[round_style](#round_style)|Vrací hodnotu, která popisuje různé metody, které může implementace zvolit pro zaokrouhlování hodnoty s plovoucí desetinnou čárkou na celočíselnou hodnotu.|
|[signaling_NaN](#signaling_nan)|Vrací reprezentace signálu, který není číslo (NAN) pro typ.|
|[tinyness_before](#tinyness_before)|Testuje, zda typ může určit, že hodnota je příliš malá, aby představovala jako normalizovanou hodnotu před zaokrouhlením.|
|[chytávání](#traps)|Testuje, zda je pro typ implementováno soutisk sestav pro aritmetické výjimky.|

### <a name="denorm_min"></a>denorm_min

Vrátí nejmenší nenulovou hodnotu nenulové normalizované hodnoty.

```cpp
static constexpr Type denorm_min() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Nejmenší nenulová hodnota denormalizované hodnoty.

#### <a name="remarks"></a>Poznámky

**typ long double** je stejný jako **typ Double** pro C++ kompilátor.

Funkce vrátí minimální hodnotu pro typ, který je stejný jako [minimum](#min) , pokud [has_denorm](#has_denorm) není rovna `denorm_present`.

#### <a name="example"></a>Příklad

```cpp
// numeric_limits_denorm_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The smallest nonzero denormalized value" << endl
        << "for float objects is: "
        << numeric_limits<float>::denorm_min( ) << endl;
   cout << "The smallest nonzero denormalized value" << endl
        << "for double objects is: "
        << numeric_limits<double>::denorm_min( ) << endl;
   cout << "The smallest nonzero denormalized value" << endl
        << "for long double objects is: "
        << numeric_limits<long double>::denorm_min( ) << endl;

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

### <a name="digits"></a>znak

Vrátí počet číslic základu, které typ může představovat bez ztráty přesnosti.

```cpp
static constexpr int digits = 0;
```

#### <a name="return-value"></a>Návratová hodnota

Počet číslic základu, který typ může představovat bez ztráty přesnosti.

#### <a name="remarks"></a>Poznámky

Člen ukládá počet číslic základu, které typ může představovat bez změny, což je počet bitů jiných než jakýkoli bit znaménka pro předdefinovaný celočíselný typ nebo počet číslic mantisy pro předdefinovaný typ s plovoucí desetinnou čárkou.

#### <a name="example"></a>Příklad

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

### <a name="digits10"></a>digits10

Vrátí počet desítkových číslic, které typ může představovat bez ztráty přesnosti.

```cpp
static constexpr int digits10 = 0;
```

#### <a name="return-value"></a>Návratová hodnota

Počet desetinných míst, který typ může představovat bez ztráty přesnosti.

#### <a name="example"></a>Příklad

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

### <a name="epsilon"></a>kurzív

Funkce vrátí rozdíl mezi 1 a nejmenší hodnotou větší než 1, který je reprezentovatelné pro datový typ.

```cpp
static constexpr Type epsilon() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi 1 a nejmenší hodnotou větší než 1, který je reprezentovatelné pro datový typ.

#### <a name="remarks"></a>Poznámky

Hodnota je FLT_EPSILON pro typ **float**. `epsilon` pro typ je nejmenší kladné číslo s plovoucí desetinnou čárkou *n* tak, že *n* + `epsilon` + *n* je reprezentovatelné.

#### <a name="example"></a>Příklad

```cpp
// numeric_limits_epsilon.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for float objects is: "
        << numeric_limits<float>::epsilon( ) << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for double objects is: "
        << numeric_limits<double>::epsilon( ) << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for long double objects is: "
        << numeric_limits<long double>::epsilon( ) << endl;
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

### <a name="has_denorm"></a>has_denorm

Testuje, zda typ umožňuje denormalizované hodnoty.

```cpp
static constexpr float_denorm_style has_denorm = denorm_absent;
```

#### <a name="return-value"></a>Návratová hodnota

Hodnota výčtu typu **const**`float_denorm_style`, která označuje, jestli typ povoluje denormalizované hodnoty.

#### <a name="remarks"></a>Poznámky

Člen ukládá `denorm_present` pro typ s plovoucí desetinnou čárkou, který má denormalizované hodnoty, a efektivně proměnlivý počet bitů exponentů.

#### <a name="example"></a>Příklad

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

### <a name="has_denorm_loss"></a>has_denorm_loss

Testuje, zda je zjištěna ztráta přesnosti jako Denormalizovaná ztráta, nikoli jako nepřesný výsledek.

```cpp
static constexpr bool has_denorm_loss = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud je ztráta přesnosti zjištěna jako Denormalizovaná ztráta; **false** , pokud není.

#### <a name="remarks"></a>Poznámky

Člen ukládá hodnotu true pro typ, který určuje, zda hodnota ztratí přesnost, protože je doručena jako denormalizovaný výsledek (příliš malý pro reprezentaci jako normalizovaná hodnota) nebo, protože je nepřesný (není totéž jako výsledek nepodléhá omezením exponentu. Rozsah a přesnost), možnost s IEC 559 s plovoucí desetinnou čárkou reprezentace, která může ovlivnit některé výsledky.

#### <a name="example"></a>Příklad

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

### <a name="has_infinity"></a>has_infinity

Testuje, zda typ obsahuje reprezentace pro kladné nekonečno.

```cpp
static constexpr bool has_infinity = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud má typ reprezentaci pro kladné nekonečno; **false** , pokud není.

#### <a name="remarks"></a>Poznámky

Člen vrátí **hodnotu true** , [](#is_iec559) Pokud is_iec559 **hodnotu true**.

#### <a name="example"></a>Příklad

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

### <a name="has_quiet_nan"></a>has_quiet_NaN

Testuje, zda typ obsahuje reprezentace pro tiché číslo (NAN), což je nesignalizace.

```cpp
static constexpr bool has_quiet_NaN = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud **typ** má reprezentaci pro tiché NaN; **false** , pokud není.

#### <a name="remarks"></a>Poznámky

Tiché NAN je kódování pro číslo, které nesignalizuje jeho přítomnost ve výrazu. Návratová hodnota má **hodnotu true** , pokud [is_iec559](#is_iec559) hodnotu true.

#### <a name="example"></a>Příklad

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

### <a name="has_signaling_nan"></a>has_signaling_NaN

Testuje, zda typ obsahuje reprezentace pro signalizaci, že není číslo (NAN).

```cpp
static constexpr bool has_signaling_NaN = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud typ obsahuje reprezentace pro signál NaN; **false** , pokud není.

#### <a name="remarks"></a>Poznámky

Signalizace NAN je kódování pro číslo, které signalizuje jeho přítomnost ve výrazu. Návratová hodnota má **hodnotu true** , pokud [is_iec559](#is_iec559) hodnotu true.

#### <a name="example"></a>Příklad

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

### <a name="infinity"></a>konečný

Reprezentace kladného nekonečna pro typ, je-li k dispozici.

```cpp
static constexpr Type infinity() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Reprezentace kladného nekonečna pro typ, je-li k dispozici.

#### <a name="remarks"></a>Poznámky

Návratová hodnota má smysl pouze v případě, že je [has_infinity](#has_infinity) **true**.

#### <a name="example"></a>Příklad

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

### <a name="is_bounded"></a>is_bounded

Testuje, zda sada hodnot, které typ může představovat, je konečná.

```cpp
static constexpr bool is_bounded = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud má typ ohraničené sady reprezentovatelné hodnoty; **false** , pokud není.

#### <a name="remarks"></a>Poznámky

Všechny předdefinované typy mají ohraničenou sadu reprezentovatelné hodnoty a vracejí **hodnotu true**.

#### <a name="example"></a>Příklad

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

### <a name="is_exact"></a>is_exact

Testuje, zda jsou výpočty prováděné u typu bez chyb zaokrouhlení.

```cpp
static constexpr bool is_exact = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou výpočty bez chyb zaokrouhlení; **false** , pokud není.

#### <a name="remarks"></a>Poznámky

Všechny předdefinované celočíselné typy mají přesné reprezentace jejich hodnot a vracejí **hodnotu false**. Pevná čárka nebo racionální reprezentace je také považována za přesný, ale reprezentace s plovoucí desetinnou čárkou není.

#### <a name="example"></a>Příklad

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

### <a name="is_iec559"></a>is_iec559

Testuje, jestli typ vyhovuje standardům IEC 559.

```cpp
static constexpr bool is_iec559 = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud typ vyhovuje standardům IEC 559; **false** , pokud není.

#### <a name="remarks"></a>Poznámky

IEC 559 je mezinárodní standard pro reprezentaci hodnot s plovoucí desetinnou čárkou, který se také označuje jako IEEE 754 v USA.

#### <a name="example"></a>Příklad

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

### <a name="is_integer"></a>is_integer

Testuje, zda typ obsahuje celočíselnou reprezentaci.

```cpp
static constexpr bool is_integer = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud typ obsahuje celočíselné vyjádření; **false** , pokud není.

#### <a name="remarks"></a>Poznámky

Všechny předdefinované celočíselné typy mají celočíselnou reprezentaci.

#### <a name="example"></a>Příklad

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

### <a name="is_modulo"></a>is_modulo

Testuje, zda má **typ** reprezentaci modulo.

```cpp
static constexpr bool is_modulo = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud typ má reprezentaci modulo; **false** , pokud není.

#### <a name="remarks"></a>Poznámky

Reprezentace modulo je reprezentace, kde jsou všechny výsledky zmenšeny na více než více než jednou. Všechny předdefinované typy unsigned integer mají reprezentaci modulo.

#### <a name="example"></a>Příklad

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

### <a name="is_signed"></a>is_signed

Testuje, zda má typ podepsaná reprezentace.

```cpp
static constexpr bool is_signed = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud má typ podepsané reprezentace; **false** , pokud není.

#### <a name="remarks"></a>Poznámky

Člen ukládá hodnotu true pro typ, který má podepsané reprezentace, což je případ všech předdefinovaných typů s plovoucí desetinnou čárkou a podepsaných celých čísel.

#### <a name="example"></a>Příklad

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

### <a name="is_specialized"></a>is_specialized

Testuje, zda má typ explicitní specializaci definovanou v šabloně třídy `numeric_limits`.

```cpp
static constexpr bool is_specialized = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud má typ explicitní specializaci definovanou v šabloně třídy; **false** , pokud není.

#### <a name="remarks"></a>Poznámky

Všechny skalární typy jiné než ukazatelé mají explicitní specializaci definovanou pro šablonu třídy `numeric_limits`.

#### <a name="example"></a>Příklad

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

### <a name="lowest"></a>menší

Vrátí největší omezenou zápornou hodnotu.

```cpp
static constexpr Type lowest() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Vrátí největší omezenou zápornou hodnotu.

#### <a name="remarks"></a>Poznámky

Vrátí nejpornou konečnou hodnotu pro typ (což je obvykle `min()` pro celočíselné typy a `-max()` pro typy s plovoucí desetinnou čárkou). Návratová hodnota má smysl, pokud `is_bounded` má **hodnotu true**.

### <a name="max"></a>počet

Vrátí maximální konečnou hodnotu pro typ.

```cpp
static constexpr Type max() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Maximální konečná hodnota pro typ.

#### <a name="remarks"></a>Poznámky

Maximální konečná hodnota je INT_MAX pro typ **int** a FLT_MAX pro typ **float**. Návratová hodnota má smysl, pokud [is_bounded](#is_bounded) má **hodnotu true**.

#### <a name="example"></a>Příklad

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

### <a name="max_digits10"></a>max_digits10

Vrátí počet desítkových číslic, které jsou požadovány pro zajištění, že dvě odlišné hodnoty typu mají rozdílové reprezentace v desítkové soustavě.

```cpp
static constexpr int max_digits10 = 0;
```

#### <a name="return-value"></a>Návratová hodnota

Vrátí počet desítkových číslic, které jsou požadovány, aby bylo zajištěno, že dvě odlišné hodnoty typu mají rozdílná reprezentace v desítkovém zobrazení.

#### <a name="remarks"></a>Poznámky

Člen ukládá počet desítkových číslic, které jsou požadovány pro zajištění, že dvě odlišné hodnoty typu mají rozdílové reprezentace v desítkové soustavě.

### <a name="max_exponent"></a>max_exponent

Vrátí maximální kladný celočíselný exponent, který typ s plovoucí desetinnou čárkou může představovat jako konečnou hodnotu, když je k tomuto výkonu vyvolána základní hodnota základu.

```cpp
static constexpr int max_exponent = 0;
```

#### <a name="return-value"></a>Návratová hodnota

Maximální celočíselný exponent na základě základu, který je reprezentován typem.

#### <a name="remarks"></a>Poznámky

Vrácená členská funkce je smysluplná jenom u typů s plovoucí desetinnou čárkou. `max_exponent` je hodnota FLT_MAX_EXP pro typ **float**.

#### <a name="example"></a>Příklad

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

### <a name="max_exponent10"></a>max_exponent10

Vrátí maximální kladný celočíselný exponent, který typ s plovoucí desetinnou čárkou může představovat jako konečnou hodnotu, když se k tomuto výkonu vyvolá základ 10.

```cpp
static constexpr int max_exponent10 = 0;
```

#### <a name="return-value"></a>Návratová hodnota

Maximální celočíselná hodnota 10 exponent, kterou typ představuje.

#### <a name="remarks"></a>Poznámky

Vrácená členská funkce je smysluplná jenom u typů s plovoucí desetinnou čárkou. `max_exponent` je hodnota FLT_MAX_10 pro typ **float**.

#### <a name="example"></a>Příklad

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

### <a name="min"></a>dlouhé

Vrátí minimální normalizovanou hodnotu pro typ.

```cpp
static constexpr Type min() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Minimální normalizovaná hodnota pro typ.

#### <a name="remarks"></a>Poznámky

Minimální normalizovaná hodnota je INT_MIN pro typ **int** a FLT_MIN pro typ **float**. Návratová hodnota má smysl, pokud [is_bounded](#is_bounded) má **hodnotu true** , nebo pokud [is_signed](#is_signed) **hodnotu false**.

#### <a name="example"></a>Příklad

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

### <a name="min_exponent"></a>min_exponent

Vrátí maximální záporný celočíselný exponent, který typ s plovoucí desetinnou čárkou může představovat jako konečnou hodnotu, když je k tomuto výkonu vyvolána základní hodnota základu.

```cpp
static constexpr int min_exponent = 0;
```

#### <a name="return-value"></a>Návratová hodnota

Minimální celočíselná exponent na základě základu, který je reprezentován typem.

#### <a name="remarks"></a>Poznámky

Členská funkce je smysluplná jenom u typů s plovoucí desetinnou čárkou. `min_exponent` je hodnota FLT_MIN_EXP pro typ **float**.

#### <a name="example"></a>Příklad

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

### <a name="min_exponent10"></a>min_exponent10

Vrátí maximální záporný celočíselný exponent, který typ s plovoucí desetinnou čárkou může představovat jako konečnou hodnotu, když se k tomuto výkonu vyvolá základ 10.

```cpp
static constexpr int min_exponent10 = 0;
```

#### <a name="return-value"></a>Návratová hodnota

Minimální celočíselný základ 10 exponent, který je reprezentován typem.

#### <a name="remarks"></a>Poznámky

Členská funkce je smysluplná jenom u typů s plovoucí desetinnou čárkou. `min_exponent10` je hodnota FLT_MIN_10_EXP pro typ **float**.

#### <a name="example"></a>Příklad

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

### <a name="quiet_nan"></a>quiet_NaN

Vrací reprezentace ticha není číslo (NAN) pro typ.

```cpp
static constexpr Type quiet_NaN() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Reprezentace tichého NAN pro typ.

#### <a name="remarks"></a>Poznámky

Návratová hodnota má smysl pouze v případě, že je [has_quiet_NaN](#has_quiet_nan) **true**.

#### <a name="example"></a>Příklad

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

### <a name="radix"></a>Číselná

Vrací základ integrálu, označovaný jako základ, který se používá pro reprezentaci typu.

```cpp
static constexpr int radix = 0;
```

#### <a name="return-value"></a>Návratová hodnota

Základ integrálu pro reprezentaci typu.

#### <a name="remarks"></a>Poznámky

Základem je 2 pro předdefinované celočíselné typy a základ, na který je vyvoláno exponent, nebo FLT_RADIX pro předdefinované typy s plovoucí desetinnou čárkou.

#### <a name="example"></a>Příklad

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

### <a name="round_error"></a>round_error

Vrátí maximální chybu zaokrouhlení pro daný typ.

```cpp
static constexpr Type round_error() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Maximální chyba zaokrouhlení pro typ

#### <a name="example"></a>Příklad

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

### <a name="round_style"></a>round_style

Vrací hodnotu, která popisuje různé metody, které může implementace zvolit pro zaokrouhlování hodnoty s plovoucí desetinnou čárkou na celočíselnou hodnotu.

```cpp
static constexpr float_round_style round_style = round_toward_zero;
```

#### <a name="return-value"></a>Návratová hodnota

Hodnota z výčtu `float_round_style`, která popisuje styl zaokrouhlení.

#### <a name="remarks"></a>Poznámky

Člen ukládá hodnotu, která popisuje různé metody, které může implementace zvolit pro zaokrouhlování hodnoty s plovoucí desetinnou čárkou na celočíselnou hodnotu.

Kruhový styl je v této implementaci pevně kódovaný, takže i když se program spustí s jiným režimem zaokrouhlování, tato hodnota se nezmění.

#### <a name="example"></a>Příklad

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

### <a name="signaling_nan"></a>signaling_NaN

Vrací reprezentace signálu, který není číslo (NAN) pro typ.

```cpp
static constexpr Type signaling_NaN() throw();
```

#### <a name="return-value"></a>Návratová hodnota

Reprezentace NAN signálu pro typ.

#### <a name="remarks"></a>Poznámky

Návratová hodnota má smysl pouze v případě, že je [has_signaling_NaN](#has_signaling_nan) **true**.

#### <a name="example"></a>Příklad

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

### <a name="tinyness_before"></a>tinyness_before

Testuje, zda typ může určit, že hodnota je příliš malá, aby představovala jako normalizovanou hodnotu před zaokrouhlením.

```cpp
static constexpr bool tinyness_before = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud typ může detekovat malé hodnoty před zaokrouhlením; **false** , pokud nemůže.

#### <a name="remarks"></a>Poznámky

Typy, které mohou detekovat nenáročné, byly zahrnuty jako možnost s IEC 559. reprezentace s plovoucí desetinnou čárkou a její implementace může ovlivnit některé výsledky.

#### <a name="example"></a>Příklad

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

### <a name="traps"></a>chytávání

Testuje, zda je pro typ implementováno soutisk sestav pro aritmetické výjimky.

```cpp
static constexpr bool traps = false;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud je pro typ implementováno vytváření přesahů. **false** , pokud není.

#### <a name="example"></a>Příklad

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
