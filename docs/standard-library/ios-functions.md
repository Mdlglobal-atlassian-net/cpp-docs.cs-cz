---
title: '&lt;funkce iOS&gt;'
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
ms.openlocfilehash: c3b1e2350d0923cbfddf95492842ae126859e29f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421609"
---
# <a name="ltiosgt-functions"></a>&lt;funkce iOS&gt;

## <a name="boolalpha"></a>boolalpha

Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) se v datovém proudu zobrazují jako **true** nebo **false** .

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení jsou proměnné typu **bool** zobrazeny jako 1 nebo 0.

`boolalpha` efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)(`ios_base::boolalpha`) a potom vrátí *str*.

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

## <a name="dec"></a>18.12

Určuje, že se celočíselné proměnné zobrazují v zápisu se základem 10.

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení se proměnné typu Integer zobrazují v základu 10.

`dec` efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)(`ios_base::dec`, `ios_base::basefield`) a pak vrací *str*.

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

## <a name="ios_defaultfloat"></a>&lt;iOS&gt; defaultfloat

Nakonfiguruje příznaky objektu `ios_base` k použití výchozího formátu zobrazení pro hodnoty float.

```cpp
ios_base& defaultfloat(ios_base& iosbase);
```

### <a name="parameters"></a>Parametry

*_Iosbase*\
Objekt `ios_base`.

### <a name="remarks"></a>Poznámky

Manipulátor efektivně volá `iosbase.`[ios_base:: unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`, pak vrátí *iosbase*.

## <a name="fixed"></a>určí

Určuje, že se v zápisu s pevným počtem desetinných míst zobrazuje číslo s plovoucí desetinnou čárkou.

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

`fixed` je výchozí zobrazovaný zápis pro čísla s plovoucí desetinnou čárkou. [vědecký](../standard-library/ios-functions.md#scientific) zápis nezpůsobí zobrazení čísel s plovoucí desetinnou čárkou pomocí vědeckého zápisu.

Manipulátor efektivně volá *str*. [setf](../standard-library/ios-base-class.md#setf)(`ios_base::fixed`, `ios_base::floatfield`) a potom vrátí *str*.

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

## <a name="hex"></a>soustavy

Určuje, že se mají v zápisu se základem 16 vyskytovat celočíselné proměnné.

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení se proměnné typu Integer zobrazují v zápisu se základem 10. [prosinec](../standard-library/ios-functions.md#dec) a [ZZÚ](../standard-library/ios-functions.md#oct) také mění způsob zobrazení celočíselných proměnných.

Manipulátor efektivně volá `str` **.** [setf](../standard-library/ios-base-class.md#setf)(`ios_base::hex`, `ios_base::basefield`) a potom vrátí *str*.

### <a name="example"></a>Příklad

Příklad použití `hex`naleznete v části [dec](../standard-library/ios-functions.md#dec) .

## <a name="hexfloat"></a>hexfloat

```cpp
ios_base& hexfloat (ios_base& str);
```

## <a name="io_errc"></a>io_errc

```cpp
enum class io_errc {
    stream = 1
};
```

## <a name="internal"></a>vnitřních

Způsobí zarovnání zarovnaného čísla na levou a číslo, které se má zarovnat vpravo.

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

[showpos](../standard-library/ios-functions.md#showpos) způsobí, že se znaménko zobrazí pro kladná čísla.

Manipulátor efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base:: Internal](../standard-library/ios-base-class.md#fmtflags)`, `[ios_base:: adjustfield](../standard-library/ios-base-class.md#fmtflags)`)`a vrátí *str*.

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

## <a name="is_error_code_enum"></a>is_error_code_enum

```cpp
template <> struct is_error_code_enum<io_errc> : public true_type { };
```

## <a name="iostream_category"></a>iostream_category

```cpp
const error_category& iostream_category() noexcept;
```

## <a name="left"></a>zbývá

Způsobí, že text, který není stejně široké jako šířka výstupu, se zobrazí v vyprázdnění streamu s levým okrajem.

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Manipulátor efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::left, ios_base::adjustfield)`a vrací *str*.

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

## <a name="make_error_code"></a>make_error_code

```cpp
error_code make_error_code(io_errc e) noexcept;
```

## <a name="make_error_condition"></a>make_error_condition

```cpp
error_condition make_error_condition(io_errc e) noexcept;
```

## <a name="noboolalpha"></a>noboolalpha

Určuje, že proměnné typu [bool](../cpp/bool-cpp.md) se v datovém proudu zobrazují jako 1 nebo 0.

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je `noboolalpha` aktivní.

`noboolalpha` efektivně volá `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::boolalpha)`a pak vrací *str*.

