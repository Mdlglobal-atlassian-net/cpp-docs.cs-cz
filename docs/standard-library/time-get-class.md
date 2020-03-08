---
title: time_get – třída
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get
- locale/std::time_get::char_type
- locale/std::time_get::iter_type
- locale/std::time_get::date_order
- locale/std::time_get::do_date_order
- locale/std::time_get::do_get
- locale/std::time_get::do_get_date
- locale/std::time_get::do_get_monthname
- locale/std::time_get::do_get_time
- locale/std::time_get::do_get_weekday
- locale/std::time_get::do_get_year
- locale/std::time_get::get
- locale/std::time_get::get_date
- locale/std::time_get::get_monthname
- locale/std::time_get::get_time
- locale/std::time_get::get_weekday
- locale/std::time_get::get_year
helpviewer_keywords:
- std::time_get [C++]
- std::time_get [C++], char_type
- std::time_get [C++], iter_type
- std::time_get [C++], date_order
- std::time_get [C++], do_date_order
- std::time_get [C++], do_get
- std::time_get [C++], do_get_date
- std::time_get [C++], do_get_monthname
- std::time_get [C++], do_get_time
- std::time_get [C++], do_get_weekday
- std::time_get [C++], do_get_year
- std::time_get [C++], get
- std::time_get [C++], get_date
- std::time_get [C++], get_monthname
- std::time_get [C++], get_time
- std::time_get [C++], get_weekday
- std::time_get [C++], get_year
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
ms.openlocfilehash: e605423b829305bd1e7bde8be4fdbf312c8ce3c1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876188"
---
# <a name="time_get-class"></a>time_get – třída

Šablona třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu sekvencí typu `CharType` na hodnoty času.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ používaný v rámci programu ke kódování znaků.

