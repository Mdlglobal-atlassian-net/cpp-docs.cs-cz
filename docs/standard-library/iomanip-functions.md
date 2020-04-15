---
title: '&lt;funkce iomanip&gt;'
ms.date: 11/04/2016
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
ms.openlocfilehash: 0ed59a94c6b1c7d962b566e2a6b186ffb617a26a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375427"
---
# <a name="ltiomanipgt-functions"></a>&lt;funkce iomanip&gt;

||||
|-|-|-|
|[get_money](#iomanip_get_money)|[get_time](#iomanip_get_time)|[put_money](#iomanip_put_money)|
|[put_time](#iomanip_put_time)|[Citoval](#quoted)|[resetiosflags](#resetiosflags)|
|[setbase](#setbase)|[setfill](#setfill)|[setiosflags](#setiosflags)|
|[setpřesnost](#setprecision)|[setw](#setw)|

## <a name="get_money"></a><a name="iomanip_get_money"></a>get_money

Extrahuje peněžní hodnotu z datového proudu pomocí požadovaného formátu a vrátí hodnotu v parametru.

```cpp
template <class Money>
T7 get_money(Money& amount, bool use_intl);
```

### <a name="parameters"></a>Parametry

*Částka*\
Extrahovaná peněžní hodnota.

*use_intl*\
Pokud **true**, použijte mezinárodní formát. Výchozí hodnota je **false** (nepravda).

### <a name="remarks"></a>Poznámky

Manipulátor vrátí objekt, který při `str`extrahování z `formatted input function` datového proudu `get` , se chová `money_get` jako, `str`který volá členskou funkci pro omezující tvář národního prostředí přidružené s , pomocí *use_intl* k označení mezinárodního formátu. Pokud je úspěšná, volání ukládá v *množství* extrahované peněžní hodnoty. Manipulátor `str`pak vrátí .

`Money`musí být `long double` typu nebo konkretizace `basic_string` se stejnými parametry prvku a vlastností jako `str`.

## <a name="get_time"></a><a name="iomanip_get_time"></a>get_time

Extrahuje hodnotu času z datového proudu pomocí požadovaného formátu. Vrátí hodnotu v parametru jako strukturu času.

```cpp
template <class Elem>
T10 put_time(struct tm *time_ptr, const Elem *time_format);
```

### <a name="parameters"></a>Parametry

*time_ptr*\
Čas ve formě časové struktury.

*time_format*\
Požadovaný formát, který chcete použít k získání časové hodnoty.

### <a name="remarks"></a>Poznámky

Manipulátor vrátí objekt, který při `str`extrahování z `formatted input function` datového proudu `get` , se chová `time_get` jako, `str`který `tptr` volá členská `fmt` funkce pro omezující tvář národního prostředí přidružené s , pomocí k označení časové struktury a k označení začátku null ukončený formátovací řetězec. Pokud je volání úspěšné, volání ukládá do časové struktury hodnoty přidružené k libovolným extrahovaným časovým polím. Manipulátor `str`pak vrátí .

## <a name="put_money"></a><a name="iomanip_put_money"></a>put_money

Vloží peněžní částku pomocí požadovaného formátu do datového proudu.

```cpp
template <class Money>
T8 put_money(const Money& amount, bool use_intl);
```

### <a name="parameters"></a>Parametry

*Částka*\
Peněžní částka vložit do datového proudu.

*use_intl*\
Nastavte na **hodnotu true,** pokud manipulátor by měl používat mezinárodní formát, **false,** pokud by neměl.

### <a name="return-value"></a>Návratová hodnota

Vrací objekt `str`.

### <a name="remarks"></a>Poznámky

Manipulátor vrátí objekt, který se `str`při vložení do datového proudu chová jako `put` formátovaná výstupní funkce, která volá členovou funkci pro omezující tvář národního prostředí `money_put` přidruženou k aplikaci `str`. V případě úspěchu `amount` se hovor vloží vhodně formátované, `str.fill()`pomocí *use_intl* k označení mezinárodního formátu a , jako prvek výplně. Manipulátor `str`pak vrátí .

`Money`musí být `long double` typu nebo konkretizace `basic_string` se stejnými parametry prvku a vlastností jako `str`.

## <a name="put_time"></a><a name="iomanip_put_time"></a>put_time

Zapíše hodnotu času z časové struktury do datového proudu pomocí zadaného formátu.

```cpp
template <class Elem>
T10 put_time(struct tm* time_ptr, const Elem* time_format);
```

### <a name="parameters"></a>Parametry

*time_ptr*\
Hodnota času pro zápis do datového proudu, poskytované ve struktuře času.

*time_format*\
Požadovaný formát pro zápis hodnoty času.

### <a name="remarks"></a>Poznámky

Manipulátor vrátí objekt, který se `str`při vložení do `formatted output function`datového proudu chová jako . Výstupní funkce volá členská funkce `put` pro `time_put` omezující `str`tvář národního prostředí přidruženého k aplikaci . Výstupní funkce používá *time_ptr* k označení časové struktury a *time_format* k označení začátku formátu s nulovým zakončeným řetězcem. Pokud je volání úspěšné, vloží literál z formátovacího řetězce a převedené hodnoty ze struktury času. Manipulátor `str`pak vrátí .

## <a name="quoted"></a><a name="quoted"></a>Citoval

**(Novinka v C++14)** Manipulátor iostream, který umožňuje pohodlné kruhové zakopnutí řetězců do a z datových proudů pomocí operátorů >> a << .

```cpp
quoted(std::string str) // or wstring
quoted(const char* str) //or wchar_t*
quoted(std::string str, char delimiter, char escape) // or wide versions
quoted(const char* str, char delimiter, char escape) // or wide versions
```

### <a name="parameters"></a>Parametry

*Str*\
Std::string, char\*, literál řetězce nebo nezpracovaný řetězec literálu nebo širokou verzi některého z\*nich (např. std::wstring, wchar_t).

*Oddělovač*\
Uživatelem zadaný znak nebo široký znak, který se má použít jako oddělovač pro začátek a konec řetězce.

*Uniknout*\
Uživatelem zadaný znak nebo široký znak, který se má použít jako řídicí znak pro řídicí sekvence v řetězci.

### <a name="remarks"></a>Poznámky

Viz [Použití operátorů vkládání a řízení formátu](../standard-library/using-insertion-operators-and-controlling-format.md).

### <a name="example"></a>Příklad

Tento příklad ukazuje, `quoted` jak používat s výchozím oddělovačem a řídicíznak pomocí úzkých řetězců. Široké řetězce jsou stejně podporovány.

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

int main(int argc, char* argv[])
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

int main(int argc, char* argv[])
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

## <a name="resetiosflags"></a><a name="resetiosflags"></a>resetiosflags

Vymaže zadané příznaky.

```cpp
T1 resetiosflags(ios_base::fmtflags mask);
```

### <a name="parameters"></a>Parametry

*Maska*\
Vlajky k vymazání.

### <a name="return-value"></a>Návratová hodnota

Manipulátor vrátí objekt, který při extrahování `str`z `str.`nebo vložené do datového `str`proudu , volá [setf](../standard-library/ios-base-class.md#setf)`(ios_base::`[fmtflags](../standard-library/ios-base-class.md#fmtflags)`, mask)`a potom vrátí .

### <a name="example"></a>Příklad

Viz [setw](../standard-library/iomanip-functions.md#setw) příklad použití `resetiosflags`.

## <a name="setbase"></a><a name="setbase"></a>setbase

Nastavte základnu pro celá čísla.

```cpp
T3 setbase(int base);
```

### <a name="parameters"></a>Parametry

*Základní*\
Základ čísla.

### <a name="return-value"></a>Návratová hodnota

Manipulátor vrátí objekt, který při extrahování `str`z `str.setf(mask,` datového proudu nebo vložení `str`do datového proudu zavolá [ios_base::basefield](../standard-library/ios-base-class.md#fmtflags)`)`a vrátí . Zde `mask` se stanoví takto:

- Pokud *základna* je `mask` `ios_base::`8, pak je [říjen](../standard-library/ios-functions.md#oct).

- Pokud je *základna* 10, pak maska je `ios_base::` [dec](../standard-library/ios-functions.md#dec).

- Pokud *základna* je `mask` 16, pak je `ios_base::` [hex](../standard-library/ios-functions.md#hex).

- Pokud *base* je jiná hodnota, `ios_base::`pak maska je [fmtflags](../standard-library/ios-base-class.md#fmtflags)`(0)`.

### <a name="example"></a>Příklad

Viz [setw](../standard-library/iomanip-functions.md#setw) příklad použití `setbase`.

## <a name="setfill"></a><a name="setfill"></a>setfill

Nastaví znak, který bude použit k vyplnění mezer v zobrazení zarovnaném doprava.

```cpp
template <class Elem>
T4 setfill(Elem Ch);
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, který bude použit k vyplnění mezer v zobrazení zarovnaném do pravého bloku.

### <a name="return-value"></a>Návratová hodnota

Manipulátor šablony vrátí objekt, který při extrahování `str`z `str.`datového proudu nebo vložení do datového proudu volá [fill](../standard-library/basic-ios-class.md#fill)`(Ch)`a poté vrátí `str`. Typ `Elem` musí být stejný jako typ prvku `str`pro datový proud .

### <a name="example"></a>Příklad

Viz [setw](../standard-library/iomanip-functions.md#setw) příklad použití `setfill`.

## <a name="setiosflags"></a><a name="setiosflags"></a>setiosflags

Nastaví zadané příznaky.

```cpp
T2 setiosflags(ios_base::fmtflags mask);
```

### <a name="parameters"></a>Parametry

*Maska*\
Příznaky nastavit.

### <a name="return-value"></a>Návratová hodnota

Manipulátor vrátí objekt, který při extrahování `str`z `str.`datového proudu nebo `str`vložení do datového proudu volá [setf](../standard-library/ios-base-class.md#setf)`(mask)`a potom vrátí .

### <a name="example"></a>Příklad

Viz [setw](../standard-library/iomanip-functions.md#setw) příklad použití `setiosflags`.

## <a name="setprecision"></a><a name="setprecision"></a>setpřesnost

Nastaví přesnost pro hodnoty s plovoucí desetinnou tálicí.

```cpp
T5 setprecision(streamsize Prec);
```

### <a name="parameters"></a>Parametry

*Prec*\
Přesnost pro hodnoty s plovoucí desetinnou desetinnou desetinnou a střední.

### <a name="return-value"></a>Návratová hodnota

Manipulátor vrátí objekt, který při extrahování `str`z `str.`datového proudu `str`nebo vložení do datového proudu volá [přesnost](../standard-library/ios-base-class.md#precision)`(Prec)`a poté vrátí .

### <a name="example"></a>Příklad

Viz [setw](../standard-library/iomanip-functions.md#setw) příklad použití `setprecision`.

## <a name="setw"></a><a name="setw"></a>setw

Určuje šířku zobrazovaného pole pro další prvek v datovém proudu.

```cpp
T6 setw(streamsize Wide);
```

### <a name="parameters"></a>Parametry

*Široký*\
Šířka zobrazovaného pole.

### <a name="return-value"></a>Návratová hodnota

Manipulátor vrátí objekt, který při extrahování `str`z `str.`datového proudu nebo vložení do datového proudu volá [šířku](../standard-library/ios-base-class.md#width)`(Wide)`a poté vrátí `str`.

### <a name="remarks"></a>Poznámky

setw nastaví šířku pouze pro další prvek v datovém proudu a musí být vložen před každý prvek, jehož šířku chcete zadat.

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

[\<iomanip>](../standard-library/iomanip.md)
