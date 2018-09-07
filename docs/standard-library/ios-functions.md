---
title: '&lt;IOS&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- xiosbase/std::defaultfloat
- xiosbase/std::boolalpha
- xiosbase/std::dec
- ios/std::fixed
- ios/std::hex
- ios/std::internal
- ios/std::left
- ios/std::noboolalpha
- ios/std::noshowbase
- ios/std::noshowpoint
- ios/std::noshowpos
- ios/std::noskipws
- ios/std::nounitbuf
- ios/std::nouppercase
- ios/std::oct
- ios/std::right
- ios/std::scientific
- ios/std::showbase
- ios/std::showpoint
- ios/std::showpos
- ios/std::skipws
- ios/std::unitbuf
- ios/std::uppercase
ms.assetid: 1382d53f-e531-4b41-adf6-6a1543512e51
helpviewer_keywords:
- std::defaultfloat [C++]
- std::boolalpha [C++]
- std::dec [C++]
- std::fixed [C++]
- std::hex [C++]
- std::internal [C++]
- std::left [C++]
- std::noboolalpha [C++]
- std::noshowbase [C++]
- std::noshowpoint [C++]
- std::noshowpos [C++]
- std::noskipws [C++]
- std::nounitbuf [C++]
- std::nouppercase [C++]
- std::oct [C++]
- std::right [C++]
- std::scientific [C++]
- std::showbase [C++]
- std::showpoint [C++]
- std::showpos [C++]
- std::skipws [C++]
- std::unitbuf [C++]
- std::uppercase [C++]
ms.openlocfilehash: a19d023400179e1e7e16541b7e3d7ef38ad963ba
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101090"
---
# <a name="ltiosgt-functions"></a>&lt;IOS&gt; funkce

