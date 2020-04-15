---
title: '&lt;funkce ios&gt;'
ms.date: 11/04/2016
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
- std::hexfloat [C++]
- std::io_errc [C++]
- std::internal [C++]
- std::iostream_category [C++]
- std::is_error_code_enum [C++]
- std::left [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
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
ms.openlocfilehash: 67ac9259110abbd03fc054ea4e60ed1715030dcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375406"
---
# <a name="ltiosgt-functions"></a>&lt;funkce ios&gt;

## <a name="boolalpha"></a><a name="boolalpha"></a>boolalpha

Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) se v datovém proudu zobrazí jako **pravdivé** nebo **nepravdivé.**

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou proměnné typu **bool** zobrazeny jako 1 nebo 0.

`boolalpha`účinně volá `str.` [setf](../standard-library/ios-base-class.md#setf)( `ios_base::boolalpha`), a pak vrátí *str*.

[noboolalpha](../standard-library/ios-functions.md#noboolalpha) obrátí účinek `boolalpha`.

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

## <a name="dec"></a><a name="dec"></a>Prosince

Určuje, že se v zápisu základní 10 se zobrazí celé proměnné.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou v základu 10 zobrazeny celé proměnné.

`dec`efektivně volá `str.` [setf](../standard-library/ios-base-class.md#setf)( `ios_base::dec`, `ios_base::basefield`), a pak vrátí *str*.

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

## <a name="ltiosgt-defaultfloat"></a><a name="ios_defaultfloat"></a>&lt;ios&gt; defaultfloat

Nakonfiguruje `ios_base` příznaky objektu tak, aby používaly výchozí formát zobrazení pro plovoucí hodnoty.

```cpp
ios_base& defaultfloat(ios_base& iosbase);
```

### <a name="parameters"></a>Parametry

*_Iosbase*\
Objekt `ios_base`.

### <a name="remarks"></a>Poznámky

Manipulátor efektivně `iosbase.`volá [ios_base::unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`, pak vrátí *iosbase*.

## <a name="fixed"></a><a name="fixed"></a>Dlouhodobého

Určuje, že číslo s plovoucí desetinnou čárkou je zobrazeno v zápisu s pevnou desetinnou čárkou.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

`fixed`je výchozí zápis zobrazení pro čísla s plovoucí desetinnou tálicí. [vědecké](../standard-library/ios-functions.md#scientific) způsobí, že čísla s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou nebo lounou se zobrazí pomocí vědeckého zápisu.

Manipulátor účinně volá *str*. [setf](../standard-library/ios-base-class.md#setf) `ios_base::fixed`( `ios_base::floatfield` , ), a potom vrátí *str*.

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

## <a name="hex"></a><a name="hex"></a>Hex

Určuje, že v zápisu báze 16 se zobrazí celé proměnné.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou v zápisu základní 10 zobrazeny celé proměnné. [dec](../standard-library/ios-functions.md#dec) a [oct](../standard-library/ios-functions.md#oct) také změnit způsob zobrazení celé číslo.

Manipulátor efektivně `str`volá **.** [setf](../standard-library/ios-base-class.md#setf) `ios_base::hex`( `ios_base::basefield`, ), a potom vrátí *str*.

### <a name="example"></a>Příklad

Příklad použití [naleznete](../standard-library/ios-functions.md#dec) v dec `hex`.

## <a name="hexfloat"></a><a name="hexfloat"></a>hexfloat

```cpp
ios_base& hexfloat (ios_base& str);
```

## <a name="io_errc"></a><a name="io_errc"></a>io_errc

```cpp
enum class io_errc {
    stream = 1
};
```

## <a name="internal"></a><a name="internal"></a>Vnitřní

Způsobí, že znak čísla zůstane zarovnaný a číslo bude zarovnané doprava.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

[showpos](../standard-library/ios-functions.md#showpos) způsobí, že se znaménko zobrazí pro kladná čísla.

Manipulátor efektivně `str.`volá [setf](../standard-library/ios-base-class.md#setf)`(`[ios_base::internal](../standard-library/ios-base-class.md#fmtflags) `,` [ios_base::adjustfield](../standard-library/ios-base-class.md#fmtflags)`)`a potom vrátí *str*.

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

## <a name="is_error_code_enum"></a><a name="is_error_code_enum"></a>is_error_code_enum

```cpp
template <> struct is_error_code_enum<io_errc> : public true_type { };
```

## <a name="iostream_category"></a><a name="iostream_category"></a>iostream_category

```cpp
const error_category& iostream_category() noexcept;
```

## <a name="left"></a><a name="left"></a>Vlevo

Způsobí, že text, který není tak široký jako výstupní šířka se zobrazí v datovém proudu zarovnané s levým okrajem.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Manipulátor efektivně `str.`volá [setf](../standard-library/ios-base-class.md#setf)`(ios_base::left, ios_base::adjustfield)`a potom vrátí *str*.

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

## <a name="make_error_code"></a><a name="make_error_code"></a>make_error_code

```cpp
error_code make_error_code(io_errc e) noexcept;
```

## <a name="make_error_condition"></a><a name="make_error_condition"></a>make_error_condition

```cpp
error_condition make_error_condition(io_errc e) noexcept;
```

## <a name="noboolalpha"></a><a name="noboolalpha"></a>noboolalpha

Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) se v datovém proudu zobrazí jako 1 nebo 0.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Ve výchozím `noboolalpha` nastavení je v platnosti.

`noboolalpha`účinně volá `str.` [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::boolalpha)`, a pak vrátí *str*.

[boolalpha](../standard-library/ios-functions.md#boolalpha) obrátí účinek `noboolalpha`.

### <a name="example"></a>Příklad

Viz [boolalpha](../standard-library/ios-functions.md#boolalpha) pro příklad `noboolalpha`použití .

## <a name="noshowbase"></a><a name="noshowbase"></a>noshowbase

Vypne označení notační základny, ve které je číslo zobrazeno.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Parametr `noshowbase` je standardně zapnutý. Pomocí [showbase](../standard-library/ios-functions.md#showbase) označte notační základ čísel.

Manipulátor efektivně `str.`volá [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showbase)`a potom vrátí *str*.

### <a name="example"></a>Příklad

Viz [showbase](../standard-library/ios-functions.md#showbase) příklad použití `noshowbase`.

## <a name="noshowpoint"></a><a name="noshowpoint"></a>bez předvádění

Zobrazí pouze celou část čísel s plovoucí desetinnou tácek, jejíž zlomková část je nulová.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

`noshowpoint`je ve výchozím nastavení zapnuto; použijte [zobrazitbod](../standard-library/ios-functions.md#showpoint) a [přesnost](../standard-library/ios-base-class.md#precision) k zobrazení nul za desetinnou čárkou.

Manipulátor efektivně `str.`volá [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showpoint)`a potom vrátí *str*.

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

## <a name="noshowpos"></a><a name="noshowpos"></a>noshowpos

Způsobí, že kladná čísla nebudou explicitně podepsána.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Parametr `noshowpos` je standardně zapnutý.

Manipulátor efektivně `str.`volá [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showps)`, pak vrátí *str*.

### <a name="example"></a>Příklad

Viz [showpos](../standard-library/ios-functions.md#showpos) příklad použití `noshowpos`.

## <a name="noskipws"></a><a name="noskipws"></a>noskipws

Způsobit mezery, které mají být čteny vstupní datový proud.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je [v platnosti skipws.](../standard-library/ios-functions.md#skipws) Když je mezera čtena ve vstupním datovém proudu, signalizuje konec vyrovnávací paměti.

Manipulátor efektivně `str.`volá [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::skipws)`a potom vrátí *str*.

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

## <a name="nounitbuf"></a><a name="nounitbuf"></a>nounitbuf

Způsobí, že výstup do vyrovnávací paměti a zpracovány při zaplnění vyrovnávací paměti.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

[unitbuf](../standard-library/ios-functions.md#unitbuf) způsobí, že vyrovnávací paměť bude zpracována, pokud není prázdná.

Manipulátor efektivně `str.`volá [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::unitbuf)`a potom vrátí *str*.

## <a name="nouppercase"></a><a name="nouppercase"></a>nouppercase

Určuje, že šestnáctkové číslice a exponent ve vědeckém zápisu se zobrazí malá písmena.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Manipulátor efektivně `str.`volá [unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::uppercase)`a potom vrátí *str*.

### <a name="example"></a>Příklad

Viz [velká písmena](../standard-library/ios-functions.md#uppercase) pro `nouppercase`příklad použití .

## <a name="oct"></a><a name="oct"></a>Zzú

Určuje, že se v zápisu základní 8 zobrazí celé proměnné.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou v zápisu základní 10 zobrazeny celé proměnné. [dec](../standard-library/ios-functions.md#dec) a [hex](../standard-library/ios-functions.md#hex) také změnit způsob, jakým se zobrazí celé číslo proměnné.

Manipulátor efektivně `str.`volá [setf](../standard-library/ios-base-class.md#setf)`(ios_base::oct, ios_base::basefield)`a potom vrátí *str*.

### <a name="example"></a>Příklad

Příklad použití [naleznete](../standard-library/ios-functions.md#dec) v dec `oct`.

## <a name="right"></a><a name="right"></a>Právo

Způsobí, že text, který není tak široký jako výstupní šířka se zobrazí v datovém proudu zarovnané s pravým okrajem.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

[vlevo](../standard-library/ios-functions.md#left) také upravuje odůvodnění textu.

Manipulátor efektivně `str.`volá [setf](../standard-library/ios-base-class.md#setf)`(ios_base::right, ios_base::adjustfield)`a potom vrátí *str*.

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

## <a name="scientific"></a><a name="scientific"></a>Vědecké

Způsobí, že čísla s plovoucí desetinnou desetinnou tázání se zobrazí pomocí vědeckého zápisu.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení platí [pro](../standard-library/ios-functions.md#fixed) čísla s plovoucí desetinnou útaže.

Manipulátor efektivně `str.`volá [setf](../standard-library/ios-base-class.md#setf)`(ios_base::scientific, ios_base::floatfield)`a potom vrátí *str*.

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

## <a name="showbase"></a><a name="showbase"></a>showbase

Označuje notační základnu, ve které je číslo zobrazeno.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Notační základ čísla lze změnit pomocí [dec](../standard-library/ios-functions.md#dec), [oct](../standard-library/ios-functions.md#oct), nebo [hex](../standard-library/ios-functions.md#hex).

Manipulátor efektivně `str.`volá [setf](../standard-library/ios-base-class.md#setf)`(ios_base::showbase)`a potom vrátí *str*.

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

## <a name="showpoint"></a><a name="showpoint"></a>zobrazit

Zobrazí celou část čísla s plovoucí desetinnou čárkou a číslic napravo od desetinné čárky, i když je zlomková část nulová.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je v platnosti [noshowpoint.](../standard-library/ios-functions.md#noshowpoint)

Manipulátor efektivně `str.`volá [setf](../standard-library/ios-base-class.md#setf)`(ios_base::showpoint)`a potom vrátí *str*.

### <a name="example"></a>Příklad

Viz [noshowpoint](../standard-library/ios-functions.md#noshowpoint) pro příklad `showpoint`použití .

## <a name="showpos"></a><a name="showpos"></a>showpos

Způsobí, že kladná čísla explicitně podepsána.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

[noshowpos](../standard-library/ios-functions.md#noshowpos) je výchozí.

Manipulátor efektivně `str.`volá [setf](../standard-library/ios-base-class.md#setf)`(ios_base::showpos)`a potom vrátí *str*.

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

## <a name="skipws"></a><a name="skipws"></a>skipws

Způsobit mezery, které nemají být čteny vstupní datový proud.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Ve výchozím `skipws` nastavení je v platnosti. [noskipws](../standard-library/ios-functions.md#noskipws) způsobí, že mezery číst ze vstupního datového proudu.

Manipulátor efektivně `str.`volá [setf](../standard-library/ios-base-class.md#setf)`(ios_base::skipws)`a potom vrátí *str*.

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

```Input
1 2 3
```

```Output
Enter three characters: 1 2 3
.1.
.2.
.3.
```

## <a name="unitbuf"></a><a name="unitbuf"></a>unitbuf

Způsobí, že výstup, který má být zpracován, pokud vyrovnávací paměť není prázdná.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Všimněte `endl` si, že také vyprázdnění vyrovnávací paměti.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) je ve výchozím nastavení v platnosti.

Manipulátor efektivně `str.`volá [setf](../standard-library/ios-base-class.md#setf)`(`[ios_base::unitbuf](../standard-library/ios-base-class.md#fmtflags)`)`a potom vrátí *str*.

## <a name="uppercase"></a><a name="uppercase"></a>Velká

Určuje, že šestnáctkové číslice a exponent ve vědeckém zápisu se zobrazí velkými písmeny.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, `ios_base`který dědí od .

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze *kterého* str je odvozen.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je v platnosti [nouppercase.](../standard-library/ios-functions.md#nouppercase)

Manipulátor efektivně `str.`volá [setf](../standard-library/ios-base-class.md#setf)`(`[ios_base::velká písmena](../standard-library/ios-base-class.md#fmtflags)`)`a potom vrátí *str*.

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
