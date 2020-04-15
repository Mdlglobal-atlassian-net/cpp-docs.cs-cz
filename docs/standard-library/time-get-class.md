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
ms.openlocfilehash: 9aebdaffc8bf3754bdbda08247f72ae08475711f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368041"
---
# <a name="time_get-class"></a>time_get – třída

Šablona třídy popisuje objekt, který může sloužit jako omezující vlastnost národního `CharType` prostředí pro řízení převodů sekvencí typu na časové hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků.

*Vstupní iterátor*\
Iterátor, ze kterého se čtou hodnoty času.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložená hodnota ukládá jedinečnou kladnou hodnotu v **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[time_get](#time_get)|Konstruktor pro objekty `time_get`typu .|

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
|[do_get_date](#do_get_date)|Chráněná virtuální členská funkce, která je volána k `x` analyzovat `strftime`řetězec jako datum vytvořené specifikátorem pro .|
|[do_get_monthname](#do_get_monthname)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu měsíce.|
|[do_get_time](#do_get_time)|Chráněná virtuální členská funkce, která je volána k `X` analyzovat `strftime`řetězec jako datum vytvořené specifikátorem pro .|
|[do_get_weekday](#do_get_weekday)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu týdnu.|
|[do_get_year](#do_get_year)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu roku.|
|[get](#get)|Čte ze zdroje data znaků a převede je na čas, který je uložen v časové struktuře.|
|[get_date](#get_date)|Analyzuje řetězec jako datum vytvořené specifikátorem `x` `strftime`pro .|
|[get_monthname](#get_monthname)|Analyzuje řetězec jako název měsíce.|
|[get_time](#get_time)|Analyzuje řetězec jako datum vytvořené specifikátorem `X` `strftime`pro .|
|[get_weekday](#get_weekday)|Analyzuje řetězec jako název dne v týdnu.|
|[get_year](#get_year)|Analyzuje řetězec jako název roku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="time_getchar_type"></a><a name="char_type"></a>time_get::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony **CharType**.

## <a name="time_getdate_order"></a><a name="date_order"></a>time_get::date_order

Vrátí pořadí data používané omezující vlastností.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>Návratová hodnota

Pořadí kalendářních dat používané omezující sazem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_date_order](#do_date_order).

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

## <a name="time_getdo_date_order"></a><a name="do_date_order"></a>time_get::do_date_order

Chráněná virtuální členská funkce, která je volána k vrácení pořadí data používaného omezující vlastností.

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>Návratová hodnota

Pořadí kalendářních dat používané omezující sazem.

### <a name="remarks"></a>Poznámky

Virtuální chráněná členská funkce vrátí hodnotu typu **time_base::dateorder**, která popisuje pořadí, ve kterém jsou komponenty data spárovány s [do_get_date](#do_get_date). V této implementaci je hodnota **time_base::mdy**, odpovídající datům formuláře 2.

### <a name="example"></a>Příklad

Viz příklad pro [date_order](#date_order) `do_date_order`, který volá .

## <a name="time_getdo_get"></a><a name="do_get"></a>time_get::do_get

Čte a převede data znaků na hodnotu času. Přijme jeden specifikátor a modifikátor převodu.

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

*První*\
Vstupní iterátor, který označuje začátek sekvence převést.

*Poslední*\
Vstupní iterátor, který označuje konec sekvence.

*iosbase*\
Objekt datového proudu.

*Státu*\
Pole v iosbase, kde jsou vhodné prvky bitové masky nastaveny tak, aby označovaly chyby.

*Ptm*\
Ukazatel na strukturu času, kde má být čas uložen.

*Fmt*\
Znak specifikátoru převodu.

*Mod*\
Volitelný modifikační znak.

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor, který označuje první nepřevedený prvek. Selhání převodu `ios_base::failbit` `state` nastaví a vrátí *jako první*.

### <a name="remarks"></a>Poznámky

Virtuální členská funkce převede a přeskočí jeden nebo`first` `last`více vstupních prvků v rozsahu [ `*pt`, ) a určí hodnoty uložené v jednom nebo více členech aplikace . Selhání převodu `ios_base::failbit` `state` nastaví a vrátí *jako první*. Jinak funkce vrátí iterátor označující první nepřevedený prvek.

Specifikátory převodu jsou:

`'a'`nebo `'A'` -- se chová stejně jako [time_get::get_weekday](#get_weekday).

`'b'`, `'B'`, `'h'` nebo -- se chová stejně jako [time_get::get_monthname](#get_monthname).

`'c'`- chová se stejně jako `"%b %d %H : %M : %S %Y"`.

`'C'`-- převede desetinné vstupní pole v rozsahu [0, `val` 99] `pt-&tm_year`na hodnotu a uloží v `val * 100 - 1900` .

`'d'`nebo `'e'` -- převede desetinné vstupní pole v rozsahu [1, 31] a uloží jeho hodnotu do . `pt-&tm_mday`

`'D'`- chová se stejně jako `"%m / %d / %y"`.

`'H'`-- převede desetinné vstupní pole v rozsahu [0, 23] a uloží jeho hodnotu do `pt-&tm_hour`.

`'I'`-- převede desetinné vstupní pole v rozsahu [0, 11] a uloží jeho hodnotu do `pt-&tm_hour`.

`'j'`-- převede desetinné vstupní pole v rozsahu [1, 366] a uloží jeho hodnotu do . `pt-&tm_yday`

`'m'`-- převede desetinné vstupní pole v rozsahu [1, `val` 12] na hodnotu a uloží `val - 1` a uloží jeho hodnotu do . `pt-&tm_mon`

`'M'`-- převede desetinné vstupní pole v rozsahu [0, 59] a uloží jeho hodnotu do `pt-&tm_min`.

`'n'`nebo `'t'` -- se chová `" "`stejně jako .

`'p'`-- převede "AM" nebo "am" na nulu a "PM" nebo `pt-&tm_hour`"PM" na 12 a přidá tuto hodnotu .

`'r'`- chová se stejně jako `"%I : %M : %S %p"`.

`'R'`- chová se stejně jako `"%H %M"`.

`'S'`-- převede desetinné vstupní pole v rozsahu [0, 59] a uloží jeho hodnotu do `pt-&tm_sec`.

`'T'`nebo `'X'` -- se chová `"%H : %M : S"`stejně jako .

`'U'`-- převede desetinné vstupní pole v rozsahu [0, 53] a uloží jeho hodnotu do `pt-&tm_yday`.

`'w'`-- převede desetinné vstupní pole v rozsahu [0, 6] a uloží jeho hodnotu do `pt-&tm_wday`.

`'W'`-- převede desetinné vstupní pole v rozsahu [0, 53] a uloží jeho hodnotu do `pt-&tm_yday`.

`'x'`- chová se stejně jako `"%d / %m / %y"`.

`'y'`-- převede desetinné vstupní pole v rozsahu [0, `val` 99] `pt-&tm_year`na hodnotu a uloží v `val < 69  val + 100 : val` .

`'Y'`- chová se stejně jako [time_get::get_year](#get_year).

Všechny ostatní specifikátor `ios_base::failbit` `state` převodu sady a vrátí. V této implementaci nemá žádný modifikátor žádný vliv.

## <a name="time_getdo_get_date"></a><a name="do_get_date"></a>time_get::do_get_date

Chráněná virtuální členská funkce, která je volána k *x* analyzovat řetězec `strftime`jako datum vyrobené specifikátorem x pro .

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*iosbase*\
Příznak formátu, který při nastavení označuje, že symbol měny je volitelný; v opačném případě je vyžadována.

*Státu*\
Nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné.

*Ptm*\
Ukazatel na místo, kde mají být uloženy informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupnípole.

### <a name="remarks"></a>Poznámky

Virtuální chráněná členská funkce se pokusí porovnat sekvenční prvky začínající nejprve v sekvenci [ `first`, `last`), dokud nerozpozná úplné, neprázdné vstupní pole data. Pokud je úspěšná, převede toto pole na ekvivalentní hodnotu jako součásti **\_tm::tm mon**, **tm::tm\_day**a **\_tm::tm year**a uloží výsledky do `ptm->tm_mon`, `ptm->tm_day`, a , resp. `ptm->tm_year` Vrátí iterátor určení první prvek za vstupní pole data. V opačném případě `iosbase::failbit` se funkce nastaví ve *stavu*. Vrátí iterátor určení první prvek za všechny předpony platné datum vstupní pole. V obou případech, pokud se vrácená hodnota `ios_base::eofbit` rovná *poslední*, funkce nastaví ve *stavu*.

Formát vstupního pole data závisí na národním prostředí. Pro výchozí národní prostředí má vstupní pole data formulář MMM DD, YYYY, kde:

- MMM je uzavřeno voláním [get_monthname](#get_monthname), což měsíc.

- DD je posloupnost desetinných míst, jejichž odpovídající číselná hodnota musí být v rozsahu [1, 31], udávající den v měsíci.

- YYYY je uzavřeno voláním [get_year](#get_year), dávat rok.

Mezery literálu a čárky musí odpovídat odpovídající prvky ve vstupní sekvenci.

### <a name="example"></a>Příklad

Viz příklad pro [get_date](#get_date) `do_get_date`, který volá .

## <a name="time_getdo_get_monthname"></a><a name="do_get_monthname"></a>time_get::do_get_monthname

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu měsíce.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*iosbase*\
Nepoužívá se.

*Státu*\
Výstupní parametr, který nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné.

*Ptm*\
Ukazatel na místo, kde mají být uloženy informace o měsíci.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupnípole.

### <a name="remarks"></a>Poznámky

Virtuální chráněná členská funkce se pokusí porovnat sekvenční prvky začínající nejprve v sekvenci [ `first`, `last`), dokud nerozpozná celé, neprázdné vstupní pole měsíce. Pokud je úspěšná, převede toto pole na ekvivalentní hodnotu jako komponenta **tm::tm\_mon**a uloží výsledek do . `ptm->tm_mon` Vrátí iterátor určení první prvek za vstupní pole měsíce. V opačném případě `ios_base::failbit` se funkce nastaví ve *stavu*. Vrátí iterátor určení první prvek za všechny předpony platné ho měsíc vstupní pole. V obou případech, pokud se vrácená hodnota `ios_base::eofbit` rovná *poslední*, funkce nastaví ve *stavu*.

Vstupní pole měsíce je posloupnost, která odpovídá nejdelší sadě sekvencí specifických pro národní prostředí, například Leden, Leden, Únor a tak dále. Převedená hodnota je počet měsíců od ledna.

### <a name="example"></a>Příklad

Viz příklad pro [get_monthname](#get_monthname) `do_get_monthname`, který volá .

## <a name="time_getdo_get_time"></a><a name="do_get_time"></a>time_get::do_get_time

Chráněná virtuální členská funkce, která je volána k *X* analyzovat řetězec `strftime`jako datum vyrobené specifikátorem X pro .

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*iosbase*\
Nepoužívá se.

*Státu*\
Nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné.

*Ptm*\
Ukazatel na místo, kde mají být uloženy informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupnípole.

### <a name="remarks"></a>Poznámky

Virtuální chráněná členská funkce se pokusí porovnat sekvenční prvky začínající nejprve v sekvenci [ `first`, `last`), dokud nerozpozná úplné, neprázdné vstupní pole času. Pokud je úspěšná, převede toto pole `tm::tm_hour`na `tm::tm_min`ekvivalentní `tm::tm_sec`hodnotu jako `ptm->tm_hour`komponenty , a , a uloží výsledky v , `ptm->tm_min`, a `ptm->tm_sec`, resp. Vrátí iterátor určení první prvek za pole pro vstup času. V opačném případě `ios_base::failbit` se funkce nastaví ve *stavu*. Vrátí iterátor určení první prvek za všechny předpony platné pole pro zadávání času. V obou případech, pokud se vrácená hodnota `ios_base::eofbit` rovná *poslední*, funkce nastaví ve *stavu*.

V této implementaci má pole pro zadání času formulář HH:MM:SS, kde:

- HH je posloupnost desetinných míst, jejichž odpovídající číselná hodnota musí být v rozsahu [0, 24), udávající hodinu dne.

- MM je posloupnost desetinných míst, jejichž odpovídající číselná hodnota musí být v rozsahu [0, 60), udávající minuty za hodinou.

- SS je posloupnost desetinných míst, jejichž odpovídající číselná hodnota musí být v rozsahu [0, 60), což dává sekundy za minutu.

Literál dvojtečky musí odpovídat odpovídající prvky ve vstupní sekvenci.

### <a name="example"></a>Příklad

Viz příklad pro [get_time](#get_time) `do_get_time`, který volá .

## <a name="time_getdo_get_weekday"></a><a name="do_get_weekday"></a>time_get::do_get_weekday

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu týdnu.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*iosbase*\
Příznak formátu, který při nastavení označuje, že symbol měny je volitelný; v opačném případě je vyžadována.

*Státu*\
Nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné.

*Ptm*\
Ukazatel na místo, kde mají být uloženy informace o dni v týdnu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupnípole.

### <a name="remarks"></a>Poznámky

Virtuální chráněná členská funkce se pokusí porovnat sekvenční prvky začínající *nejprve* v sekvenci [ `first`, `last`), dokud nerozpozná úplné, neprázdné vstupní pole dne v týdnu. Pokud je úspěšná, převede toto pole na ekvivalentní hodnotu jako komponenta **tm::tm\_wday**a uloží výsledek do . `ptm->tm_wday` Vrátí iterátor určení první prvek za vstupní pole den v týdnu. V opačném případě `ios_base::failbit` se funkce nastaví ve *stavu*. Vrátí iterátor určení první prvek za všechny předpony platné pole vstup v týdnu. V obou případech, pokud se vrácená hodnota `ios_base::eofbit` rovná *poslední*, funkce nastaví ve *stavu*.

Vstupní pole ve všední den je posloupnost, která odpovídá nejdelší sadě sekvencí specifických pro národní prostředí, například Slunce, Neděle, Po, Pondělí a tak dále. Převedená hodnota je počet dní od neděle.

### <a name="example"></a>Příklad

Podívejte se [get_weekday](#get_weekday)na příklad `do_get_weekday`pro get_weekday , který volá .

## <a name="time_getdo_get_year"></a><a name="do_get_year"></a>time_get::do_get_year

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu roku.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*iosbase*\
Příznak formátu, který při nastavení označuje, že symbol měny je volitelný; v opačném případě je vyžadována.

*Státu*\
Nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné.

*Ptm*\
Ukazatel na místo, kde mají být uloženy informace o roce.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupnípole.

### <a name="remarks"></a>Poznámky

Virtuální chráněná členská funkce se pokusí porovnat sekvenční prvky začínající *nejprve* v sekvenci [ `first`, `last`), dokud nerozpozná celé, neprázdné vstupní pole roku. Pokud je úspěšná, převede toto pole na ekvivalentní hodnotu jako komponenta `ptm->tm_year` **tm::tm\_year**a uloží výsledek v . Vrátí iterátor označující první prvek za vstupní pole roku. V opačném případě `ios_base::failbit` se funkce nastaví ve *stavu*. Vrátí iterátor označující první prvek za všechny předpony vstupnípole platného roku. V obou případech, pokud se vrácená hodnota `ios_base::eofbit` rovná *poslední*, funkce nastaví ve *stavu*.

Vstupní pole roku je posloupnost desetinných míst, jejichž odpovídající číselná hodnota musí být v rozsahu [1900, 2036). Uložená hodnota je tato hodnota mínus 1900. V této implementaci představují hodnoty v rozsahu [69, 136) rozsah let [1969, 2036). Hodnoty v rozsahu [0, 69) jsou také přípustné, ale mohou představovat buď rozsah let [1900, 1969) nebo [2000, 2069), v závislosti na konkrétním překladatelském prostředí.

### <a name="example"></a>Příklad

Podívejte se [get_year](#get_year)na příklad `do_get_year`pro get_year , který volá .

## <a name="time_getget"></a><a name="get"></a>time_get::získat

Čte ze zdroje data znaků a převede je na čas, který je uložen v časové struktuře. První funkce přijme jeden specifikátor převodu a modifikátor, druhá přijme několik.

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

*První*\
Vstupní iterátor, který označuje, kde začíná sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor, který označuje konec sekvence, která má být převedena.

*iosbase*\
Proud.

*Státu*\
Příslušné prvky bitové masky jsou nastaveny pro stav datového proudu k označení chyb.

*Ptm*\
Ukazatel na strukturu času, kde má být čas uložen.

*Fmt*\
Znak specifikátoru převodu.

*Mod*\
Volitelný modifikační znak.

*fmt_first*\
Poukazuje na to, kde začínají direktivy formátu.

*fmt_last*\
Odkazuje na konec formátsměrnic.

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor prvnímu znaku za daty, která byla `*ptm`použita k přiřazení časové struktury .

### <a name="remarks"></a>Poznámky

První členská `do_get(first, last, iosbase, state, ptm, fmt, mod)`funkce vrátí .

Druhá členská `do_get` funkce volá pod kontrolou formátu `[fmt_first, fmt_last)`ohraničeného . S formátem zachází jako s posloupností polí, z nichž každé určuje `[first, last)`převod nuly nebo více vstupních prvků oddělených . Vrátí iterátor označující první nepřevedený prvek. Existují tři druhy polí:

Procento (%) ve formátu, následovaný volitelným modifikátorem *mod* v sadě [EOQ#], následovaný specifikátorem převodu `do_get(first, last, iosbase, state, ptm, fmt, mod)` *fmt*, nahradí *nejprve* hodnotu vrácenou . Selhání převodu `ios_base::failbit` nastaví ve *stavu* a vrátí.

Element prázdné ho ve formátu přeskočí za nulu nebo více vstupních prvků prázdného místa.

Jakýkoli jiný prvek ve formátu musí odpovídat dalšímu vstupnímu prvku, který je přeskočen. Selhání shody `ios_base::failbit` nastaví ve *stavu* a vrátí.

## <a name="time_getget_date"></a><a name="get_date"></a>time_get::get_date

Analyzuje řetězec jako datum vytvořené specifikátorem *x* pro `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*iosbase*\
Příznak formátu, který při nastavení označuje, že symbol měny je volitelný; v opačném případě je vyžadována.

*Státu*\
Nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné.

*Ptm*\
Ukazatel na místo, kde mají být uloženy informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupnípole.

### <a name="remarks"></a>Poznámky

Členská funkce [do_get_date](#do_get_date)vrátí`first` `last`do_get_date `iosbase` `state`( `ptm`, , , ).

Všimněte si, že měsíce se počítají od 0 do 11.

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

## <a name="time_getget_monthname"></a><a name="get_monthname"></a>time_get::get_monthname

Analyzuje řetězec jako název měsíce.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*iosbase*\
Nepoužívá se.

*Státu*\
Výstupní parametr, který nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné.

*Ptm*\
Ukazatel na místo, kde mají být uloženy informace o měsíci.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupnípole.

### <a name="remarks"></a>Poznámky

Členská funkce [do_get_monthname](#do_get_monthname)vrátí`first` `last`do_get_monthname `iosbase` `state`( `ptm`, , , ).

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

## <a name="time_getget_time"></a><a name="get_time"></a>time_get::get_time

Analyzuje řetězec jako datum vytvořené specifikátorem *X* pro `strftime`.

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*iosbase*\
Nepoužívá se.

*Státu*\
Nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné.

*Ptm*\
Ukazatel na místo, kde mají být uloženy informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupnípole.

### <a name="remarks"></a>Poznámky

Členská funkce [do_get_time](#do_get_time)vrátí`first` `last`do_get_time `iosbase` `state`( `ptm`, , , ).

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

## <a name="time_getget_weekday"></a><a name="get_weekday"></a>time_get::get_weekday

Analyzuje řetězec jako název dne v týdnu.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*iosbase*\
Příznak formátu, který při nastavení označuje, že symbol měny je volitelný; v opačném případě je vyžadována.

*Státu*\
Nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné.

*Ptm*\
Ukazatel na místo, kde mají být uloženy informace o dni v týdnu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupnípole.

### <a name="remarks"></a>Poznámky

Členská funkce [do_get_weekday](#do_get_weekday)vrátí`first` `last`do_get_weekday `iosbase` `state`( `ptm`, , , ).

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

## <a name="time_getget_year"></a><a name="get_year"></a>time_get::get_year

Analyzuje řetězec jako název roku.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*iosbase*\
Příznak formátu, který při nastavení označuje, že symbol měny je volitelný; v opačném případě je vyžadována.

*Státu*\
Nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné.

*Ptm*\
Ukazatel na místo, kde mají být uloženy informace o roce.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za vstupnípole.

### <a name="remarks"></a>Poznámky

Členská funkce [do_get_year](#do_get_year)vrátí`first` `last`do_get_year `iosbase` `state`( `ptm`, , , ).

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

## <a name="time_getiter_type"></a><a name="iter_type"></a>time_get::iter_type

Typ, který popisuje vstupní iterátor.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony **InputIterator**.

## <a name="time_gettime_get"></a><a name="time_get"></a>time_get::time_get

Konstruktor pro objekty `time_get`typu .

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

*Refs*\
Celá hodnota používaná k určení typu správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *refs* a jejich význam jsou:

- 0: Životnost objektu je spravována národními prostředími, které jej obsahují.

- 1: Životnost objektu musí být spravována ručně.

- \>1: Tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože destruktor je chráněn.

Konstruktor inicializuje svůj základní objekt pomocí **národního prostředí::**[omezující stolku](../standard-library/locale-class.md#facet_class)(`refs`).

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)\
[time_base třída](../standard-library/time-base-class.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