[boolalpha](../standard-library/ios-functions.md#boolalpha) obrátí účinek `noboolalpha`.

### <a name="example"></a>Příklad

Příklad použití `noboolalpha`naleznete v tématu [boolalpha](../standard-library/ios-functions.md#boolalpha) .

## <a name="noshowbase"></a>noshowbase

Vypne označení základu zápisu, ve kterém se zobrazuje číslo.

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Parametr `noshowbase` je standardně zapnutý. Použijte [showbase](../standard-library/ios-functions.md#showbase) k označení základu zápisu čísel.

Manipulátor efektivně volá `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showbase)`a vrací *str*.

### <a name="example"></a>Příklad

Příklad použití `noshowbase`naleznete v tématu [showbase](../standard-library/ios-functions.md#showbase) .

## <a name="noshowpoint"></a>noshowpoint

Zobrazí pouze část čísla s plovoucí desetinnou čárkou, jejichž Zlomková část je nulová.

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

`noshowpoint` je ve výchozím nastavení zapnutá. použijte [showpoint](../standard-library/ios-functions.md#showpoint) a [Precision](../standard-library/ios-base-class.md#precision) pro zobrazení nul za desetinnou čárkou.

Manipulátor efektivně volá `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showpoint)`a vrací *str*.

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

## <a name="noshowpos"></a>noshowpos

Způsobí, že kladná čísla nebudou explicitně podepsána.

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Parametr `noshowpos` je standardně zapnutý.

Manipulátor efektivně volá `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showps)`a vrátí *str*.

### <a name="example"></a>Příklad

Příklad použití `noshowpos`naleznete v tématu [showpos](../standard-library/ios-functions.md#showpos) .

## <a name="noskipws"></a>noskipws

Způsobí, že vstupní datový proud přečte mezery.

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je [skipws](../standard-library/ios-functions.md#skipws) platný. Když je ve vstupním streamu čtena mezera, signalizuje konec vyrovnávací paměti.

Manipulátor efektivně volá `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::skipws)`a vrací *str*.

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

## <a name="nounitbuf"></a>nounitbuf

Způsobí, že výstup bude uložen do vyrovnávací paměti a zpracován, když je vyrovnávací paměť plná.

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

[unitbuf](../standard-library/ios-functions.md#unitbuf) způsobí, že se vyrovnávací paměť zpracuje, když není prázdná.

Manipulátor efektivně volá `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::unitbuf)`a vrací *str*.

## <a name="nouppercase"></a>Velká písmena

Určuje, že hexadecimální číslice a exponent v matematickém zápisu se zobrazí malými písmeny.

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Manipulátor efektivně volá `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::uppercase)`a vrací *str*.

### <a name="example"></a>Příklad

Příklad použití `nouppercase`naleznete v části [velká písmena](../standard-library/ios-functions.md#uppercase) .

## <a name="oct"></a>mořská

Určuje, že se v zápisu se základem 8 vyskytují celočíselné proměnné.

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení se proměnné typu Integer zobrazují v zápisu se základem 10. [dec](../standard-library/ios-functions.md#dec) a [hex](../standard-library/ios-functions.md#hex) také mění způsob zobrazení celočíselných proměnných.

Manipulátor efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::oct, ios_base::basefield)`a vrací *str*.

### <a name="example"></a>Příklad

Příklad použití `oct`naleznete v části [dec](../standard-library/ios-functions.md#dec) .

## <a name="right"></a>Kliknutím

Způsobí, že text, který není stejně široké jako šířka výstupu, se zobrazí v vyprázdnění streamu s pravým okrajem.

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

[šipka doleva](../standard-library/ios-functions.md#left) také upraví zdůvodnění textu.

Manipulátor efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::right, ios_base::adjustfield)`a vrací *str*.

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

## <a name="scientific"></a>odbornou

Způsobí, že se čísla s plovoucí desetinnou čárkou budou zobrazovat pomocí vědeckého zápisu.

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je [pevný](../standard-library/ios-functions.md#fixed) zápis platný pro čísla s plovoucí desetinnou čárkou.

Manipulátor efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::scientific, ios_base::floatfield)`a vrací *str*.

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

## <a name="showbase"></a>showbase

Určuje notaci základ, ve kterém je zobrazeno číslo.

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Notaci základu čísla se dá změnit s [prosinec](../standard-library/ios-functions.md#dec), [ZZÚ](../standard-library/ios-functions.md#oct)nebo [hex](../standard-library/ios-functions.md#hex).

Manipulátor efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::showbase)`a vrací *str*.

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

## <a name="showpoint"></a>showpoint

Zobrazí část čísla s plovoucí desetinnou čárkou a číslicemi vpravo od desetinné čárky, a to i v případě, že desetinná část je nula.

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je [noshowpoint](../standard-library/ios-functions.md#noshowpoint) platný.

Manipulátor efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::showpoint)`a vrací *str*.

### <a name="example"></a>Příklad

Příklad použití `showpoint`naleznete v tématu [noshowpoint](../standard-library/ios-functions.md#noshowpoint) .

## <a name="showpos"></a>showpos

Způsobí, že kladné číslo bude explicitně podepsáno.

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Výchozí hodnota je [noshowpos](../standard-library/ios-functions.md#noshowpos) .

Manipulátor efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::showpos)`a vrací *str*.

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

## <a name="skipws"></a>skipws

Způsobí, že vstupní datový proud nebude číst mezery.

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je `skipws` aktivní. [noskipws](../standard-library/ios-functions.md#noskipws) způsobí čtení mezer ze vstupního datového proudu.

Manipulátor efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::skipws)`a vrací *str*.

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

## <a name="unitbuf"></a>unitbuf

Způsobí, že výstup bude zpracován, pokud není vyrovnávací paměť prázdná.

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Všimněte si, že `endl` také vyprázdní vyrovnávací paměť.

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) je ve výchozím nastavení platný.

Manipulátor efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base:: unitbuf](../standard-library/ios-base-class.md#fmtflags)`)`a vrací *str*.

## <a name="uppercase"></a>všechna

Určuje, že hexadecimální číslice a exponent v matematickém zápisu se zobrazí velkými písmeny.

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>Parametry

\ *str*
Odkaz na objekt typu [ios_base](../standard-library/ios-base-class.md)nebo na typ, který dědí z `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt, ze kterého je odvozena *str* .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je to, že platí [velká písmena](../standard-library/ios-functions.md#nouppercase) .

Manipulátor efektivně volá `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base:: velká písmena](../standard-library/ios-base-class.md#fmtflags)`)`a vrací *str*.

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
