---
title: time_get – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 9ff44c6352224b65d712161a62d34b34ee858ad6
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102743"
---
# <a name="timeget-class"></a>time_get – třída

Třída šablony popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu sekvencí typu `CharType` na hodnoty času.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Parametry

*CharType*  
Typ používaný v rámci programu ke kódování znaků.

*InputIterator*  
Iterátor, ze kterého se čtou hodnoty času.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložené hodnotě uloží jedinečnou kladnou hodnotu v **id.**

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
|[do_get_date](#do_get_date)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako data vytvořeného `x` specifikátor pro `strftime`.|
|[do_get_monthname](#do_get_monthname)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu měsíce.|
|[do_get_time](#do_get_time)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako data vytvořeného `X` specifikátor pro `strftime`.|
|[do_get_weekday](#do_get_weekday)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu týdnu.|
|[do_get_year](#do_get_year)|Chráněná virtuální členská funkce, která je volána k analýze řetězce jako názvu roku.|
|[get](#get)|Čte ze zdroje data znaků a převede je na čas, který je uložen v časové struktuře.|
|[get_date](#get_date)|Analyzuje řetězec jako datum vygenerované `x` specifikátor pro `strftime`.|
|[get_monthname –](#get_monthname)|Analyzuje řetězec jako název měsíce.|
|[get_time](#get_time)|Analyzuje řetězec jako datum vygenerované `X` specifikátor pro `strftime`.|
|[get_weekday](#get_weekday)|Analyzuje řetězec jako název dne v týdnu.|
|[get_year –](#get_year)|Analyzuje řetězec jako název roku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

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

Pořadí data používaného omezující vlastností.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_date_order –](#do_date_order).

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

Pořadí data používaného omezující vlastností.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrátí hodnotu typu **time_base::dateorder**, která popisuje pořadí, ve které datum komponent odpovídajících [do_get_date –](#do_get_date). V této implementaci je hodnota **time_base::mdy**, odpovídající data ve formátu 2 prosince 1979.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [date_order –](#date_order), který volá `do_date_order`.

## <a name="do_get"></a>  time_get::do_get

Čte a převede data znaků na hodnotu času. Přijímá jeden konverznímu specifikátoru a modifikátor.

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

*první*<br/>
Iterátor vstupu, který označuje začátek sekvence pro převod.

*poslední*<br/>
Iterátor vstupu, který označuje konec sekvence.

*iosbase*<br/>
Objekt datového proudu.

*Stav*<br/>
Pole v iosbase kde prvky odpovídající bitové masky jsou nastavené pro označení chyb.

*druh*<br/>
Ukazatele na strukturu čas, ve kterém má být uložen čas.

*FMT*<br/>
Znak specifikátoru převodu.

*MOD*<br/>
Znak volitelný modifikátor.

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor, který určuje první prvek nepřevedeném. Chyba převodu nastaví `ios_base::failbit` v `state` a vrátí *první*.

### <a name="remarks"></a>Poznámky

Virtuální členská funkce převede a přeskočí jednu nebo více vstupních prvků v rozsahu [`first`, `last`) k určení hodnoty uložené v jedné nebo více členů `*pt`. Chyba převodu nastaví `ios_base::failbit` v `state` a vrátí *první*. V opačném případě funkce vrátí iterátor s vyznačením nepřevedeném první prvek.

Specifikátory převodu jsou:

`'a'` nebo `'A'` – se chová stejně jako [time_get::get_weekday](#get_weekday).

`'b'`, `'B'`, nebo `'h'` – se chová stejně jako [time_get::get_monthname](#get_monthname).

`'c'` --se chová stejně jako `"%b %d %H : %M : %S %Y"`.

`'C'` --převede na hodnotu decimal vstupního pole v rozsahu [0, 99] `val` a ukládá `val * 100 - 1900` v `pt-&tm_year`.

`'d'` nebo `'e'` – Převede desítkové vstupního pole v rozsahu [1, 31] a uloží svou hodnotu v `pt-&tm_mday`.

`'D'` --se chová stejně jako `"%m / %d / %y"`.

`'H'` --Převede desítkové vstupního pole v rozsahu [0, 23] a uloží svou hodnotu v `pt-&tm_hour`.

`'I'` --Převede desítkové vstupního pole v rozsahu [0, 11] a uloží svou hodnotu v `pt-&tm_hour`.

`'j'` --Převede desítkové vstupního pole v rozsahu [1, 366] a uloží svou hodnotu v `pt-&tm_yday`.

`'m'` --převede na hodnotu decimal vstupního pole v rozsahu [1, 12] `val` a ukládá `val - 1` v a uloží svou hodnotu v `pt-&tm_mon`.

`'M'` --Převede desítkové vstupního pole v rozsahu [0, 59] a uloží svou hodnotu v `pt-&tm_min`.

`'n'` nebo `'t'` – se chová stejně jako `" "`.

`'p'` --Převede "Teď" nebo "am" na nulu a "Odp." nebo "Odp." 12 a přidá tuto hodnotu a `pt-&tm_hour`.

`'r'` --se chová stejně jako `"%I : %M : %S %p"`.

`'R'` --se chová stejně jako `"%H %M"`.

`'S'` --Převede desítkové vstupního pole v rozsahu [0, 59] a uloží svou hodnotu v `pt-&tm_sec`.

`'T'` nebo `'X'` – se chová stejně jako `"%H : %M : S"`.

`'U'` --Převede desítkové vstupního pole v rozsahu [0, 53] a uloží svou hodnotu v `pt-&tm_yday`.

`'w'` --Převede desítkové vstupního pole v rozsahu [0, 6] a uloží svou hodnotu v `pt-&tm_wday`.

`'W'` --Převede desítkové vstupního pole v rozsahu [0, 53] a uloží svou hodnotu v `pt-&tm_yday`.

`'x'` --se chová stejně jako `"%d / %m / %y"`.

`'y'` --převede na hodnotu decimal vstupního pole v rozsahu [0, 99] `val` a ukládá `val < 69  val + 100 : val` v `pt-&tm_year`.

`'Y'` --se chová stejně jako [time_get::get_year](#get_year).

Všechny ostatní sady specifikátoru převodu `ios_base::failbit` v `state` a vrátí. V této implementaci jakékoli modifikační nemá žádný vliv.

## <a name="do_get_date"></a>  time_get::do_get_date

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako data vytvořeného *x* specifikátor pro `strftime`.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*  
Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*  
Vstupní iterátor adresující konec sekvence má být převeden.

*iosbase*  
Příznak formátu, který při nastavení znamená, že symbol měny je volitelná. v opačném případě je povinný.

*Stav*  
Nastaví prvky odpovídající bitové masky pro stav datového proudu podle Určuje, zda byla operace úspěšná.

*druh*  
Ukazatel na ve kterém se uloží informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí porovnat sekvenční začínající na první v pořadí elementů [ `first`, `last`) dokud rozpoznal kompletní, neprázdné datum vstupní pole. Pokud úspěšné, převede toto pole na její ekvivalentní hodnotu jako součásti **tm::tm\_pondělí**, **tm::tm\_den**, a **tm::tm\_rok** a ukládá výsledky `ptm->tm_mon`, `ptm->tm_day`, a `ptm->tm_year`v uvedeném pořadí. Vrátí iterátor určení prvního prvku mimo pole vstupní data. Jinak, funkce nastaví `iosbase::failbit` v *stavu*. Vrátí iterátor určení prvního prvku mimo jakoukoli předponu vstupní pole platné datum. V obou případech, pokud je návratová hodnota *poslední*, funkce nastaví `ios_base::eofbit` v *stavu*.

Formát pro vstupní pole datum je závislé na národním prostředí. Pro výchozí národní prostředí, v poli vstupní datum má formulář MMM DD, rrrr, kde:

- MMM je nalezena shoda s voláním [get_monthname –](#get_monthname), poskytuje měsíce.

- DD je posloupnost desítková číslice jehož odpovídající číselná hodnota musí být v rozsahu [1, 31] poskytuje den v měsíci.

- RRRR je nalezena shoda s voláním [get_year –](#get_year), poskytující v roce.

Literál mezery a čárky musí odpovídat odpovídající elementy ve vstupní sekvence.

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

*první*  
Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*  
Vstupní iterátor adresující konec sekvence má být převeden.

*iosbase*  
Nevyužité.

*Stav*  
Výstupní parametr, který nastaví prvky odpovídající bitové masky pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*druh*  
Ukazatel na umístění informace měsíce mají být uloženy.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí porovnat sekvenční začínající na první v pořadí elementů [ `first`, `last`) dokud rozpoznal kompletní, prázdný měsíc vstupní pole. Pokud úspěšné, převede toto pole na její ekvivalentní hodnotu jako součást **tm::tm\_pondělí**a uloží výsledek v `ptm->tm_mon`. Vrátí iterátor určení prvního prvku mimo měsíc vstupní pole. Jinak, funkce nastaví `ios_base::failbit` v *stavu*. Vrátí iterátor určení prvního prvku mimo jakoukoli předponu platný měsíc vstupní pole. V obou případech, pokud je návratová hodnota *poslední*, funkce nastaví `ios_base::eofbit` v *stavu*.

Vstupní pole měsíc je sekvenci, která odpovídá nejdelší sadu pořadí specifických pro národní prostředí, jako je Jan, leden, únor, dne a tak dále. Převedená hodnota je počet měsíců od ledna.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_monthname –](#get_monthname), který volá `do_get_monthname`.

## <a name="do_get_time"></a>  time_get::do_get_time

Chráněná virtuální členská funkce, která je volána k analýze řetězce jako data vytvořeného *X* specifikátor pro `strftime`.

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*  
Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*  
Vstupní iterátor adresující konec sekvence má být převeden.

*iosbase*  
Nevyužité.

*Stav*  
Nastaví prvky odpovídající bitové masky pro stav datového proudu podle Určuje, zda byla operace úspěšná.

*druh*  
Ukazatel na ve kterém se uloží informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí porovnat sekvenční začínající na první v pořadí elementů [ `first`, `last`) dokud rozpoznal kompletní, prázdný čas vstupní pole. Pokud úspěšné, převede toto pole na její ekvivalentní hodnotu jako součásti `tm::tm_hour`, `tm::tm_min`, a `tm::tm_sec`a ukládá výsledky `ptm->tm_hour`, `ptm->tm_min`, a `ptm->tm_sec`v uvedeném pořadí. Vrátí iterátor určení prvního prvku mimo dobu vstupní pole. Jinak, funkce nastaví `ios_base::failbit` v *stavu*. Vrátí iterátor určení prvního prvku mimo jakoukoli předponu platný čas vstupní pole. V obou případech, pokud je návratová hodnota *poslední*, funkce nastaví `ios_base::eofbit` v *stavu*.

V této implementaci vstupní pole časového má tvar hh: mm:, kde:

- HH jsou posloupnost desítková číslice, jehož odpovídající číselná hodnota musí být v rozsahu [0, 24), poskytuje hodinu dne.

- MM je posloupnost desítková číslice, jehož odpovídající číselná hodnota musí být v rozsahu [0, 60), poskytuje minut po hodině.

- SS je posloupnost desítková číslice, jehož odpovídající číselná hodnota musí být v rozsahu [0, 60), poskytuje sekund po minutě.

Literál dvojtečky musí odpovídat odpovídající elementy ve vstupní sekvence.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_time](#get_time), který volá `do_get_time`.

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

*první*  
Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*  
Vstupní iterátor adresující konec sekvence má být převeden.

*iosbase*  
Příznak formátu, který při nastavení znamená, že symbol měny je volitelná. v opačném případě je povinný.

*Stav*  
Nastaví prvky odpovídající bitové masky pro stav datového proudu podle Určuje, zda byla operace úspěšná.

*druh*  
Ukazatel na kde se uloží informace o den v týdnu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí porovnat sekvenční prvky počínaje *první* v sekvenci [ `first`, `last`) dokud rozpoznal kompletní, den v týdnu prázdný vstupní pole. Pokud úspěšné, převede toto pole na její ekvivalentní hodnotu jako součást **tm::tm\_wday**a uloží výsledek v `ptm->tm_wday`. Vrátí iterátor určení prvního prvku mimo vstupní pole den v týdnu. Jinak, funkce nastaví `ios_base::failbit` v *stavu*. Vrátí iterátor určení prvního prvku mimo jakoukoli předponu vstupní pole platný den v týdnu. V obou případech, pokud je návratová hodnota *poslední*, funkce nastaví `ios_base::eofbit` v *stavu*.

Vstupní pole den v týdnu je sekvence, která odpovídá nejdelší sadu pořadí specifických pro národní prostředí, jako je například Sun, neděle, pondělí, pondělí a tak dále. Převedená hodnota je počet dnů od neděle.

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

*první*  
Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*  
Vstupní iterátor adresující konec sekvence má být převeden.

*iosbase*  
Příznak formátu, který při nastavení znamená, že symbol měny je volitelná. v opačném případě je povinný.

*Stav*  
Nastaví prvky odpovídající bitové masky pro stav datového proudu podle Určuje, zda byla operace úspěšná.

*druh*  
Ukazatel na kdy informace roku se uloží.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí porovnat sekvenční prvky počínaje *první* v sekvenci [ `first`, `last`) dokud rozpoznal kompletní, prázdný rok vstupní pole. Pokud úspěšné, převede toto pole na její ekvivalentní hodnotu jako součást **tm::tm\_rok**a uloží výsledek v `ptm->tm_year`. Vrátí iterátor určení prvního prvku mimo vstupní pole year. Jinak, funkce nastaví `ios_base::failbit` v *stavu*. Vrátí iterátor určení prvního prvku mimo jakoukoli předponu vstupní pole platný rok. V obou případech, pokud je návratová hodnota *poslední*, funkce nastaví `ios_base::eofbit` v *stavu*.

Vstupní pole year je posloupnost desítková číslice, jehož odpovídající číselná hodnota musí být v rozsahu [1900, 2036). Uložené hodnoty je tato hodnota minus 1900. V této implementaci hodnoty v rozsahu [69, 136) představují řadu let [1969, 2036). Hodnoty v rozmezí [0, 69) jsou přípustné, ale může představovat rozsah let [1900, 1969) nebo [2000, 2069), v závislosti na konkrétním prostředí posunutí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [get_year –](#get_year), který volá `do_get_year`.

## <a name="get"></a>  time_get::Get

Čte ze zdroje data znaků a převede je na čas, který je uložen v časové struktuře. První funkce přijímá jeden konverznímu specifikátoru a modifikátor, druhý přijímá několik.

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

*první*  
Vstupní iterátor, který označuje, kde začíná sekvence má být převeden.

*poslední*  
Vstupní iterátor, který označuje konec sekvence má být převeden.

*iosbase*  
Datový proud.

*Stav*  
Prvky odpovídající bitové masky jsou nastavené pro stav datového proudu pro označení chyb.

*druh*  
Ukazatel na čas strukturu, ve kterém má být uložen čas.

*FMT*  
Znak specifikátoru převodu.

*MOD*  
Znak volitelný modifikátor.

*fmt_first*  
Odkazuje na kde začít direktivy formátu.

*fmt_last*  
Odkazuje na konci direktivy formátu.

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor na první znak za data, která byla použita k přiřazení časové struktuře `*ptm`.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí `do_get(first, last, iosbase, state, ptm, fmt, mod)`.

Druhé volání funkcí členských `do_get` pod kontrolou formátu oddělené `[fmt_first, fmt_last)`. Zpracovává formátu jako posloupnost polí, z nichž každý Určuje převod nula nebo více vstupních prvků oddělená `[first, last)`. Vrátí iterátor s vyznačením nepřevedeném první prvek. Existují tři typy polí:

Procent (%), ve formátu, následovaný volitelný modifikátor *mod* v sadě [EOQ #], za nímž následuje specifikátoru převodu *fmt*, nahradí *první* s hodnotou vrácenou `do_get(first, last, iosbase, state, ptm, fmt, mod)`. Chyba převodu nastaví `ios_base::failbit` v *stavu* a vrátí.

Element prázdné znaky ve formátu přeskočí za nulu nebo více vstupních prvků prázdné znaky.

Jiný prvek ve formátu musí odpovídat další vstupní element, který se přeskočí. Selhání shody nastaví `ios_base::failbit` v *stavu* a vrátí.

## <a name="get_date"></a>  time_get::get_date

Analyzuje řetězec jako datum vygenerované *x* specifikátor pro `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*  
Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*  
Vstupní iterátor adresující konec sekvence má být převeden.

*iosbase*  
Příznak formátu, který při nastavení znamená, že symbol měny je volitelná. v opačném případě je povinný.

*Stav*  
Nastaví prvky odpovídající bitové masky pro stav datového proudu podle Určuje, zda byla operace úspěšná.

*druh*  
Ukazatel na ve kterém se uloží informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_get_date –](#do_get_date)(`first`, `last`, `iosbase`, `state`, `ptm`).

Všimněte si, že měsíců jsou počítány od 0 do 11.

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

*první*  
Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*  
Vstupní iterátor adresující konec sekvence má být převeden.

*iosbase*  
Nevyužité.

*Stav*  
Výstupní parametr, který nastaví prvky odpovídající bitové masky pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*druh*  
Ukazatel na umístění informace měsíce mají být uloženy.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_get_monthname –](#do_get_monthname)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

Analyzuje řetězec jako datum vygenerované *X* specifikátor pro `strftime`.

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*první*  
Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*  
Vstupní iterátor adresující konec sekvence má být převeden.

*iosbase*  
Nevyužité.

*Stav*  
Nastaví prvky odpovídající bitové masky pro stav datového proudu podle Určuje, zda byla operace úspěšná.

*druh*  
Ukazatel na ve kterém se uloží informace o datu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_get_time –](#do_get_time)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

*první*  
Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*  
Vstupní iterátor adresující konec sekvence má být převeden.

*iosbase*  
Příznak formátu, který při nastavení znamená, že symbol měny je volitelná. v opačném případě je povinný.

*Stav*  
Nastaví prvky odpovídající bitové masky pro stav datového proudu podle Určuje, zda byla operace úspěšná.

*druh*  
Ukazatel na kde se uloží informace o den v týdnu.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_get_weekday –](#do_get_weekday)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

*první*  
Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*  
Vstupní iterátor adresující konec sekvence má být převeden.

*iosbase*  
Příznak formátu, který při nastavení znamená, že symbol měny je volitelná. v opačném případě je povinný.

*Stav*  
Nastaví prvky odpovídající bitové masky pro stav datového proudu podle Určuje, zda byla operace úspěšná.

*druh*  
Ukazatel na kdy informace roku se uloží.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek nad rámec vstupní pole.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_get_year –](#do_get_year)(`first`, `last`, `iosbase`, `state`, `ptm`).

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

Konstruktor pro objekty typu `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

*odolný systém souborů*  
Celočíselná hodnota určuje typ Správa paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *odolný systém souborů* parametrů a jejich význam:

- 0: Životnost objektu se spravuje přes národní prostředí, které je obsahují.

- 1: doba života objektu je nutné ručně spravovat.

- \> 1: tyto hodnoty nejsou definovány.

Žádné přímé příklady je to možné, protože destruktor je chráněn.

Konstruktor inicializuje jeho základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)(`refs`).

## <a name="see-also"></a>Viz také:

[\<národní prostředí >](../standard-library/locale.md)<br/>
[time_base – třída](../standard-library/time-base-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
