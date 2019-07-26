---
title: '&lt;funkce&gt; iomanip'
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
ms.openlocfilehash: 09bb043c40774b102dee023773349223a2fbb4a9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449220"
---
# <a name="ltiomanipgt-functions"></a>&lt;funkce&gt; iomanip

||||
|-|-|-|
|[get_money](#iomanip_get_money)|[get_time](#iomanip_get_time)|[put_money](#iomanip_put_money)|
|[put_time](#iomanip_put_time)|[uvedená](#quoted)|[resetiosflags](#resetiosflags)|
|[setbase](#setbase)|[setfill](#setfill)|[setiosflags](#setiosflags)|
|[setprecision](#setprecision)|[setw](#setw)|

## <a name="iomanip_get_money"></a>  get_money

Extrahuje peněžní hodnotu z datového proudu pomocí požadovaného formátu a vrátí hodnotu v parametru.

```cpp
template <class Money>
T7 get_money(Money& _Amount, bool _Intl);
```

### <a name="parameters"></a>Parametry

*_Amount*\
Extrahovaná peněžní hodnota.

*_Intl*\
Pokud **má hodnotu true**, použijte mezinárodní formát. Výchozí hodnota je **false**.

### <a name="remarks"></a>Poznámky

Manipulátor vrátí objekt `str`, který při extrakci z datového proudu chová `get` `formatted input function` jako volání členské funkce pro omezující vlastnost `money_get` národního prostředí `str`, která je přidružena k, pomocí *_Intl* pro označení mezinárodního formátu V případě úspěchu se volání uloží do *_Amount* extrahované peněžní hodnoty. Manipulátor se pak vrátí `str`.

`Money`musí být typu `long double` nebo instance `basic_string` se stejnými parametry elementu a vlastností jako `str`.

## <a name="iomanip_get_time"></a>get_time

Extrahuje časovou hodnotu z datového proudu pomocí požadovaného formátu. Vrátí hodnotu v parametru jako časovou strukturu.

```cpp
template <class Elem>
T10 put_time(struct tm *_Tptr, const Elem *_Fmt);
```

### <a name="parameters"></a>Parametry

*_Tptr*\
Čas ve formě struktury času.

*_Fmt*\
Požadovaný formát, který se má použít k získání hodnoty času.

### <a name="remarks"></a>Poznámky

Manipulátor vrátí objekt, který `str`při extrakci z datového proudu chová `formatted input function` jako volání členské funkce `get` pro omezující vlastnost `time_get` národního prostředí `str`, která je přidružena k, pomocí `tptr` Určete časovou strukturu a `fmt` určete začátek formátovacího řetězce zakončeného hodnotou null. V případě úspěchu se volání ukládají do struktury času, které jsou přidruženy k polím s extrahovanými časovými poli. Manipulátor se pak vrátí `str`.

## <a name="iomanip_put_money"></a>put_money

Vloží peněžní částku pomocí požadovaného formátu do datového proudu.

```cpp
template <class Money>
T8 put_money(const Money& _Amount, bool _Intl);
```

### <a name="parameters"></a>Parametry

*_Amount*\
Peněžní částka, která má být vložena do datového proudu.

*_Intl*\
Nastavte na **hodnotu true** , pokud má manipulátor používat mezinárodní formát, **false** , pokud by neměl.

### <a name="return-value"></a>Návratová hodnota

Vrátí `str`.

### <a name="remarks"></a>Poznámky

Manipulátor vrátí objekt, který při vložení do datového `str`proudu chová jako naformátovanou výstupní funkci, která volá členskou funkci `put` pro omezující vlastnost `money_put` národního prostředí přidruženou `str`k. V případě úspěchu bude volání vloženo `amount` vhodně formátované pomocí * _Intl` to indicate international format and `str. Fill ()`, as the fill element. The manipulator then returns `str.

`Money`musí být typu `long double` nebo instance `basic_string` se stejnými parametry elementu a vlastností jako `str`.

## <a name="iomanip_put_time"></a>put_time

Zapisuje časovou hodnotu z časové struktury do datového proudu pomocí zadaného formátu.

```cpp
template <class Elem>
T10 put_time(struct tm* _Tptr, const Elem* _Fmt);
```

### <a name="parameters"></a>Parametry

*_Tptr*\
Hodnota času pro zápis do datového proudu, která je poskytována v časové struktuře.

*_Fmt*\
Požadovaný formát pro zápis hodnoty času.

### <a name="remarks"></a>Poznámky

Manipulátor vrátí objekt, který při vložení do datového proudu `str`se chová `formatted output function`jako. Funkce Output volá členskou funkci `put` pro omezující vlastnost `time_put` národního prostředí přidruženou k `str`. Funkce Output používá *_Tptr* k označení časové struktury a *_Fmt* k indikaci začátku řetězce formátu zakončeného hodnotou null. V případě úspěchu volání vloží literálový text z řetězce formátu a převede hodnoty z časové struktury. Manipulátor se pak vrátí `str`.

## <a name="quoted"></a>uvedená

**(Novinka v c++ 14)** Iostream – manipulátor, který umožňuje pohodlné kruhové Trip řetězců do proudu a z datových proudů pomocí operátorů > > a < <.

```cpp
quoted(std::string str) // or wstring
quoted(const char* str) //or wchar_t*
quoted(std::string str, char delimiter, char escape) // or wide versions
quoted(const char* str, char delimiter, char escape) // or wide versions
```

### <a name="parameters"></a>Parametry

*str*\
Std:: String, char\*, řetězcový literál nebo nezpracovaný řetězcový literál nebo celá verze některého z těchto (například std:: wstring, wchar_t\*).

*oddělovač*\
Uživatelem zadaný znak nebo celý znak, který se použije jako oddělovač pro začátek a konec řetězce.

*před*\
Uživatelem zadaný znak nebo velký znak, který se použije jako řídicí znak řídicích sekvencí v rámci řetězce.

### <a name="remarks"></a>Poznámky

Viz téma [použití operátorů vkládání a řízení formátu](../standard-library/using-insertion-operators-and-controlling-format.md).

### <a name="example"></a>Příklad

Tento příklad ukazuje, jak použít `quoted` s výchozím oddělovačem a řídicím znakem pomocí úzkých řetězců. Stejně se podporují i řetězce s velkým množstvím.

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

## <a name="resetiosflags"></a>resetiosflags

Vymaže zadané příznaky.

```cpp
T1 resetiosflags(ios_base::fmtflags Mask);
```

### <a name="parameters"></a>Parametry

*Zrušit*\
Příznaky, které mají být vymazány.

### <a name="return-value"></a>Návratová hodnota

Manipulátor vrátí objekt, který při extrakci nebo vložení do datového proudu `str`volá **str**. [setf](../standard-library/ios-base-class.md#setf) ( `ios_base::` [fmtflags](../standard-library/ios-base-class.md#fmtflags), _ *Maska*) a pak se vrátí `str`.

### <a name="example"></a>Příklad

Příklad [](../standard-library/iomanip-functions.md#setw) použití `resetiosflags`naleznete v tématu setw.

## <a name="setbase"></a>setbase

Nastaví základ pro celá čísla.

```cpp
T3 setbase(int _Base);
```

### <a name="parameters"></a>Parametry

*_Base*\
Základ čísla

### <a name="return-value"></a>Návratová hodnota

Manipulátor vrátí objekt, který při extrakci nebo vložení do datového proudu `str`volá **str**. `setf`( **Maska**, [ios_base:: basefield](../standard-library/ios-base-class.md#fmtflags)), a pak se `str`vrátí. `mask` Tady se určuje takto:

- Pokud je *základna* _ 8, `mask` pak `ios_base::`je [ZZÚ](../standard-library/ios-functions.md#oct).

- Pokud je *základna* _ 10, pak maska `ios_base::`je [prosinec](../standard-library/ios-functions.md#dec).

- Pokud je *základna* _ 16, `mask` pak `ios_base::`je [hex](../standard-library/ios-functions.md#hex).

- Pokud je *základna* _ jakákoli jiná hodnota, pak je `ios_base::`maska [fmtflags](../standard-library/ios-base-class.md#fmtflags)(0).

### <a name="example"></a>Příklad

Příklad [](../standard-library/iomanip-functions.md#setw) použití `setbase`naleznete v tématu setw.

## <a name="setfill"></a>setfill

Nastaví znak, který se použije k vyplňování mezer v zobrazení zarovnaném vpravo.

```cpp
template <class Elem>
T4 setfill(Elem Ch);
```

### <a name="parameters"></a>Parametry

*Zvolte*\
Znak, který bude použit k vyplňování mezer v zobrazení zarovnané na pravé straně.

### <a name="return-value"></a>Návratová hodnota

Manipulátor šablony vrátí objekt, který při extrakci nebo vložení do datového proudu `str`volá **str**. [vyplnit](../standard-library/basic-ios-class.md#fill) (`Ch`) a potom vrátí `str`. Typ `Elem` musí být stejný jako typ prvku pro datový proud `str`.

### <a name="example"></a>Příklad

Příklad [](../standard-library/iomanip-functions.md#setw) použití `setfill`naleznete v tématu setw.

## <a name="setiosflags"></a>setiosflags

Nastaví zadané příznaky.

```cpp
T2 setiosflags(ios_base::fmtflags Mask);
```

### <a name="parameters"></a>Parametry

*Zrušit*\
Příznaky, které mají být nastaveny.

### <a name="return-value"></a>Návratová hodnota

Manipulátor vrátí objekt, který při extrakci nebo vložení do datového proudu `str`volá **str**. [setf](../standard-library/ios-base-class.md#setf) (_ *Maska*) a pak se vrátí `str`.

### <a name="example"></a>Příklad

Příklad [](../standard-library/iomanip-functions.md#setw) použití `setiosflags`naleznete v tématu setw.

## <a name="setprecision"></a>setprecision

Nastaví přesnost hodnot s plovoucí desetinnou čárkou.

```cpp
T5 setprecision(streamsize Prec);
```

### <a name="parameters"></a>Parametry

*Prec*\
Přesnost pro hodnoty s plovoucí desetinnou čárkou.

### <a name="return-value"></a>Návratová hodnota

Manipulátor vrátí objekt, který při extrakci nebo vložení do datového proudu `str`volá **str**. [přesnost](../standard-library/ios-base-class.md#precision) (`Prec`) a potom vrátí `str`.

### <a name="example"></a>Příklad

Příklad [](../standard-library/iomanip-functions.md#setw) použití `setprecision`naleznete v tématu setw.

## <a name="setw"></a>setw

Určuje šířku pole zobrazení pro další prvek v datovém proudu.

```cpp
T6 setw(streamsize Wide);
```

### <a name="parameters"></a>Parametry

*Rozlehlý*\
Šířka zobrazovaného pole

### <a name="return-value"></a>Návratová hodnota

Manipulátor vrátí objekt, který při extrakci nebo vložení do datového proudu `str`volá **str**. [Šířka](../standard-library/ios-base-class.md#width) (_ *Roztažitelné*), pak vrátí `str`.

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

## <a name="see-also"></a>Viz také:

[\<iomanip>](../standard-library/iomanip.md)
