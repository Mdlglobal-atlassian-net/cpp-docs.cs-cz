---
title: '&lt;IOS&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 10
manager: ghogen
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
ms.openlocfilehash: 390cbdc8d0df98e631765aea8cbc3bbc7ac161f3
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltiosgt-functions"></a>&lt;IOS&gt; funkce

||||
|-|-|-|
|[defaultfloat –](#ios_defaultfloat)|[boolalpha](#boolalpha)|[DEC](#dec)|
|[Pevná](#fixed)|[Hex](#hex)|[internal](#internal)|
|[Vlevo](#left)|[noboolalpha](#noboolalpha)|[noshowbase](#noshowbase)|
|[noshowpoint](#noshowpoint)|[noshowpos](#noshowpos)|[noskipws](#noskipws)|
|[nounitbuf](#nounitbuf)|[nouppercase](#nouppercase)|[OCT](#oct)|
|[Vpravo](#right)|[Scientific](#scientific)|[showbase](#showbase)|
|[showpoint](#showpoint)|[showpos](#showpos)|[skipws](#skipws)|
|[unitbuf](#unitbuf)|[Velká písmena](#uppercase)|

## <a name="boolalpha"></a>  boolalpha

Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) zobrazí jako **true** nebo **false** v datovém proudu.

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, proměnné typu `bool` zobrazují jako 1 nebo 0.

`boolalpha` efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::boolalpha`) a vrátí `str`.

[noboolalpha](../standard-library/ios-functions.md#noboolalpha) obrátí účinku `boolalpha`.

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

Určuje celé číslo proměnné, které se zobrazují v základní 10 zápisu.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou proměnné celé číslo zobrazené na základní 10.

**DEC** efektivně volá `str.` [setf](../standard-library/ios-base-class.md#setf)( `ios_base::dec` **, ios_base::basefield**) a vrátí `str`.

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

## <a name="ios_defaultfloat"></a>  &lt;IOS&gt; defaultfloat –

Nakonfiguruje příznaky z `ios_base` objekt, který chcete použít výchozí zobrazení formát pro hodnoty typu float.

```cpp
ios_base& defaultfloat(ios_base& _Iosbase);
```

### <a name="parameters"></a>Parametry

`_Iosbase` `ios_base` Objektu.

### <a name="remarks"></a>Poznámky

Manipulator efektivně volá potvrzuj_i `osbase.` [ios_base::unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`, vrátí potvrzuj_i `osbase`.

## <a name="fixed"></a>  Pevná

Určuje, že číslo s plovoucí desetinnou čárkou zobrazí notaci decimal.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

**pevné** je zápis výchozí zobrazení pro čísla s plovoucí desetinnou čárkou. [Scientific](../standard-library/ios-functions.md#scientific) způsobí, že s plovoucí desetinnou čárkou čísla, který se má zobrazit pomocí exponenciální notace.

Manipulator efektivně volá * str.*[setf](../standard-library/ios-base-class.md#setf)( `ios_base::fixed`, **ios_base::floatfield**) a vrátí `str`.

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

Určuje, že proměnné celé číslo se zobrazí v základní 16 zápis.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení zobrazí se základní 10 notaci proměnné celé číslo. [DEC](../standard-library/ios-functions.md#dec) a [oct](../standard-library/ios-functions.md#oct) také změnit proměnné celé číslo způsob, jak se zobrazují.

Manipulator efektivně volá `str` **.** [setf](../standard-library/ios-base-class.md#setf)( `ios_base::hex`, **ios_base::basefield**) a vrátí `str`.

### <a name="example"></a>Příklad

V tématu [dec](../standard-library/ios-functions.md#dec) příklad použití **šestnáctkových**.

## <a name="internal"></a>  Interní

Způsobí, že přihlášení počet zbývajících oprávněné a číslo, které má být zarovnání doprava.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého `str` je odvozený.

### <a name="remarks"></a>Poznámky

[showpos](../standard-library/ios-functions.md#showpos) způsobí, že přihlášení k zobrazení kladná čísla.

Manipulator efektivně volá `str`. [SETF](../standard-library/ios-base-class.md#setf)( [ios_base::internal](../standard-library/ios-base-class.md#fmtflags), [ios_base::adjustfield](../standard-library/ios-base-class.md#fmtflags)) a vrátí `str`.

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

## <a name="left"></a>  Vlevo

Způsobí, že text, který není široká jako šířka výstupu se objeví v vyprázdnění datového proudu s levým okrajem.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Manipulator efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::left`, **ios_base::adjustfield**) a vrátí `str`.

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

Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) zobrazí jako 1 nebo 0 v datovém proudu.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `noboolalpha` je v platnosti.

`noboolalpha` efektivně volá `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::boolalpha`) a vrátí `str`.

[boolalpha](../standard-library/ios-functions.md#boolalpha) obrátí účinku `noboolalpha`.

### <a name="example"></a>Příklad

V tématu [boolalpha](../standard-library/ios-functions.md#boolalpha) příklad použití `noboolalpha`.

## <a name="noshowbase"></a>  noshowbase

Vypne označující konvenční základní, ve kterém se zobrazí číslo.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Parametr `noshowbase` je standardně zapnutý. Použití [showbase](../standard-library/ios-functions.md#showbase) udávajících konvenční základní čísel.

Manipulator efektivně volá `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::showbase`) a vrátí `str`.

### <a name="example"></a>Příklad

V tématu [showbase](../standard-library/ios-functions.md#showbase) příklad použití `noshowbase`.

## <a name="noshowpoint"></a>  noshowpoint

Zobrazí jenom část celé číslo s plovoucí desetinnou čárkou čísel, jejichž zlomkové části je nulová.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

`noshowpoint` je ve výchozím; použít [showpoint](../standard-library/ios-functions.md#showpoint) a [přesnost](../standard-library/ios-base-class.md#precision) k zobrazení nul za desetinnou čárkou.

Manipulator efektivně volá `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::showpoint`) a vrátí `str`.

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

Způsobí, že nebyla výslovně podepsané kladná čísla.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Parametr `noshowpos` je standardně zapnutý.

Manipulator efektivně volá `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::showps`), vrátí `str`.

### <a name="example"></a>Příklad

V tématu [showpos](../standard-library/ios-functions.md#showpos) příklad použití `noshowpos`.

## <a name="noskipws"></a>  noskipws

Způsobit prostory a číst vstupního datového proudu.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení [skipws](../standard-library/ios-functions.md#skipws) je v platnosti. Když mezeru se čtou v vstupního datového proudu, signalizuje konce vyrovnávací paměti.

Manipulator efektivně volá `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::skipws`) a vrátí `str`.

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

Příčiny výstupní vyrovnávací paměti a zpracování na při zaplnění vyrovnávací paměti.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

[unitbuf](../standard-library/ios-functions.md#unitbuf) způsobí, že vyrovnávací paměť na zpracování, pokud není prázdná.

Manipulator efektivně volá `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::unitbuf`) a vrátí `str`.

## <a name="nouppercase"></a>  nouppercase

Určuje, že šestnáctkové číslice a exponent v vědecká notace se objeví na malá písmena.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Manipulator efektivně volá `str`.[ unsetf –](../standard-library/ios-base-class.md#unsetf)( `ios_base::uppercase`) a vrátí `str`.

### <a name="example"></a>Příklad

V tématu [velká](../standard-library/ios-functions.md#uppercase) příklad použití `nouppercase`.

## <a name="oct"></a>  OCT

Určuje celé číslo proměnné, které se zobrazují v základní 8 zápisu.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého *str* je odvozený.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení zobrazí se základní 10 notaci proměnné celé číslo. [DEC](../standard-library/ios-functions.md#dec) a [šestnáctkových](../standard-library/ios-functions.md#hex) také změnit proměnné celé číslo způsob, jak se zobrazují.

Manipulator efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::oct`, `ios_base::basefield`) a vrátí `str`.

### <a name="example"></a>Příklad

V tématu [dec](../standard-library/ios-functions.md#dec) příklad použití **oct**.

## <a name="right"></a>  Vpravo

Způsobí, že text, který není široká jako šířka výstupu se objeví v vyprázdnění datového proudu s pravým okrajem.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého *str* je odvozený.

### <a name="remarks"></a>Poznámky

[levé](../standard-library/ios-functions.md#left) také upraví zarovnání do bloku textu.

Manipulator efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::right`, `ios_base::adjustfield`) a vrátí `str`.

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

## <a name="scientific"></a>  Scientific

Čísla s plovoucí desetinnou čárkou příčiny zobrazená pomocí exponenciální notace.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení [pevné](../standard-library/ios-functions.md#fixed) zápisu je používána pro čísla s plovoucí desetinnou čárkou.

Manipulator efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::scientific`, `ios_base::floatfield`) a vrátí `str`.

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

Označuje konvenční základní, ve kterém se zobrazí číslo.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Konvenční základ číslo může být změněna pomocí [dec](../standard-library/ios-functions.md#dec), [oct](../standard-library/ios-functions.md#oct), nebo [šestnáctkových](../standard-library/ios-functions.md#hex).

Manipulator efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showbase`) a vrátí `str`.

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

Zobrazí celé číslo část číslo s plovoucí desetinnou čárkou a číslic vpravo od desetinné čárky, i v případě, že zlomkové části je nulová.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení [noshowpoint](../standard-library/ios-functions.md#noshowpoint) je v platnosti.

Manipulator efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showpoint`) a vrátí `str`.

### <a name="example"></a>Příklad

V tématu [noshowpoint](../standard-library/ios-functions.md#noshowpoint) příklad použití `showpoint`.

## <a name="showpos"></a>  showpos

Způsobí, že kladná čísla explicitně podepsat.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

[noshowpos](../standard-library/ios-functions.md#noshowpos) je výchozí.

Manipulator efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::showpos`) a vrátí `str`.

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

Způsobit prostory a vstupní datový proud nelze číst.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze které _ *Str* je odvozený.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `skipws` je v platnosti. [noskipws](../standard-library/ios-functions.md#noskipws) způsobí, že prostory čtení ze vstupního datového proudu.

Manipulator efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( `ios_base::skipws`) a vrátí `str`.

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

Příčiny výstupní mají být zpracovány, pokud vyrovnávací paměť není prázdný.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého `str` je odvozený.

### <a name="remarks"></a>Poznámky

Všimněte si, že `endl` také vyprázdní vyrovnávací paměť.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) ve výchozím nastavení je v platnosti.

Manipulator efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( [ios_base::unitbuf](../standard-library/ios-base-class.md#fmtflags)) a vrátí `str`.

## <a name="uppercase"></a>  Velká písmena

Určuje, že šestnáctkové číslice a exponent v vědecká notace se objeví na velká písmena.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

`str` Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md), nebo typu, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého `str` je odvozený.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení [nouppercase](../standard-library/ios-functions.md#nouppercase) je v platnosti.

Manipulator efektivně volá `str`.[ SETF](../standard-library/ios-base-class.md#setf)( [ios_base::uppercase](../standard-library/ios-base-class.md#fmtflags)) a vrátí `str`.

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

## <a name="see-also"></a>Viz také

[\<IOS >](../standard-library/ios.md)<br/>
