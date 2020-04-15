---
title: time_put – třída
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
ms.openlocfilehash: 10691de0a583dc7d5a66c319968d90978bf59480
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368000"
---
# <a name="time_put-class"></a>time_put – třída

Šablona třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí `CharType`pro řízení převodů hodnot času na sekvence typu .

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků.

*Výstupní iterátor*\
Typ iterátoru, do kterého časové funkce zapisují svůj výstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložená hodnota ukládá jedinečnou kladnou hodnotu v **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[time_put](#time_put)|Konstruktor pro objekty `time_put`typu .|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje výstupní iterátor.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_put](#do_put)|Virtuální funkce, která vyvezuje `CharType`informace o čase a datu jako posloupnost s.|
|[Dát](#put)|Vyveze informace o čase `CharType`a datu jako posloupnost s.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="time_putchar_type"></a><a name="char_type"></a>time_put::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `CharType`parametr šablony .

## <a name="time_putdo_put"></a><a name="do_put"></a>time_put::do_put

Virtuální funkce, která vyvezuje `CharType`informace o čase a datu jako posloupnost s.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parametry

*Další*\
Výstupní iterátor, kde mají být vloženy posloupnosti znaků představujícíčas a datum.

*_Iosbase*\
Nepoužívá se.

*_Pt*\
Informace o čase a datu jsou výstupem.

*_Fmt*\
Formát výstupu. Platné hodnoty naleznete [v tématu strftime, wcsftime, _strftime_l, _wcsftime_l.](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

*_Mod*\
Modifikátor pro formát. Platné hodnoty naleznete [v tématu strftime, wcsftime, _strftime_l, _wcsftime_l.](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

### <a name="return-value"></a>Návratová hodnota

Iterátor na první pozici po poslední vložený prvek.

### <a name="remarks"></a>Poznámky

Virtuální chráněná členská funkce generuje `next` sekvenční prvky začínající od časových hodnot uložených v objektu \* `_Pt`typu `tm`. Funkce vrátí iterátor určení další místo vložit prvek mimo generovaný výstup.

Výstup je generován stejnými pravidly, která `strftime`používají , s posledním argumentem *_Pt*, pro generování řady **znaků** do pole. Předpokládá se, že každý takový **znakový** `CharType` prvek je mapován na ekvivalentní prvek typu jednoduchým mapováním 1:1. Pokud *_Mod* rovná nule, efektivní formát je "%F", kde F je nahrazen *_Fmt*. V opačném případě je efektivní formát "%MF", kde m je nahrazen *_Mod*.

### <a name="example"></a>Příklad

Viz příklad pro [put](#put) `do_put`, který volá .

## <a name="time_putiter_type"></a><a name="iter_type"></a>time_put::iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `OutputIterator`parametr šablony .

## <a name="time_putput"></a><a name="put"></a>time_put::put

Vyveze informace o čase `CharType`a datu jako posloupnost s.

```cpp
iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;

iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Další*\
Výstupní iterátor, kde mají být vloženy posloupnosti znaků představujícíčas a datum.

*_Iosbase*\
Nepoužívá se.

*_Fill*\
Znak typu `CharType` použitý pro mezery.

*_Pt*\
Informace o čase a datu jsou výstupem.

*_Fmt*\
Formát výstupu. Platné hodnoty naleznete [v tématu strftime, wcsftime, _strftime_l, _wcsftime_l.](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

*_Mod*\
Modifikátor pro formát. Platné hodnoty naleznete [v tématu strftime, wcsftime, _strftime_l, _wcsftime_l.](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

*První*\
Začátek řetězce formátování pro výstup. Platné hodnoty naleznete [v tématu strftime, wcsftime, _strftime_l, _wcsftime_l.](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

*Poslední*\
Konec řetězce formátování pro výstup. Platné hodnoty naleznete [v tématu strftime, wcsftime, _strftime_l, _wcsftime_l.](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

### <a name="return-value"></a>Návratová hodnota

Iterátor na první pozici po poslední vložený prvek.

### <a name="remarks"></a>Poznámky

První členská funkce`next`vrátí `_Iosbase` `_Fill` [do_put](#do_put) `_Fmt`( `_Mod`, , `_Pt`, . . . . Druhá členská funkce \* `next` zkopíruje do ++ `first` `last`libovolný prvek v intervalu [ , ) kromě procenta (%). Pro procento následované znakem *C* `first`v `last`intervalu [ `next`  =  `do_put`, `next` `_Iosbase`) `_Fill` `_Pt`funkce místo toho vyhodnotí ( , , , *C*, 0) a přeskočí kolem *C*. Pokud je však *C* kvalifikátorznak z množiny `C2` EOQ#, následovaný znakem `next`  =  `do_put` `next`v `_Iosbase` `_Fill`intervalu `C2`[ `first`, `last`), funkce místo toho vyhodnotí ( , , , `_Pt` *, C*) a přeskočí minulost `C2`.

### <a name="example"></a>Příklad

```cpp
// time_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   t.tm_hour = 5;
   t.tm_min = 30;
   t.tm_sec = 40;
   t.tm_year = 00;
   t.tm_mday = 4;
   t.tm_mon = 6;

   pszPutI.imbue( loc );
   char *pattern = "x: %X %x";
   use_facet <time_put <char> >
   (loc).put(basic_ostream<char>::_Iter(pszPutI.rdbuf( )),
          pszPutI, ' ', &t, pattern, pattern+strlen(pattern));

      cout << "num_put( ) = " << pszPutI.rdbuf( )->str( ) << endl;

      char strftimebuf[255];
      strftime(&strftimebuf[0], 255, pattern, &t);
      cout << "strftime( ) = " << &strftimebuf[0] << endl;
}
```

```Output
num_put( ) = x: 05:30:40 07/04/00
strftime( ) = x: 05:30:40 07/04/00
```

## <a name="time_puttime_put"></a><a name="time_put"></a>time_put::time_put

Konstruktor pro objekty typu `time_put`.

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Celá hodnota používaná k určení typu správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* a jejich význam jsou:

- 0: Životnost objektu je spravována národními prostředími, které jej obsahují.

- 1: Životnost objektu musí být spravována ručně.

- \>1: Tyto hodnoty nejsou definovány.

Konstruktor inicializuje svůj základní objekt pomocí [národního prostředí::omezující fasety](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)\
[time_base třída](../standard-library/time-base-class.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