*InputIterator*\
Iterátor, ze kterého se čtou hodnoty času.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v ID jedinečnou kladnou hodnotu **.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[time_get](#time_get)|Konstruktor pro objekty typu `time_get`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje vstupní iterátor.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[date_order](#date_order)|Vrátí pořadí data používané omezující vlastností.|
|[do_date_order](#do_date_order)|Chráněná virtuální členská funkce, která je volána k vrácení pořadí data používaného omezující vlastností.|
|[do_get](#do_get)|Čte a převede data znaků na hodnotu času.|
|[do_get_date](#do_get_date)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako data vytvořeného specifikátorem `x` pro `strftime`.|
|[do_get_monthname](#do_get_monthname)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu měsíce.|
|[do_get_time](#do_get_time)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako data vytvořeného specifikátorem `X` pro `strftime`.|
|[do_get_weekday](#do_get_weekday)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu týdnu.|
|[do_get_year](#do_get_year)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu roku.|
|[get](#get)|Čte ze zdroje data znaků a převede je na čas, který je uložen v časové struktuře.|
|[get_date](#get_date)|Analyzuje řetězec jako datum vytvořené specifikátorem `x` pro `strftime`.|
|[get_monthname](#get_monthname)|Analyzuje řetězec jako název měsíce.|
|[get_time](#get_time)|Analyzuje řetězec jako datum vytvořené specifikátorem `X` pro `strftime`.|
|[get_weekday](#get_weekday)|Analyzuje řetězec jako název dne v týdnu.|
|[get_year](#get_year)|Analyzuje řetězec jako název roku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Obor názvů:** std

## <a name="char_type"></a>time_get:: char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="date_order"></a>time_get::d ate_order

Vrátí pořadí data používané omezující vlastností.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>Návratová hodnota

Pořadí data používané omezující vlastností.

### <a name="remarks"></a>Poznámky

Členská funkce vrací [do_date_order](#do_date_order).

### <a name="example"></a>Příklad

```cpp
// time_get_date_order.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
void po( char *p )
{
   locale loc( p );

   time_get <char>::dateorder order = use_facet <time_get <char> >( loc ).date_order ( );
   cout << loc.name( );
   switch (order){
      case time_base::dmy: cout << "(day, month, year)" << endl;
      break;
      case time_base::mdy: cout << "(month, day, year)" << endl;
      break;
      case time_base::ydm: cout << "(year, day, month)" << endl;
      break;
      case time_base::ymd: cout << "(year, month, day)"<< endl;
      break;
      case time_base::no_order: cout << "(no_order)"<< endl;
      break;
   }
}

int main( )
{
   po( "C" );
   po( "german" );
   po( "English_Britain" );
}
```

```Output
C(month, day, year)
German_Germany.1252(day, month, year)
English_United Kingdom.1252(day, month, year)
```

## <a name="do_date_order"></a>time_get::d o_date_order

Chráněná virtuální členská funkce, která je volána k vrácení pořadí data používaného omezující vlastností.

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>Návratová hodnota

Pořadí data používané omezující vlastností.

### <a name="remarks"></a>Poznámky

Členská funkce Protected vrací hodnotu typu **time_base::d ateorder**, která popisuje pořadí, ve kterém jsou komponenty data porovnány [do_get_date](#do_get_date). V této implementaci je hodnota **time_base:: MDY**, která odpovídá datům ve formátu 2. prosince 1979.

### <a name="example"></a>Příklad

Podívejte se na příklad [date_order](#date_order), který volá `do_date_order`.

## <a name="do_get"></a>time_get::d o_get

Čte a převede data znaků na hodnotu času. Přijímá jeden specifikátor převodu a modifikátor.

```cpp
virtual iter_type
    do_get(
iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor, který označuje začátek sekvence, která se má převést.

*poslední*\
Vstupní iterátor, který označuje konec sekvence.

*iosbase*\
Objekt Stream.

\ *stavu*
Pole v iosbase, kde jsou pro indikaci chyb nastaveny odpovídající prvky maskování.

*ptm*\
Ukazatel na časovou strukturu, ve které má být čas uložen.

*fmt*\
Znak specifikátoru převodu.

\ *mod*
Volitelný znak modifikátoru.

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor, který určí první převedený prvek. V `state` se nezdařily chyby převodu `ios_base::failbit` a jako *první*se vrátí.

### <a name="remarks"></a>Poznámky

Virtuální členská funkce převede a přeskočí jeden nebo více vstupních prvků v rozsahu [`first`, `last`) k určení hodnot uložených v jednom nebo více členech `*pt`. V `state` se nezdařily chyby převodu `ios_base::failbit` a jako *první*se vrátí. V opačném případě funkce vrátí iterátor označující první převedený prvek.

Specifikátory převodu jsou:

`'a'` nebo `'A'` – se chovají stejně jako [time_get:: get_weekday](#get_weekday).

`'b'`, `'B'`nebo `'h'` – se chovají stejně jako [time_get:: get_monthname](#get_monthname).

`'c'` – se chová stejně jako `"%b %d %H : %M : %S %Y"`.

`'C'` – převede vstupní pole Decimal v rozsahu [0, 99] na hodnotu `val` a uloží `val * 100 - 1900` v `pt-&tm_year`.

`'d'` nebo `'e'`--převede vstupní pole desetinného čísla v rozsahu [1, 31] a uloží jeho hodnotu do `pt-&tm_mday`.

`'D'` – se chová stejně jako `"%m / %d / %y"`.

`'H'`--převede vstupní pole desetinného čísla v rozsahu [0, 23] a uloží jeho hodnotu do `pt-&tm_hour`.

`'I'`--převede vstupní pole desetinného čísla v rozsahu [0, 11] a uloží jeho hodnotu do `pt-&tm_hour`.

`'j'`--převede vstupní pole desetinného čísla v rozsahu [1, 366] a uloží jeho hodnotu do `pt-&tm_yday`.

`'m'`--převede vstupní pole desetinného čísla v rozsahu [1, 12] na hodnotu `val` a uloží `val - 1` v a uloží hodnotu do `pt-&tm_mon`.

`'M'`--převede vstupní pole desetinného čísla v rozsahu [0, 59] a uloží jeho hodnotu do `pt-&tm_min`.

`'n'` nebo `'t'` – se chovají stejně jako `" "`.

`'p'`--převede "AM" nebo "am" na nulu a "PM" nebo "PM" na 12 a přidá tuto hodnotu do `pt-&tm_hour`.

`'r'` – se chová stejně jako `"%I : %M : %S %p"`.

`'R'` – se chová stejně jako `"%H %M"`.

`'S'`--převede vstupní pole desetinného čísla v rozsahu [0, 59] a uloží jeho hodnotu do `pt-&tm_sec`.

`'T'` nebo `'X'` – se chovají stejně jako `"%H : %M : S"`.

`'U'`--převede vstupní pole desetinného čísla v rozsahu [0, 53] a uloží jeho hodnotu do `pt-&tm_yday`.

`'w'`--převede vstupní pole desetinného čísla v rozsahu [0, 6] a uloží jeho hodnotu do `pt-&tm_wday`.

`'W'`--převede vstupní pole desetinného čísla v rozsahu [0, 53] a uloží jeho hodnotu do `pt-&tm_yday`.

`'x'` – se chová stejně jako `"%d / %m / %y"`.

`'y'` – převede vstupní pole Decimal v rozsahu [0, 99] na hodnotu `val` a uloží `val < 69  val + 100 : val` v `pt-&tm_year`.

`'Y'` – se chová stejně jako [time_get:: get_year](#get_year).

Všechny ostatní specifikátory převodu `ios_base::failbit` v `state` a vrátí. V této implementaci jakýkoli modifikátor nemá žádný vliv.

## <a name="do_get_date"></a>time_get::d o_get_date

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako data vytvořeného specifikátorem *x* pro `strftime`.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*poslední*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*iosbase*\
Příznak formátu, který po nastavení označuje, že symbol měny je nepovinný; v opačném případě se vyžaduje.

\ *stavu*
Nastaví odpovídající prvky maskování pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*ptm*\
Ukazatel na místo, kde budou uloženy informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupním polem.

### <a name="remarks"></a>Poznámky

Členská funkce Virtual Protected se pokusí porovnat sekvenční prvky začínající první v sekvenci [`first`, `last`), dokud nerozpozná celé neprázdné vstupní pole data. Je-li to úspěšné, převede toto pole na jeho ekvivalentní hodnotu jako komponenty **TM:: tm\_Mon**, **TM:: TM\_Day**a **TM:: TM\_year**a ukládá výsledky do `ptm->tm_mon`, `ptm->tm_day`a `ptm->tm_year`v uvedeném pořadí. Vrátí iterátor, který určuje první prvek za polem pro zadání data. V opačném případě funkce nastaví `iosbase::failbit` ve *stavu*. Vrátí iterátor určení prvního prvku nad rámec libovolné předpony platného vstupního pole data. V obou případech, Pokud vrácená hodnota se rovná *Last*, sada funkcí nastaví `ios_base::eofbit` ve *stavu*.

Formát pole pro zadání data je závislý na národním prostředí. Pro výchozí národní prostředí má pole pro zadání data formulář MMM DD, rrrr, kde:

- MMM se bude shodovat s voláním [get_monthname](#get_monthname), což dává v měsíci.

- DD je posloupnost desítkových číslic, jejichž odpovídající číselná hodnota musí být v rozsahu [1, 31], který poskytuje den v měsíci.

- RRRR se shoduje se voláním [get_year](#get_year), což dává rok.

Mezery literálů a čárky musí odpovídat odpovídajícím prvkům ve vstupní sekvenci.

### <a name="example"></a>Příklad

Podívejte se na příklad [get_date](#get_date), který volá `do_get_date`.

## <a name="do_get_monthname"></a>time_get::d o_get_monthname

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu měsíce.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*poslední*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*iosbase*\
Nepoužívá se.

\ *stavu*
Výstupní parametr, který nastaví odpovídající prvky maskování pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*ptm*\
Ukazatel na místo, kam mají být uloženy informace o měsíci.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupním polem.

### <a name="remarks"></a>Poznámky

Členská funkce Virtual Protected se pokusí porovnat sekvenční prvky začínající první v sekvenci [`first`, `last`), dokud nerozpozná celé, neprázdné vstupní pole měsíce. V případě úspěchu převede toto pole na jeho ekvivalentní hodnotu jako součást **TM:: tm\_Mon**a uloží výsledek do `ptm->tm_mon`. Vrátí iterátor, který určuje první prvek za vstupním polem měsíc. V opačném případě funkce nastaví `ios_base::failbit` ve *stavu*. Vrátí iterátor, který určuje první prvek nad rámec libovolné předpony vstupního pole platný měsíc. V obou případech, Pokud vrácená hodnota se rovná *Last*, sada funkcí nastaví `ios_base::eofbit` ve *stavu*.

Vstupní pole měsíc je sekvence, která odpovídá nejdelší sadě sekvencí specifických pro národní prostředí, jako jsou leden, leden, únor, únor a tak dále. Převedená hodnota je počet měsíců od ledna.

### <a name="example"></a>Příklad

Podívejte se na příklad [get_monthname](#get_monthname), který volá `do_get_monthname`.

## <a name="do_get_time"></a>time_get::d o_get_time

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako data vytvořeného specifikátorem *X* pro `strftime`.

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*poslední*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*iosbase*\
Nepoužívá se.

\ *stavu*
Nastaví odpovídající prvky maskování pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*ptm*\
Ukazatel na místo, kde budou uloženy informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupním polem.

### <a name="remarks"></a>Poznámky

Členská funkce Virtual Protected se pokusí porovnat sekvenční prvky začínající první v sekvenci [`first`, `last`), dokud nerozpozná celé, neprázdné vstupní pole Time. V případě úspěchu převede toto pole na jeho ekvivalentní hodnotu, protože komponenty `tm::tm_hour`, `tm::tm_min`a `tm::tm_sec`a výsledky ukládá `ptm->tm_hour`, `ptm->tm_min`a `ptm->tm_sec`v uvedeném pořadí. Vrátí iterátor, který určuje první prvek za vstupním polem Time. V opačném případě funkce nastaví `ios_base::failbit` ve *stavu*. Vrátí iterátor určení prvního prvku nad rámec libovolné předpony platného vstupního pole Time. V obou případech, Pokud vrácená hodnota se rovná *Last*, sada funkcí nastaví `ios_base::eofbit` ve *stavu*.

V této implementaci má pole Time Input tvar HH: MM: SS, kde:

- HH je posloupnost desítkových číslic, jejichž odpovídající číselná hodnota musí být v rozsahu [0, 24), který poskytuje hodinu dne.

- MM je posloupnost desítkových číslic, jejichž odpovídající číselná hodnota musí být v rozsahu [0, 60), který poskytuje minuty po celé hodině.

- SS je posloupnost desítkových číslic, jejichž odpovídající číselná hodnota musí být v rozsahu [0, 60), který poskytuje sekundy po minutě.

Dvojtečky literálů musí odpovídat odpovídajícím prvkům ve vstupní sekvenci.

### <a name="example"></a>Příklad

Podívejte se na příklad [get_time](#get_time), který volá `do_get_time`.

## <a name="do_get_weekday"></a>time_get::d o_get_weekday

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu týdnu.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*poslední*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*iosbase*\
Příznak formátu, který po nastavení označuje, že symbol měny je nepovinný; v opačném případě se vyžaduje.

\ *stavu*
Nastaví odpovídající prvky maskování pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*ptm*\
Ukazatel na místo, kam mají být uloženy informace o týdnu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupním polem.

### <a name="remarks"></a>Poznámky

Členská funkce Virtual Protected se pokusí porovnat sekvenční prvky začínající *první* v sekvenci [`first`, `last`), dokud nerozpozná celé neprázdné vstupní pole v týdnu. V případě úspěchu převede toto pole na jeho ekvivalentní hodnotu jako součást **TM:: tm\_wDay**a uloží výsledek do `ptm->tm_wday`. Vrátí iterátor, který určuje první prvek za vstupním polem dne v týdnu. V opačném případě funkce nastaví `ios_base::failbit` ve *stavu*. Vrátí iterátor určení prvního prvku nad rámec libovolné předpony platného vstupního pole v týdnu. V obou případech, Pokud vrácená hodnota se rovná *Last*, sada funkcí nastaví `ios_base::eofbit` ve *stavu*.

Vstupní pole Weekday je sekvence, která se shoduje s nejdelší sadou sekvencí specifických pro národní prostředí, například Sun, neděle, Mon, pondělí a tak dále. Převedená hodnota je počet dní od neděle.

### <a name="example"></a>Příklad

Podívejte se na příklad [get_weekday](#get_weekday), který volá `do_get_weekday`.

## <a name="do_get_year"></a>time_get::d o_get_year

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu roku.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*poslední*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*iosbase*\
Příznak formátu, který po nastavení označuje, že symbol měny je nepovinný; v opačném případě se vyžaduje.

\ *stavu*
Nastaví odpovídající prvky maskování pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*ptm*\
Ukazatel na místo, kam mají být uloženy informace o roku.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupním polem.

### <a name="remarks"></a>Poznámky

Členská funkce Virtual Protected se pokusí porovnat sekvenční prvky začínající *první* v sekvenci [`first`, `last`), dokud nerozpozná celé neprázdné vstupní pole roku. V případě úspěchu převede toto pole na jeho ekvivalentní hodnotu jako součást **TM:: tm\_Year**a výsledek uloží do `ptm->tm_year`. Vrátí iterátor, který určuje první prvek za vstupním polem year. V opačném případě funkce nastaví `ios_base::failbit` ve *stavu*. Vrátí iterátor určení prvního prvku nad rámec libovolné předpony platného vstupního pole roku. V obou případech, Pokud vrácená hodnota se rovná *Last*, sada funkcí nastaví `ios_base::eofbit` ve *stavu*.

Pole Year input je posloupnost desítkových číslic, jejichž odpovídající číselná hodnota musí být v rozsahu [1900, 2036). Uloženou hodnotou je hodnota minus 1900. V této implementaci hodnoty v rozsahu [69, 136) reprezentují rozsah roků [1969, 2036). Hodnoty v rozsahu [0, 69) jsou také přípustné, ale mohou představovat buď rozsah roků [1900, 1969) nebo [2000, 2069) v závislosti na konkrétním prostředí překladu.

### <a name="example"></a>Příklad

Podívejte se na příklad [get_year](#get_year), který volá `do_get_year`.

## <a name="get"></a>time_get:: Get

Čte ze zdroje data znaků a převede je na čas, který je uložen v časové struktuře. První funkce přijímá jeden specifikátor převodu a modifikátor, druhý akceptuje několik.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char_type* fmt_first,
    char_type* fmt_last) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor, který označuje, kde se spustí sekvence, která má být převedena.

*poslední*\
Vstupní iterátor, který označuje konec posloupnosti, která má být převedena.

*iosbase*\
Datový proud.

\ *stavu*
Pro stav datového proudu jsou nastaveny příslušné prvky maskování dat, aby označovaly chyby.

*ptm*\
Ukazatel na časovou strukturu, ve které má být čas uložen.

*fmt*\
Znak specifikátoru převodu.

\ *mod*
Volitelný znak modifikátoru.

*fmt_first*\
Odkazuje na to, kde se spouští direktivy Format.

*fmt_last*\
Odkazuje na konec direktiv formátu.

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor na první znak za daty, která byla použita k přiřazení časové struktury `*ptm`.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí `do_get(first, last, iosbase, state, ptm, fmt, mod)`.

Druhá členská funkce volá `do_get` pod kontrolou formátu odděleného `[fmt_first, fmt_last)`. Považuje formát za sekvenci polí, z nichž každý určuje převod nula nebo více elementů Input oddělených `[first, last)`. Vrátí iterátor určení prvního nepřevedeného prvku. Existují tři druhy polí:

A za cent (%) ve formátu, za nímž následuje volitelný modifikátor *mod* v sadě [EOQ #] následovaný specifikátorem převodu *FMT*, je *nejdříve* nahrazen hodnotou vrácenou `do_get(first, last, iosbase, state, ptm, fmt, mod)`. Selhání převodu nastaví `ios_base::failbit` ve *stavu* a vrátí.

Prázdný element ve formátu přeskočí za nula nebo více vstupních prázdných elementů.

Všechny ostatní prvky ve formátu musí odpovídat dalšímu vstupnímu prvku, který se přeskočí. Sada chyb se shodou `ios_base::failbit` ve *stavu* a vrátí.

## <a name="get_date"></a>time_get:: get_date

Analyzuje řetězec jako datum vytvořené specifikátorem *x* pro `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*poslední*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*iosbase*\
Příznak formátu, který po nastavení označuje, že symbol měny je nepovinný; v opačném případě se vyžaduje.

\ *stavu*
Nastaví odpovídající prvky maskování pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*ptm*\
Ukazatel na místo, kde budou uloženy informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupním polem.

### <a name="remarks"></a>Poznámky

Členská funkce vrací [do_get_date](#do_get_date)(`first`, `last`, `iosbase`, `state`, `ptm`).

Všimněte si, že měsíce se počítají z 0 do 11.

### <a name="example"></a>Příklad

```cpp
// time_get_get_date.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset(&t, 0, sizeof(struct tm));

   pszGetF << "July 4, 2000";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get<char> >
   (loc).get_date(basic_istream<char>::_Iter(pszGetF.rdbuf( ) ),
            basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if ( st & ios_base::failbit )
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(July 4, 2000) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 4
tm_mon: 6
tm_year: 100
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_monthname"></a>time_get:: get_monthname

Analyzuje řetězec jako název měsíce.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*poslední*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*iosbase*\
Nepoužívá se.

\ *stavu*
Výstupní parametr, který nastaví odpovídající prvky maskování pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*ptm*\
Ukazatel na místo, kam mají být uloženy informace o měsíci.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupním polem.

### <a name="remarks"></a>Poznámky

Členská funkce vrací [do_get_monthname](#do_get_monthname)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Příklad

```cpp
// time_get_get_monthname.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "juillet";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get <char> >
   (loc).get_monthname(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
              basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(juillet) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 0
tm_mon: 6
tm_year: 0
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_time"></a>time_get:: get_time

Analyzuje řetězec jako datum vytvořené specifikátorem *X* pro `strftime`.

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*poslední*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*iosbase*\
Nepoužívá se.

\ *stavu*
Nastaví odpovídající prvky maskování pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*ptm*\
Ukazatel na místo, kde budou uloženy informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupním polem.

### <a name="remarks"></a>Poznámky

Členská funkce vrací [do_get_time](#do_get_time)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Příklad

```cpp
// time_get_get_time.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "11:13:20";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get <char> >
      (loc).get_time(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << endl;
}
```

```Output
time_get::get_time(11:13:20) =
tm_sec: 20
tm_min: 13
tm_hour: 11
```

## <a name="get_weekday"></a>time_get:: get_weekday

Analyzuje řetězec jako název dne v týdnu.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*poslední*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*iosbase*\
Příznak formátu, který po nastavení označuje, že symbol měny je nepovinný; v opačném případě se vyžaduje.

\ *stavu*
Nastaví odpovídající prvky maskování pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*ptm*\
Ukazatel na místo, kam mají být uloženy informace o týdnu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupním polem.

### <a name="remarks"></a>Poznámky

Členská funkce vrací [do_get_weekday](#do_get_weekday)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Příklad

```cpp
// time_get_get_weekday.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "mercredi";
   pszGetF.imbue(loc);
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_weekday(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_wday: " << t.tm_wday
      << endl;
}
```

```Output
time_get::get_time(mercredi) =
tm_wday: 3
```

## <a name="get_year"></a>time_get:: get_year

Analyzuje řetězec jako název roku.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*poslední*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*iosbase*\
Příznak formátu, který po nastavení označuje, že symbol měny je nepovinný; v opačném případě se vyžaduje.

\ *stavu*
Nastaví odpovídající prvky maskování pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*ptm*\
Ukazatel na místo, kam mají být uloženy informace o roku.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupním polem.

### <a name="remarks"></a>Poznámky

Členská funkce vrací [do_get_year](#do_get_year)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Příklad

```cpp
// time_get_get_year.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "1928";

   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_year(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_year: " << t.tm_year
      << endl;
}
```

```Output
time_get::get_year(1928) =
tm_year: 28
```

## <a name="iter_type"></a>time_get:: iter_type

Typ, který popisuje vstupní iterátor.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **InputIterator**.

## <a name="time_get"></a>time_get:: time_get

Konstruktor pro objekty typu `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

\ *ReFS*
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *ReFS* a jejich význam jsou:

- 0: životnost objektu je spravována místními objekty, které jej obsahují.

- 1: životnost objektu musí být ručně spravovaná.

- \> 1: tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože je destruktor chráněný.

Konstruktor inicializuje svůj základní objekt pomocí **locale::** [Face](../standard-library/locale-class.md#facet_class)(`refs`).

## <a name="see-also"></a>Viz také

[\<> národního prostředí](../standard-library/locale.md)\
[time_base\ třídy](../standard-library/time-base-class.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