||||
|-|-|-|
|[defaultfloat](#ios_defaultfloat)|[boolalpha](#boolalpha)|[DEC](#dec)|
|[Oprava](#fixed)|[Hex](#hex)|[internal](#internal)|
|[doleva](#left)|[noboolalpha](#noboolalpha)|[noshowbase](#noshowbase)|
|[noshowpoint](#noshowpoint)|[noshowpos](#noshowpos)|[noskipws](#noskipws)|
|[nounitbuf](#nounitbuf)|[nouppercase](#nouppercase)|[Říjen](#oct)|
|[doprava](#right)|[vědecké](#scientific)|[showbase](#showbase)|
|[showpoint](#showpoint)|[showpos](#showpos)|[skipws](#skipws)|
|[unitbuf](#unitbuf)|[velká písmena](#uppercase)|

## <a name="boolalpha"></a>  boolalpha

Určuje proměnné tohoto typu [bool](../cpp/bool-cpp.md) zobrazí jako **true** nebo **false** v datovém proudu.

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, proměnné typu **bool** se zobrazují jako 1 nebo 0.

`boolalpha` efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::boolalpha`) a vrátí *str*.

[noboolalpha](../standard-library/ios-functions.md#noboolalpha) obrátí účinek metody `boolalpha`.

### <a name="example"></a>Příklad

```cpp
// ios_boolalpha.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   bool b = true;
   cout << b << endl;
   boolalpha( cout );
   cout << b << endl;
   noboolalpha( cout );
   cout << b << endl;
   cout << boolalpha << b << endl;
}
```

```Output
1
true
1
true
```

## <a name="dec"></a>  DEC

Určuje, že celočíselné proměnné zobrazí v základní 10 zápisu.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Celočíselné proměnné jsou ve výchozím nastavení, zobrazí se základem 10.

`dec` efektivně volá `str.` [setf](../standard-library/ios-base-class.md#setf)( `ios_base::dec`, `ios_base::basefield`) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
// ios_dec.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 100;

   cout << i << endl;   // Default is base 10
   cout << hex << i << endl;
   dec( cout );
   cout << i << endl;
   oct( cout );
   cout << i << endl;
   cout << dec << i << endl;
}
```

```Output
100
64
100
144
100
```

## <a name="ios_defaultfloat"></a>  &lt;IOS&gt; defaultfloat

Nakonfiguruje příznaky ze `ios_base` objektu, který chcete použít výchozí zobrazovací formát pro hodnoty typu float.

```cpp
ios_base& defaultfloat(ios_base& _Iosbase);
```

### <a name="parameters"></a>Parametry

*_Iosbase*<br/>
`ios_base` Objektu.

### <a name="remarks"></a>Poznámky

Manipulátor efektivně volá _I `osbase.` [ios_base::unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`, vrátí _I `osbase`.

## <a name="fixed"></a>  Oprava

Určuje, že číslo s plovoucí desetinnou čárkou se zobrazí v oprava desítkovém zápisu.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

`fixed` je výchozí zobrazení notace pro čísla s plovoucí desetinnou čárkou. [vědecké](../standard-library/ios-functions.md#scientific) způsobí, že s plovoucí desetinnou čárkou čísla, který se má zobrazit pomocí vědeckého zápisu.

Efektivně volá manipulátor * str.*[setf](../standard-library/ios-base-class.md#setf)( `ios_base::fixed`, `ios_base::floatfield`) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
// ios_fixed.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 1.1F;

   cout << i << endl;   // fixed is the default
   cout << scientific << i << endl;
   cout.precision( 1 );
   cout << fixed << i << endl;
}
```

```Output
1.1
1.100000e+000
1.1
```

## <a name="hex"></a>  Hex

Určuje, že se zobrazí celočíselné proměnné v základní 16 zápisu.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou celočíselné proměnné zobrazí v základní 10 zápisu. [DEC](../standard-library/ios-functions.md#dec) a [oct](../standard-library/ios-functions.md#oct) také změnit způsob, jak celočíselné proměnné se zobrazí.

Efektivně volá manipulátor `str` **.** [setf](../standard-library/ios-base-class.md#setf)( `ios_base::hex`, `ios_base::basefield`) a vrátí *str*.

### <a name="example"></a>Příklad

Zobrazit [dec](../standard-library/ios-functions.md#dec) příklad, jak používat `hex`.

## <a name="internal"></a>  Interní

Způsobí, že se znaménkem číslo vlevo oprávněné a číslo, které má být zarovnané vpravo.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého *str* pochází.

### <a name="remarks"></a>Poznámky

[showpos](../standard-library/ios-functions.md#showpos) způsobí, že znak, který má být zobrazen pro kladná čísla.

Efektivně volá manipulátor `str`. [SETF](../standard-library/ios-base-class.md#setf)( [ios_base::internal](../standard-library/ios-base-class.md#fmtflags), [ios_base::adjustfield](../standard-library/ios-base-class.md#fmtflags)) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
// ios_internal.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( void )
{
   using namespace std;
   float i = -123.456F;
   cout.fill( '.' );
   cout << setw( 10 ) << i << endl;
   cout << setw( 10 ) << internal << i << endl;
}
```

```Output
..-123.456
-..123.456
```

## <a name="left"></a>  doleva

Způsobí, že text, který není stejně široká jako šířka výstupu se zobrazí v stream vyprázdnění se na levém okraji.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Efektivně volá manipulátor `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::left`, `ios_base::adjustfield`) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
// ios_left.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout.width( 20 );
   cout << f1 << endl;
   cout << left << f1 << endl;
}
```

```Output
                   5
5
```

## <a name="noboolalpha"></a>  noboolalpha

Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) jako 1 nebo 0 v datovém proudu.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `noboolalpha` je v platnosti.

`noboolalpha` efektivně volá `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::boolalpha`) a vrátí *str*.

[boolalpha](../standard-library/ios-functions.md#boolalpha) obrátí účinek metody `noboolalpha`.

### <a name="example"></a>Příklad

Zobrazit [boolalpha](../standard-library/ios-functions.md#boolalpha) pro příklad použití `noboolalpha`.

## <a name="noshowbase"></a>  noshowbase

Vypne označující konvenční základní třídy, ve kterém se zobrazí číslo.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Parametr `noshowbase` je standardně zapnutý. Použití [showbase](../standard-library/ios-functions.md#showbase) udávajících konvenční základ čísla.

Efektivně volá manipulátor `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::showbase`) a vrátí *str*.

### <a name="example"></a>Příklad

Zobrazit [showbase](../standard-library/ios-functions.md#showbase) příklad, jak používat `noshowbase`.

## <a name="noshowpoint"></a>  noshowpoint

Zobrazí pouze část celého čísla s plovoucí desetinnou čárkou čísel, jehož zlomkové části je nula.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

`noshowpoint` je ve výchozím; použít [showpoint](../standard-library/ios-functions.md#showpoint) a [přesnost](../standard-library/ios-base-class.md#precision) zobrazíte nulami za desetinnou čárkou.

Efektivně volá manipulátor `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::showpoint`) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
// ios_noshowpoint.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.000;
   cout << f1 << endl;   // noshowpoint is default
   cout.precision( 4 );
   cout << showpoint << f1 << endl;
   cout << noshowpoint << f1 << endl;
}
```

```Output
5
5.000
5
```

## <a name="noshowpos"></a>  noshowpos

Způsobí, že kladná čísla nesmí být explicitně přihlášení.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Parametr `noshowpos` je standardně zapnutý.

Efektivně volá manipulátor `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::showps`), potom se vrací *str*.

### <a name="example"></a>Příklad

Zobrazit [showpos](../standard-library/ios-functions.md#showpos) pro příklad použití `noshowpos`.

## <a name="noskipws"></a>  noskipws

Způsobit prostory přečtou vstupní datový proud.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení [skipws](../standard-library/ios-functions.md#skipws) je v platnosti. Když místo je určen pro čtení vstupního datového proudu, signalizuje konec vyrovnávací paměti.

Efektivně volá manipulátor `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::skipws`) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
// ios_noskipws.cpp
// compile with: /EHsc
#include <iostream>
#include <string>

int main() {
   using namespace std;
   string s1, s2, s3;
   cout << "Enter three strings: ";
   cin >> noskipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

## <a name="nounitbuf"></a>  nounitbuf

Způsobí, že výstupní ukládány do vyrovnávací paměti a zpracování na při vyrovnávací paměť je plná.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

[unitbuf](../standard-library/ios-functions.md#unitbuf) způsobí, že vyrovnávací paměť pro zpracování, pokud není prázdná.

Efektivně volá manipulátor `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::unitbuf`) a vrátí *str*.

## <a name="nouppercase"></a>  nouppercase

Určuje, že šestnáctkových číslic a exponent za použití vědeckého zápisu se zobrazí na malá písmena.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Efektivně volá manipulátor `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::uppercase`) a vrátí *str*.

### <a name="example"></a>Příklad

Zobrazit [velká](../standard-library/ios-functions.md#uppercase) pro příklad použití `nouppercase`.

## <a name="oct"></a>  Říjen

Určuje, že celočíselné proměnné zobrazí v základní 8 zápisu.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého *str* pochází.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou celočíselné proměnné zobrazí v základní 10 zápisu. [DEC](../standard-library/ios-functions.md#dec) a [hex](../standard-library/ios-functions.md#hex) také změnit způsob, jak celočíselné proměnné se zobrazí.

Efektivně volá manipulátor `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::oct`, `ios_base::basefield`) a vrátí *str*.

### <a name="example"></a>Příklad

Zobrazit [dec](../standard-library/ios-functions.md#dec) příklad, jak používat `oct`.

## <a name="right"></a>  doprava

Způsobí, že text, který není stejně široká jako šířka výstupu se zobrazí v vyprázdnění datový proud s na pravém okraji.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého *str* pochází.

### <a name="remarks"></a>Poznámky

[levé](../standard-library/ios-functions.md#left) také upraví zarovnání textu.

Efektivně volá manipulátor `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::right`, `ios_base::adjustfield`) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
// ios_right.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << left << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << right << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
}
```

```Output
5
                   5
5
5
                   5
                   5
```

## <a name="scientific"></a>  vědecké

Způsobí, že s plovoucí desetinnou čárkou čísla, který se má zobrazit pomocí vědeckého zápisu.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení [oprava](../standard-library/ios-functions.md#fixed) zápisu je používána pro čísla s plovoucí desetinnou čárkou.

Efektivně volá manipulátor `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::scientific`, `ios_base::floatfield`) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
// ios_scientific.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 100.23F;

   cout << i << endl;
   cout << scientific << i << endl;
}
```

```Output
100.23
1.002300e+002
```

## <a name="showbase"></a>  showbase

Označuje konvenční základní třídy, ve kterém se zobrazí číslo.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Konvenční základní číslo je možné měnit pomocí [dec](../standard-library/ios-functions.md#dec), [oct](../standard-library/ios-functions.md#oct), nebo [hex](../standard-library/ios-functions.md#hex).

Efektivně volá manipulátor `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showbase`) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
// ios_showbase.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int j = 100;

   cout << showbase << j << endl;   // dec is default
   cout << hex << j << showbase << endl;
   cout << oct << j << showbase << endl;

   cout << dec << j << noshowbase << endl;
   cout << hex << j << noshowbase << endl;
   cout << oct << j << noshowbase << endl;
}
```

```Output
100
0x64
0144
100
64
144
```

## <a name="showpoint"></a>  showpoint

Zobrazuje část celého čísla číslo s plovoucí desetinnou čárkou a číslic vpravo od desetinné čárky, i v případě, že zlomkové části je nula.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení [noshowpoint](../standard-library/ios-functions.md#noshowpoint) je v platnosti.

Efektivně volá manipulátor `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showpoint`) a vrátí *str*.

### <a name="example"></a>Příklad

Zobrazit [noshowpoint](../standard-library/ios-functions.md#noshowpoint) pro příklad použití `showpoint`.

## <a name="showpos"></a>  showpos

Způsobí, že explicitně podepsat kladná čísla.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

[noshowpos](../standard-library/ios-functions.md#noshowpos) je výchozí nastavení.

Efektivně volá manipulátor `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showpos`) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
// ios_showpos.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 1;

   cout << noshowpos << i << endl;   // noshowpos is default
   cout << showpos << i << endl;
}
```

```Output
1
+1
```

## <a name="skipws"></a>  skipws

Způsobit prostory vstupního datového proudu nelze číst.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* pochází.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `skipws` je v platnosti. [noskipws](../standard-library/ios-functions.md#noskipws) způsobí, že prostory ke čtení ze vstupního datového proudu.

Efektivně volá manipulátor `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::skipws`) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   char s1, s2, s3;
   cout << "Enter three characters: ";
   cin >> skipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

```Output

1 2 3

```

```Output

      1 2 3.1.
.2.
.3.
```

## <a name="unitbuf"></a>  unitbuf

Způsobí, že výstupní ke zpracování, pokud vyrovnávací paměť není prázdný.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého *str* pochází.

### <a name="remarks"></a>Poznámky

Všimněte si, že `endl` také vyprázdní vyrovnávací paměť.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) ve výchozím nastavení je v platnosti.

Efektivně volá manipulátor `str`.[ SETF](../standard-library/ios-base-class.md#setf)( [ios_base::unitbuf](../standard-library/ios-base-class.md#fmtflags)) a vrátí *str*.

## <a name="uppercase"></a>  velká písmena

Určuje, že šestnáctkových číslic a exponent za použití vědeckého zápisu se zobrazí na velká písmena.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Odkaz na objekt typu [ios_base –](../standard-library/ios-base-class.md), nebo typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého *str* pochází.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení [nouppercase](../standard-library/ios-functions.md#nouppercase) je v platnosti.

Efektivně volá manipulátor `str`.[ SETF](../standard-library/ios-base-class.md#setf)( [ios_base::uppercase](../standard-library/ios-base-class.md#fmtflags)) a vrátí *str*.

### <a name="example"></a>Příklad

```cpp
// ios_uppercase.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
   using namespace std;

   double i = 1.23e100;
   cout << i << endl;
   cout << uppercase << i << endl;

   int j = 10;
   cout << hex << nouppercase << j << endl;
   cout << hex << uppercase << j << endl;
}
```

```Output
1.23e+100
1.23E+100
a
A
```

## <a name="see-also"></a>Viz také:

[\<IOS >](../standard-library/ios.md)<br/>
