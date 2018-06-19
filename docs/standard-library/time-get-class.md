---
title: time_get – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c3db9edd974d111881b17b6f1a53c1b4ac3b336
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862845"
---
# <a name="timeget-class"></a>time_get – třída

Šablony třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převody pořadí typu `CharType` hodnoty času.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Parametry

`CharType` Typ v rámci programu použitá ke kódování znaků.

`InputIterator` Iterator, ze kterých časové hodnoty se čtou.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[time_get](#time_get)|V konstruktoru pro objekty typu `time_get`.|

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
|[do_get_date](#do_get_date)|A chráněná člena virtuální funkce, která je volána, analyzovat řetězec jako datum vyprodukované `x` – specifikátor pro `strftime`.|
|[do_get_monthname](#do_get_monthname)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu měsíce.|
|[do_get_time](#do_get_time)|A chráněná člena virtuální funkce, která je volána, analyzovat řetězec jako datum vyprodukované `X` – specifikátor pro `strftime`.|
|[do_get_weekday](#do_get_weekday)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu týdnu.|
|[do_get_year](#do_get_year)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu roku.|
|[get](#get)|Čte ze zdroje data znaků a převede je na čas, který je uložen v časové struktuře.|
|[get_date](#get_date)|Analyzuje řetězec jako datum vyprodukované `x` – specifikátor pro `strftime`.|
|[get_monthname –](#get_monthname)|Analyzuje řetězec jako název měsíce.|
|[get_time](#get_time)|Analyzuje řetězec jako datum vyprodukované `X` – specifikátor pro `strftime`.|
|[get_weekday](#get_weekday)|Analyzuje řetězec jako název dne v týdnu.|
|[get_year –](#get_year)|Analyzuje řetězec jako název roku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="char_type"></a>  time_get::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="date_order"></a>  time_get::date_order

Vrátí pořadí data používané omezující vlastností.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>Návratová hodnota

Datum pořadí použít omezující vlastnost.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [do_date_order –](#do_date_order).

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

## <a name="do_date_order"></a>  time_get::do_date_order

Chráněná virtuální členská funkce, která je volána k vrácení pořadí data používaného omezující vlastností.

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>Návratová hodnota

Datum pořadí použít omezující vlastnost.

### <a name="remarks"></a>Poznámky

Chráněný člen virtuální funkce vrátí hodnotu typu **time_base::dateorder**, který popisuje pořadí v datum, pro které jsou součástí odpovídala [do_get_date –](#do_get_date). V této implementaci hodnota je **time_base::mdy**, odpovídající pro data formuláře 2. prosince 1979.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [date_order –](#date_order), který volá `do_date_order`.

## <a name="do_get"></a>  time_get::do_get

Čte a převede data znaků na hodnotu času. Přijme jeden převod specifikace a modifikátor.

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

`first` Iterator vstup, označující začátek pořadí, které chcete převést.

`last` Iterator vstup, který označuje konec sekvenci.

`iosbase` Objekt datového proudu.

`state` Na pole v iosbase, kde jsou příslušné bitové masky elementy nastaveny k označení chyb.

`ptm` Ukazatel na strukturu čas, kdy je čas k uložení.

`fmt` Převod specifikátor znak.

`mod` Znak volitelné modifikátor.

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor, který označí první nepřevedeném elementu. Chyba převodu nastaví `ios_base::failbit` v `state` a vrátí `first`.

### <a name="remarks"></a>Poznámky

Funkce člena virtuální převede a přeskočí jednu nebo více vstupních elementy v rozsahu [`first`, `last`) k určení hodnotami uloženými v jedné nebo více členů `*pt`. Chyba převodu nastaví `ios_base::failbit` v `state` a vrátí `first`. Jinak funkce vrátí hodnotu iterovat určení první nepřevedeném elementu.

Specifikátory převod jsou:

`'a'` nebo `'A'` – se chová stejně jako [time_get::get_weekday](#get_weekday).

`'b'`, `'B'`, nebo `'h'` – se chová stejně jako [time_get::get_monthname](#get_monthname).

`'c'` --se chová stejně jako `"%b %d %H : %M : %S %Y"`.

`'C'` --převádí na hodnotu decimal vstupní pole v rozsahu [0, 99] `val` a ukládá `val * 100 - 1900` v `pt-&tm_year`.

`'d'` nebo `'e'` – převede decimal vstupní pole v rozsahu [1, 31] a ukládá její hodnota v `pt-&tm_mday`.

`'D'` --se chová stejně jako `"%m / %d / %y"`.

`'H'` – Převede decimal vstupní pole v rozsahu [0, 23] a ukládá její hodnota v `pt-&tm_hour`.

`'I'` – Převede decimal vstupní pole v rozsahu [0, 11] a ukládá její hodnota v `pt-&tm_hour`.

`'j'` – Převede decimal vstupní pole v rozsahu [1, 366] a ukládá její hodnota v `pt-&tm_yday`.

`'m'` --převádí na hodnotu decimal vstupní pole v rozsahu [1, 12] `val` a ukládá `val - 1` v a ukládá její hodnota v `pt-&tm_mon`.

`'M'` – Převede decimal vstupní pole v rozsahu [0, 59] a ukládá její hodnota v `pt-&tm_min`.

`'n'` nebo `'t'` – se chová stejně jako `" "`.

`'p'` – Převede "M" nebo "m" nula "Odp." nebo "Odp." na 12 a přidá této hodnoty na `pt-&tm_hour`.

`'r'` --se chová stejně jako `"%I : %M : %S %p"`.

`'R'` --se chová stejně jako `"%H %M"`.

`'S'` – Převede decimal vstupní pole v rozsahu [0, 59] a ukládá její hodnota v `pt-&tm_sec`.

`'T'` nebo `'X'` – se chová stejně jako `"%H : %M : S"`.

`'U'` – Převede decimal vstupní pole v rozsahu [0, 53] a ukládá její hodnota v `pt-&tm_yday`.

`'w'` – Převede decimal vstupní pole v rozsahu [0, 6] a ukládá její hodnota v `pt-&tm_wday`.

`'W'` – Převede decimal vstupní pole v rozsahu [0, 53] a ukládá její hodnota v `pt-&tm_yday`.

`'x'` --se chová stejně jako `"%d / %m / %y"`.

`'y'` --převádí na hodnotu decimal vstupní pole v rozsahu [0, 99] `val` a ukládá `val < 69  val + 100 : val` v `pt-&tm_year`.

`'Y'` --se chová stejně jako [time_get::get_year](#get_year).

Všechny ostatní sady převod specifikátor `ios_base::failbit` v `state` a vrátí. V této implementaci žádné modifikátor nemá žádný vliv.

## <a name="do_get_date"></a>  time_get::do_get_date

A chráněná člena virtuální funkce, která je volána, analyzovat řetězec jako datum vyprodukované *x* – specifikátor pro `strftime`.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`iosbase` Příznak formátu, který při sadu označuje, že symbolu měny je volitelná. jinak je vyžadována.

`state` Nastaví prvky příslušné bitové masky pro datový proud stav podle zda operace byla úspěšná.

`ptm` Ukazatel na kterém má být uložena informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Funkce virtuální chráněného člena se pokusí vyhledat sekvenční elementy začínající na první v pořadí [ `first`, `last`) dokud má rozpoznána úplná, neprázdné datum vstupní pole. Pokud úspěšné, převede ji toto pole na ekvivalentní hodnotu jako komponenty **tm::tm\_mon**, **tm::tm\_den**, a **tm::tm\_roku** a ukládá výsledky do `ptm->tm_mon`, `ptm->tm_day`, a `ptm->tm_year`, v uvedeném pořadí. Vrátí iterovat určení první prvek nad rámec vstupní pole data. Jinak, nastaví funkci `iosbase::failbit` v `state`. Vrátí iterovat určení první prvek nad rámec všechny předpony vstupní pole platné datum. V obou případech, pokud se rovná návratovou hodnotu `last`, nastaví funkce `ios_base::eofbit` v `state`.

Formát pro vstupní pole datum je národní prostředí, které jsou závislé. Pro výchozí národní prostředí, data vstupní pole má tvar MMM DD RRRR, kde:

- MMMM je nalezena shoda s voláním [get_monthname –](#get_monthname), udělíte v měsíci.

- DD je pořadí čísel desítkové soustavy, jejichž odpovídající číselná hodnota musí být v rozsahu [1, 31] poskytnutí den v měsíci.

- RRRR je nalezena shoda s voláním [get_year –](#get_year), udělíte v roce.

Literál prostory a čárky musí odpovídat odpovídající elementů ve vstupní pořadí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_date –](#get_date), který volá `do_get_date`.

## <a name="do_get_monthname"></a>  time_get::do_get_monthname

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu měsíce.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`iosbase` Nepoužívá se.

`state` Výstupní parametr, který nastaví elementy příslušné bitové masky pro datový proud stavu podle zda operace byla úspěšná.

`ptm` Ukazatel na to, kde je měsíc informace k uložení.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Funkce virtuální chráněného člena se pokusí vyhledat sekvenční elementy začínající na první v pořadí [ `first`, `last`) dokud má rozpoznána úplná, neprázdná měsíc vstupní pole. Pokud úspěšné, převede ji toto pole na ekvivalentní hodnotu jako součást **tm::tm\_mon**a ukládá výsledky v `ptm->tm_mon`. Vrátí iterovat určení první prvek nad rámec vstupní pole měsíc. Jinak, nastaví funkci `ios_base::failbit` v *stavu*. Vrátí iterovat určení první prvek nad rámec všechny předpony vstupní pole platný měsíc. V obou případech, pokud se rovná návratovou hodnotu `last`, nastaví funkce `ios_base::eofbit` v *stavu*.

Vstupní pole měsíc je sekvenci, která odpovídá nejdelší sadu posloupnosti specifická pro národní prostředí, například Jan, leden, Feb, února a tak dále. Převedená hodnota je počet měsíců od ledna.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_monthname –](#get_monthname), který volá `do_get_monthname`.

## <a name="do_get_time"></a>  time_get::do_get_time

A chráněná člena virtuální funkce, která je volána, analyzovat řetězec jako datum vyprodukované *X* – specifikátor pro `strftime`.

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`iosbase` Nepoužívá se.

`state` Nastaví prvky příslušné bitové masky pro datový proud stav podle zda operace byla úspěšná.

`ptm` Ukazatel na kterém má být uložena informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Funkce virtuální chráněného člena se pokusí vyhledat sekvenční elementy začínající na první v pořadí [ `first`, `last`) dokud má rozpoznána úplná, neprázdná čas vstupní pole. Pokud úspěšné, převede ji toto pole na ekvivalentní hodnotu jako komponenty **tm::tm_hour**, **tm::tm_min**, a **tm::tm_sec**a ukládá výsledky do `ptm->tm_hour`, `ptm->tm_min`, a `ptm->tm_sec`, v uvedeném pořadí. Vrátí iterovat určení první prvek nad rámec vstupní pole čas. Jinak, nastaví funkci `ios_base::failbit` v *stavu*. Vrátí iterovat určení první prvek nad rámec všechny předpony vstupní pole doby platnosti. V obou případech, pokud se rovná návratovou hodnotu `last`, nastaví funkce `ios_base::eofbit` v *stavu*.

V této implementaci vstupní pole čas má formátu hh: mm:, kde:

- HH je posloupnost desetinných míst, jejichž odpovídající číselná hodnota musí být v rozsahu [0, 24), udělíte hodinu dne.

- MM je posloupnost desetinných míst, jejichž odpovídající číselná hodnota musí být v rozsahu [0 a 60), která poskytuje minut po hodině.

- SS je posloupnost desetinných míst, jejichž odpovídající číselná hodnota musí být v rozsahu [0 a 60), která poskytuje sekund po minutě.

Literál dvojtečky musí odpovídat odpovídající elementů ve vstupní pořadí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_time –](#get_time), který volá `do_get_time`.

## <a name="do_get_weekday"></a>  time_get::do_get_weekday

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu týdnu.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`iosbase` Příznak formátu, který při sadu označuje, že symbolu měny je volitelná. jinak je vyžadována.

`state` Nastaví prvky příslušné bitové masky pro datový proud stav podle zda operace byla úspěšná.

`ptm` Ukazatel na to, kde informace den v týdnu je k uložení.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Funkce virtuální chráněného člena se pokusí vyhledat sekvenční elementy začínající na `first` v pořadí [ `first`, `last`) dokud má rozpoznána úplná, neprázdná den v týdnu vstupní pole. Pokud úspěšné, převede ji toto pole na ekvivalentní hodnotu jako součást **tm::tm\_wday**a ukládá výsledky v `ptm->tm_wday`. Vrátí iterovat určení první prvek nad rámec vstupní pole den v týdnu. Jinak, nastaví funkci `ios_base::failbit` v *stavu*. Vrátí iterovat určení první prvek nad rámec všechny předpony vstupní pole platný den v týdnu. V obou případech, pokud se rovná návratovou hodnotu `last`, nastaví funkce `ios_base::eofbit` v *stavu*.

Vstupní pole den v týdnu je sekvenci, která odpovídá nejdelší sadu posloupnosti specifická pro národní prostředí, například Sun, neděle, Mon, pondělí a tak dále. Převedená hodnota je počet dní od neděle.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_weekday –](#get_weekday), který volá `do_get_weekday`.

## <a name="do_get_year"></a>  time_get::do_get_year

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu roku.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`iosbase` Příznak formátu, který při sadu označuje, že symbolu měny je volitelná. jinak je vyžadována.

`state` Nastaví prvky příslušné bitové masky pro datový proud stav podle zda operace byla úspěšná.

`ptm` Ukazatel na to, kde je rok informace k uložení.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Funkce virtuální chráněného člena se pokusí vyhledat sekvenční elementy začínající na `first` v pořadí [ `first`, `last`) dokud má rozpoznána úplná, neprázdná roku vstupní pole. Pokud úspěšné, převede ji toto pole na ekvivalentní hodnotu jako součást **tm::tm\_roku**a ukládá výsledky v `ptm->tm_year`. Vrátí iterovat určení první prvek nad rámec vstupní pole rok. Jinak, nastaví funkci `ios_base::failbit` v *stavu*. Vrátí iterovat určení první prvek nad rámec všechny předpony vstupní pole platný rok. V obou případech, pokud se rovná návratovou hodnotu `last`, nastaví funkce `ios_base::eofbit` v *stavu*.

Vstupní pole rok je posloupnost desetinných míst, jejichž odpovídající číselná hodnota musí být v rozsahu [1900, 2036). Uložené hodnoty je tato hodnota minus 1900. V této implementaci hodnoty v rozsahu [69, 136) představují řadu let [1969, 2036). Hodnoty v rozsahu [0, 69) jsou přípustné, ale může představovat rozsahu let [1900, 1969) nebo [2000, 2069), v závislosti na konkrétní překlad prostředí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_year –](#get_year), který volá `do_get_year`.

## <a name="get"></a>  time_get::Get

Čte ze zdroje data znaků a převede je na čas, který je uložen v časové struktuře. První funkce přijímá jeden převod specifikátor a modifikátor, druhý přijímá několik.

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

`first` Vstupní iterator, která určuje, kde se spustí sekvenci má být převeden.

`last` Vstupní iterator, který označuje konec pořadí má být převeden.

`iosbase` Datový proud.

`state` Elementy příslušné bitové masky se nastavují pro stav datového proudu k označení chyb.

`ptm` Ukazatel na strukturu čas, kdy je čas k uložení.

`fmt` Převod specifikátor znak.

`mod` Znak volitelné modifikátor.

`fmt_first` Body, kde spustit formát direktivy.

`fmt_last` Bodů na konec formát direktivy.

### <a name="return-value"></a>Návratová hodnota

Vrátí iterovat na první znak po data, která byla použita k přiřazení struktura čas `*ptm`.

### <a name="remarks"></a>Poznámky

Vrátí první členská funkce `do_get(first, last, iosbase, state, ptm, fmt, mod)`.

Druhé volání funkce člen `do_get` pod kontrolou formát oddělená `[fmt_first, fmt_last)`. Formát se považuje za posloupnost pole, z nichž každý Určuje převod nula nebo více vstupních elementy oddělená `[first, last)`. Vrátí iterovat určení první nepřevedeném elementu. Existují tři druhy pole:

Procent (%), ve formátu, za nímž následuje volitelné modifikátor `mod` v sadě [EOQ #], následovaný specifikátorem převod `fmt`, nahradí `first` pomocí hodnoty vrácené `do_get(first, last, iosbase, state, ptm, fmt, mod)`. Chyba převodu nastaví `ios_base::failbit` v `state` a vrátí.

Element prázdný znak ve formátu přeskočí po nula nebo více vstupních prázdné prvky.

Jakýkoli další prvek ve formátu musí odpovídat další vstupní element, který bude přeskočena. Selhání shody nastaví `ios_base::failbit` v `state` a vrátí.

## <a name="get_date"></a>  time_get::get_date

Analyzuje řetězec jako datum vyprodukované *x* – specifikátor pro `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`iosbase` Příznak formátu, který při sadu označuje, že symbolu měny je volitelná. jinak je vyžadována.

`state` Nastaví prvky příslušné bitové masky pro datový proud stav podle zda operace byla úspěšná.

`ptm` Ukazatel na kterém má být uložena informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [do_get_date –](#do_get_date)( `first`, `last`, `iosbase`, `state`, `ptm`).

Všimněte si, že měsíců, se počítají od 0 do 11.

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

## <a name="get_monthname"></a>  time_get::get_monthname

Analyzuje řetězec jako název měsíce.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`iosbase` Nepoužívá se.

`state` Výstupní parametr, který nastaví elementy příslušné bitové masky pro datový proud stavu podle zda operace byla úspěšná.

`ptm` Ukazatel na to, kde je měsíc informace k uložení.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [do_get_monthname –](#do_get_monthname)( `first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="get_time"></a>  time_get::get_time

Analyzuje řetězec jako datum vyprodukované *X* – specifikátor pro `strftime`.

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`iosbase` Nepoužívá se.

`state` Nastaví prvky příslušné bitové masky pro datový proud stav podle zda operace byla úspěšná.

`ptm` Ukazatel na kterém má být uložena informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [do_get_time –](#do_get_time)( `first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="get_weekday"></a>  time_get::get_weekday

Analyzuje řetězec jako název dne v týdnu.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`iosbase` Příznak formátu, který při sadu označuje, že symbolu měny je volitelná. jinak je vyžadována.

`state` Nastaví prvky příslušné bitové masky pro datový proud stav podle zda operace byla úspěšná.

`ptm` Ukazatel na to, kde informace den v týdnu je k uložení.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [do_get_weekday –](#do_get_weekday)( `first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="get_year"></a>  time_get::get_year

Analyzuje řetězec jako název roku.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`iosbase` Příznak formátu, který při sadu označuje, že symbolu měny je volitelná. jinak je vyžadována.

`state` Nastaví prvky příslušné bitové masky pro datový proud stav podle zda operace byla úspěšná.

`ptm` Ukazatel na to, kde je rok informace k uložení.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [do_get_year –](#do_get_year)( `first`, `last`, `iosbase`, `state`, `ptm`).

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

## <a name="iter_type"></a>  time_get::iter_type

Typ, který popisuje vstupní iterátor.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **InputIterator**.

## <a name="time_get"></a>  time_get::time_get

V konstruktoru pro objekty typu `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

`refs` Celočíselná hodnota určuje typ správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty `refs` parametrů a jejich významu jsou:

- 0: doba života objektu spravuje národní prostředí, které je obsahují.

- 1: doba života objektu, se musí ručně spravovat.

- \> 1: tyto hodnoty nejsou definovány.

Žádné přímé příklady je možné, protože je chráněn destruktoru.

Konstruktor inicializuje jeho základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)( `refs`).

## <a name="see-also"></a>Viz také

[\<národní prostředí >](../standard-library/locale.md)<br/>
[time_base – třída](../standard-library/time-base-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
