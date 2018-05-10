---
title: '&lt;iomanip –&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iomanip/std::get_money
- iomanip/std::get_time
- iomanip/std::put_money
- iomanip/std::put_time
- iomanip/std::quoted
- iomanip/std::resetiosflags
- iomanip/std::setbase
- iomanip/std::setfill
- iomanip/std::setiosflags
- iomanip/std::setprecision
- iomanip/std::setw
ms.assetid: 3ddde610-70cc-4cfa-8a89-3e83d1d356a8
helpviewer_keywords:
- std::get_money [C++]
- std::get_time [C++]
- std::put_money [C++]
- std::put_time [C++]
- std::quoted [C++]
- std::resetiosflags [C++]
- std::setbase [C++]
- std::setfill [C++]
- std::setiosflags [C++]
- std::setprecision [C++]
- std::setw [C++]
ms.openlocfilehash: 5e491b9dc5035435fce16b704d28a71a1b0644de
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ltiomanipgt-functions"></a>&lt;iomanip –&gt; funkce

||||
|-|-|-|
|[get_money](#iomanip_get_money)|[get_time](#iomanip_get_time)|[put_money](#iomanip_put_money)|
|[put_time](#iomanip_put_time)|[v uvozovkách](#quoted)|[resetiosflags](#resetiosflags)|
|[setbase](#setbase)|[setfill](#setfill)|[setiosflags](#setiosflags)|
|[setprecision](#setprecision)|[setw](#setw)|

## <a name="iomanip_get_money"></a>  get_money –

Extrahuje peněžní hodnota z datového proudu požadovaného formátu a vrátí hodnotu jako parametr.

```cpp
template <class Money>
T7 get_money(Money& _Amount, bool _Intl);
```

### <a name="parameters"></a>Parametry

_Amount extrahované peněžní hodnota.

_Intl Pokud `true`, použijte Mezinárodní formát. Výchozí hodnota je `false`.

### <a name="remarks"></a>Poznámky

Manipulator vrátí objekt, když se extrahují z datového proudu `str`, chová jako `formatted input function` – členská funkce, který volá `get` pro národní prostředí omezující vlastnost `money_get` přidružené `str`pomocí `_Intl` k Uveďte mezinárodním formátu. Pokud je úspěšné, volání ukládá do `_Amount` extrahované peněžní hodnota. Vrátí manipulator `str`.

`Money` musí být typu `long double` nebo vytváření instancí z `basic_string` se stejnými parametry elementu a vlastnosti jako `str`.

## <a name="iomanip_get_time"></a>  get_time –

Extrahuje hodnotu času z datového proudu požadovaného formátu. Vrátí hodnotu jako struktura časové parametr.

```cpp
template <class Elem>
T10 put_time(struct tm *_Tptr, const Elem *_Fmt);
```

### <a name="parameters"></a>Parametry

`_Tptr` Čas ve formátu času struktura.

`_Fmt` Požadovaný formát, který se použije k získání hodnoty time.

### <a name="remarks"></a>Poznámky

Manipulator vrátí objekt, když se extrahují z datového proudu `str`, chová jako `formatted input function` – členská funkce, který volá `get` pro národní prostředí omezující vlastnost `time_get` přidružené `str`pomocí `tptr` k označení struktury čas a `fmt` označující začátek řetězec formátu ukončené hodnotou null. V případě úspěšného volání ukládá v struktura časové hodnoty přidružené žádné pole extrahované čas. Vrátí manipulator `str`.

## <a name="iomanip_put_money"></a>  put_money –

Vloží peněžní velikost požadovaného formátu do datového proudu.

```cpp
template <class Money>
T8 put_money(const Money& _Amount, bool _Intl);
```

### <a name="parameters"></a>Parametry

`_Amount` Peněžní částku vložení do datového proudu.

`_Intl` Nastavte na `true` Pokud manipulator musí mít formát mezinárodní, `false` Pokud neměli.

### <a name="return-value"></a>Návratová hodnota

Vrátí `str`.

### <a name="remarks"></a>Poznámky

Manipulator vrátí objekt, který, když vložíte do datového proudu `str`, chová jako formátovaný výstup funkci, která volá funkci člen `put` pro národní prostředí omezující vlastnost `money_put` přidružené `str`. Pokud úspěšné, volání vloží `amount` vhodně formátován pomocí `_Intl` udávajících mezinárodním formátu a `str.fill()`, jako element výplně. Vrátí manipulator `str`.

`Money` musí být typu `long double` nebo vytváření instancí z `basic_string` se stejnými parametry elementu a vlastnosti jako `str`.

## <a name="iomanip_put_time"></a>  put_time –

Zapíše hodnotu času z struktura časové do datového proudu pomocí zadaného formátu.

```cpp
template <class Elem>
T10 put_time(struct tm* _Tptr, const Elem* _Fmt);
```

### <a name="parameters"></a>Parametry

`_Tptr` Hodnota čas k zápisu do datového proudu, zadaný ve struktuře čas.

`_Fmt` Požadovaný formát pro zápis hodnoty času.

### <a name="remarks"></a>Poznámky

Manipulator vrátí objekt, který, když vložíte do datového proudu `str`, chová jako `formatted output function`. Výstup funkce volá funkci člen `put` pro národní prostředí omezující vlastnost `time_put` přidružené `str`. Používá funkci výstup `_Tptr` k označení struktury čas a `_Fmt` k označení začátku řetězce ukončené NUL formátu. V případě úspěšného volání vloží literálu text z formátovacího řetězce a převedené hodnoty z struktura časové. Vrátí manipulator `str`.

## <a name="quoted"></a>  v uvozovkách

**(Nové v C ++ 14)**  Iostream manipulator, která umožňuje pohodlný odezvy řetězců do a z datové proudy pomocí >> a << operátory.

```cpp
quoted(std::string str) // or wstring
quoted(const char* str) //or wchar_t*
quoted(std::string str, char delimiter, char escape) // or wide versions
quoted(const char* str, char delimiter, char escape) // or wide versions
```

### <a name="parameters"></a>Parametry

`str` Std::string, char *, řetězec literálu nebo nezpracovaná řetězcový literál nebo celou verzi některý z těchto (např. std::wstring, wchar_t\*).

`delimiter` Znak definované uživatelem, nebo široká znaková má používat jako oddělovač pro začátek a konec řetězce.

`escape` Znak definované uživatelem, nebo široká znaková chcete použít jako řídicí znak pro řídicí sekvence v rámci řetězce.

### <a name="remarks"></a>Poznámky

V tématu [používání operátorů Insertion a řízení formátu](../standard-library/using-insertion-operators-and-controlling-format.md).

### <a name="example"></a>Příklad

Tento příklad ukazuje, jak používat `quoted` s výchozím oddělovač a pomocí řídicí znak zúžit řetězce. Široké řetězce jsou rovnoměrně podporovány.

```cpp
#include <iostream>
#include <iomanip>
#include <sstream>

using namespace std;

void show_quoted_v_nonquoted()
{
    // Results are identical regardless of input string type:
    // string inserted { R"(This is a "sentence".)" }; // raw string literal
    // string inserted { "This is a \"sentence\"." };  // regular string literal
    const char* inserted = "This is a \"sentence\".";  // const char*
    stringstream ss, ss_quoted;
    string extracted, extracted_quoted;

    ss << inserted;
    ss_quoted << quoted(inserted);

    cout << "ss.str() is storing       : " << ss.str() << endl;
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl << endl;

    // Round-trip the strings
    ss >> extracted;
    ss_quoted >> quoted(extracted_quoted);

    cout << "After round trip: " << endl;
    cout << "Non-quoted      : " << extracted << endl;
    cout << "Quoted          : " << extracted_quoted << endl;
}

void main(int argc, char* argv[])
{
    show_quoted_v_nonquoted();

    // Keep console window open in debug mode.
    cout << endl << "Press Enter to exit" << endl;
    string input{};
    getline(cin, input);
}

/* Output:
ss.str() is storing       : This is a "sentence".
ss_quoted.str() is storing: "This is a \"sentence\"."

After round trip:
Non-quoted      : This
Quoted          : This is a "sentence".

Press Enter to exit
*/
```

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak poskytnout vlastní oddělovač nebo řídicí znak:

```cpp
#include <iostream>
#include <iomanip>
#include <sstream>

using namespace std;

void show_custom_delimiter()
{
    string inserted{ R"("This" "is" "a" "heavily-quoted" "sentence".)" };
    // string inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };
    // const char* inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };
    stringstream ss, ss_quoted;
    string extracted;

    ss_quoted << quoted(inserted, '*');
    ss << inserted;
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl;
    cout << "ss.str() is storing       : " << ss.str() << endl << endl;

    // Use the same quoted arguments as on insertion.
    ss_quoted >> quoted(extracted, '*');

    cout << "After round trip: " << endl;
    cout << "Quoted          : " << extracted << endl;

    extracted = {};
    ss >> extracted;
    cout << "Non-quoted      : " << extracted << endl << endl;
}

void show_custom_escape()
{
    string inserted{ R"(\\root\trunk\branch\nest\egg\yolk)" };
    // string inserted{ "\\\\root\\trunk\\branch\\nest\\egg\\yolk" };
    stringstream ss, ss_quoted, ss_quoted_custom;
    string extracted;

    // Use '"' as delimiter and '~' as escape character.
    ss_quoted_custom << quoted(inserted, '"', '~');
    ss_quoted << quoted(inserted);
    ss << inserted;
    cout << "ss_quoted_custom.str(): " << ss_quoted_custom.str() << endl;
    cout << "ss_quoted.str()       : " << ss_quoted.str() << endl;
    cout << "ss.str()              : " << ss.str() << endl << endl;

    // No spaces in this string, so non-quoted behaves same as quoted
    // after round-tripping.
}

void main(int argc, char* argv[])
{
    cout << "Custom delimiter:" << endl;
    show_custom_delimiter();
    cout << "Custom escape character:" << endl;
    show_custom_escape();

    // Keep console window open in debug mode.
    cout << endl << "Press Enter to exit" << endl;
    string input{};
    getline(cin, input);
}
/* Output:
Custom delimiter:
ss_quoted.str() is storing: *"This" "is" "a" "heavily-quoted" "sentence".*
ss.str() is storing       : "This" "is" "a" "heavily-quoted" "sentence".

After round trip:
Quoted          : "This" "is" "a" "heavily-quoted" "sentence".
Non-quoted      : "This"

Custom escape character:
ss_quoted_custom.str(): "\\root\trunk\branch\nest\egg\yolk"
ss_quoted.str()       : "\\\\root\\trunk\\branch\\nest\\egg\\yolk"
ss.str()              : \\root\trunk\branch\nest\egg\yolk

Press Enter to exit
*/

```

## <a name="resetiosflags"></a>  resetiosflags

Vymaže zadané příznaky.

```cpp
T1 resetiosflags(ios_base::fmtflags Mask);
```

### <a name="parameters"></a>Parametry

`Mask` Příznaky zrušte.

### <a name="return-value"></a>Návratová hodnota

Manipulator vrátí objekt, pokud z extrahovat nebo vložit do datového proudu **str**, volání **str**. [SETF](../standard-library/ios-base-class.md#setf)( `ios_base::` [fmtflags –](../standard-library/ios-base-class.md#fmtflags), _ *maska*) a vrátí **str**.

### <a name="example"></a>Příklad

V tématu [setw](../standard-library/iomanip-functions.md#setw) příklad použití `resetiosflags`.

## <a name="setbase"></a>  setbase

Nastavte základ pro celá čísla.

```cpp
T3 setbase(int _Base);
```

### <a name="parameters"></a>Parametry

`_Base` Číslo základní.

### <a name="return-value"></a>Návratová hodnota

Manipulator vrátí objekt, pokud z extrahovat nebo vložit do datového proudu **str**, volání **str**. `setf`( **maska**, [ios_base::basefield](../standard-library/ios-base-class.md#fmtflags)) a vrátí **str**. Zde **maska** je stanoven následujícím způsobem:

- Pokud _ *základní* je 8, pak **maska** je `ios_base::` [oct](../standard-library/ios-functions.md#oct).

- Pokud _ *základní* je 10 a pak maska je `ios_base::` [dec](../standard-library/ios-functions.md#dec).

- Pokud _ *základní* 16, pak je **maska** je `ios_base::` [šestnáctkových](../standard-library/ios-functions.md#hex).

- Pokud _ *základní* je jakoukoli jinou hodnotu, pak maska je `ios_base::` [fmtflags –](../standard-library/ios-base-class.md#fmtflags)(0).

### <a name="example"></a>Příklad

V tématu [setw](../standard-library/iomanip-functions.md#setw) příklad použití `setbase`.

## <a name="setfill"></a>  setfill

Nastaví znak, který se použije k vyplnění mezer v zobrazení se zarovnané vpravo.

```cpp
template <class Elem>
T4 setfill(Elem Ch);
```

### <a name="parameters"></a>Parametry

`Ch` Znak, který se použije k vyplnění mezer v zobrazení se zarovnané vpravo.

### <a name="return-value"></a>Návratová hodnota

Šablony manipulator vrátí objekt, který při vydání z nebo vložit do datového proudu **str**, volání **str**. [výplně](../standard-library/basic-ios-class.md#fill)( `Ch`) a vrátí **str**. Typ **Elem** musí být stejný jako typ elementu pro datový proud **str**.

### <a name="example"></a>Příklad

V tématu [setw](../standard-library/iomanip-functions.md#setw) příklad použití `setfill`.

## <a name="setiosflags"></a>  setiosflags

Nastaví zadaný příznaků.

```cpp
T2 setiosflags(ios_base::fmtflags Mask);
```

### <a name="parameters"></a>Parametry

`Mask` Příznaky nastavit.

### <a name="return-value"></a>Návratová hodnota

Manipulator vrátí objekt, pokud z extrahovat nebo vložit do datového proudu **str**, volání **str**. [SETF](../standard-library/ios-base-class.md#setf)(_ *maska*) a vrátí **str**.

### <a name="example"></a>Příklad

V tématu [setw](../standard-library/iomanip-functions.md#setw) příklad použití `setiosflags`.

## <a name="setprecision"></a>  setprecision

Nastaví přesnost pro hodnoty s plovoucí desetinnou čárkou.

```cpp
T5 setprecision(streamsize Prec);
```

### <a name="parameters"></a>Parametry

`Prec` Přesnost pro hodnoty s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Manipulator vrátí objekt, pokud z extrahovat nebo vložit do datového proudu **str**, volání **str**. [přesnost](../standard-library/ios-base-class.md#precision)( `Prec`) a vrátí **str**.

### <a name="example"></a>Příklad

V tématu [setw](../standard-library/iomanip-functions.md#setw) příklad použití `setprecision`.

## <a name="setw"></a>  setw

Určuje šířku pole zobrazení pro další prvek v datovém proudu.

```cpp
T6 setw(streamsize Wide);
```

### <a name="parameters"></a>Parametry

`Wide` Šířka pole zobrazení.

### <a name="return-value"></a>Návratová hodnota

Manipulator vrátí objekt, pokud z extrahovat nebo vložit do datového proudu **str**, volání **str**. [Šířka](../standard-library/ios-base-class.md#width)(_ *široké*), vrátí **str**.

### <a name="remarks"></a>Poznámky

setw Nastaví šířku pouze pro další prvek v datovém proudu a je nutné vložit před každý element, jehož šířka chcete zadat.

### <a name="example"></a>Příklad

```cpp
// iomanip_setw.cpp
// compile with: /EHsc
// Defines the entry point for the console application.
//
// Sample use of the following manipulators:
//   resetiosflags
//   setiosflags
//   setbase
//   setfill
//   setprecision
//   setw

#include <iostream>
#include <iomanip>

using namespace std;

const double   d1 = 1.23456789;
const double   d2 = 12.3456789;
const double   d3 = 123.456789;
const double   d4 = 1234.56789;
const double   d5 = 12345.6789;
const long      l1 = 16;
const long      l2 = 256;
const long      l3 = 1024;
const long      l4 = 4096;
const long      l5 = 65536;
int         base = 10;

void DisplayDefault( )
{
   cout << endl << "default display" << endl;
   cout << "d1 = " << d1 << endl;
   cout << "d2 = " << d2 << endl;
   cout << "d3 = " << d3 << endl;
   cout << "d4 = " << d4 << endl;
   cout << "d5 = " << d5 << endl;
}

void DisplayWidth( int n )
{
   cout << endl << "fixed width display set to " << n << ".\n";
   cout << "d1 = " << setw(n) << d1 << endl;
   cout << "d2 = " << setw(n) << d2 << endl;
   cout << "d3 = " << setw(n) << d3 << endl;
   cout << "d4 = " << setw(n) << d4 << endl;
   cout << "d5 = " << setw(n) << d5 << endl;
}

void DisplayLongs( )
{
   cout << setbase(10);
   cout << endl << "setbase(" << base << ")" << endl;
   cout << setbase(base);
   cout << "l1 = " << l1 << endl;
   cout << "l2 = " << l2 << endl;
   cout << "l3 = " << l3 << endl;
   cout << "l4 = " << l4 << endl;
   cout << "l5 = " << l5 << endl;
}

int main( int argc, char* argv[] )
{
   DisplayDefault( );

   cout << endl << "setprecision(" << 3 << ")" << setprecision(3);
   DisplayDefault( );

   cout << endl << "setprecision(" << 12 << ")" << setprecision(12);
   DisplayDefault( );

   cout << setiosflags(ios_base::scientific);
   cout << endl << "setiosflags(" << ios_base::scientific << ")";
   DisplayDefault( );

   cout << resetiosflags(ios_base::scientific);
   cout << endl << "resetiosflags(" << ios_base::scientific << ")";
   DisplayDefault( );

   cout << endl << "setfill('" << 'S' << "')" << setfill('S');
   DisplayWidth(15);
   DisplayDefault( );

   cout << endl << "setfill('" << ' ' << "')" << setfill(' ');
   DisplayWidth(15);
   DisplayDefault( );

   cout << endl << "setprecision(" << 8 << ")" << setprecision(8);
   DisplayWidth(10);
   DisplayDefault( );

   base = 16;
   DisplayLongs( );

   base = 8;
   DisplayLongs( );

   base = 10;
   DisplayLongs( );

   return   0;
}
```

```Output

default display
d1 = 1.23457
d2 = 12.3457
d3 = 123.457
d4 = 1234.57
d5 = 12345.7

setprecision(3)
default display
d1 = 1.23
d2 = 12.3
d3 = 123
d4 = 1.23e+003
d5 = 1.23e+004

setprecision(12)
default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setiosflags(4096)
default display
d1 = 1.234567890000e+000
d2 = 1.234567890000e+001
d3 = 1.234567890000e+002
d4 = 1.234567890000e+003
d5 = 1.234567890000e+004

resetiosflags(4096)
default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setfill('S')
fixed width display set to 15.
d1 = SSSSS1.23456789
d2 = SSSSS12.3456789
d3 = SSSSS123.456789
d4 = SSSSS1234.56789
d5 = SSSSS12345.6789

default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setfill(' ')
fixed width display set to 15.
d1 =      1.23456789
d2 =      12.3456789
d3 =      123.456789
d4 =      1234.56789
d5 =      12345.6789

default display
d1 = 1.23456789
d2 = 12.3456789
d3 = 123.456789
d4 = 1234.56789
d5 = 12345.6789

setprecision(8)
fixed width display set to 10.
d1 =  1.2345679
d2 =  12.345679
d3 =  123.45679
d4 =  1234.5679
d5 =  12345.679

default display
d1 = 1.2345679
d2 = 12.345679
d3 = 123.45679
d4 = 1234.5679
d5 = 12345.679

setbase(16)
l1 = 10
l2 = 100
l3 = 400
l4 = 1000
l5 = 10000

setbase(8)
l1 = 20
l2 = 400
l3 = 2000
l4 = 10000
l5 = 200000

setbase(10)
l1 = 16
l2 = 256
l3 = 1024
l4 = 4096
l5 = 65536
```

## <a name="see-also"></a>Viz také

[\<iomanip – >](../standard-library/iomanip.md)<br/>
