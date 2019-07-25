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
ms.openlocfilehash: 73f4cdd0028164ce5f8215258c517c2e59eb7538
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459947"
---
# <a name="timeput-class"></a>time_put – třída

Třída šablony popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu časových hodnot na sekvence typu `CharType`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ používaný v rámci programu ke kódování znaků.

*OutputIterator*\
Typ iterátoru, do kterého časové funkce zapisují svůj výstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v ID jedinečnou kladnou hodnotu **.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[time_put](#time_put)|Konstruktor pro objekty typu `time_put`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje výstupní iterátor.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_put](#do_put)|Virtuální funkce, která vypisuje informace o čase a datu v pořadí `CharType`s.|
|[převést](#put)|Vytvoří výstup informací o čase a datu v posloupnosti `CharType`s.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="char_type"></a>time_put::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `CharType`šablony.

## <a name="do_put"></a>time_put::d o_put

Virtuální funkce, která vypisuje informace o čase a datu v pořadí `CharType`s.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parametry

*generace*\
Výstupní iterátor, kde má být vložena posloupnost znaků reprezentujících čas a datum.

*_Iosbase*\
Nepoužívané.

*_Pt*\
Výstup informací o čase a datu.

*_Fmt*\
Formát výstupu. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

*_Mod*\
Modifikátor pro formát. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

### <a name="return-value"></a>Návratová hodnota

Iterátor na první pozici po vložení posledního elementu.

### <a name="remarks"></a>Poznámky

Členská funkce Virtual Protected generuje sekvenční prvky začínající `next` v čase uložené v objektu \* `_Pt`typu `tm`. Funkce vrátí iterátor, který určuje další místo pro vložení elementu za generovaný výstup.

Výstup je vygenerován stejnými pravidly `strftime`, které používá, s posledním argumentem *_Pt*, pro generování řady elementů typu **char** do pole. U každého takového elementu **char** se předpokládá mapování na ekvivalentní prvek typu `CharType` jednoduchým mapováním 1:1. Pokud se *_Mod* rovná nule, je platný formát "% F", kde F je nahrazeno *_Fmt*. V opačném případě je platný formát "% MF", kde M je nahrazeno *_Mod*.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [vložení](#put), která `do_put`volá.

## <a name="iter_type"></a>time_put::iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `OutputIterator`šablony.

## <a name="put"></a>time_put::p UT

Vytvoří výstup informací o čase a datu v posloupnosti `CharType`s.

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

*generace*\
Výstupní iterátor, kde má být vložena posloupnost znaků reprezentujících čas a datum.

*_Iosbase*\
Nepoužívané.

*_Fill*\
Znak typu `CharType` použitý pro mezery

*_Pt*\
Výstup informací o čase a datu.

*_Fmt*\
Formát výstupu. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

*_Mod*\
Modifikátor pro formát. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

*první*\
Začátek formátovacího řetězce pro výstup. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

*posledního*\
Konec formátovacího řetězce pro výstup. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

### <a name="return-value"></a>Návratová hodnota

Iterátor na první pozici po vložení posledního elementu.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [do_put](#do_put)(`next`, `_Iosbase`, `_Fill`, `_Pt`, `_Fmt`, `_Mod`). Druhá členská funkce kopíruje \* do `next` + + libovolný prvek v intervalu [ `first`, `last`), který je jiný než procento (%). Pro procentní podíl následovaný znakem *C* v `first`intervalu [, `do_put` `last` `next` `next`  = ) funkce místo toho vyhodnotí (, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) a přeskočí předchozí *C*. Pokud je však *C* znak kvalifikátor ze sady EOQ # a za ním `C2` následuje znak v intervalu [ `first`, `last`), funkce místo toho vyhodnotí `next`(  =  `do_put` `next`, `_Iosbase` `C2` , `_Fill` ,`C2`, ,C)apřeskočíminulosti`_Pt`.

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

## <a name="time_put"></a>time_put::time_put

Konstruktor pro objekty typu `time_put`

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *_Refs* a jejich význam jsou:

- 0: Životnost objektu je spravována národními prostředími, která jej obsahují.

- 1: Životnost objektu musí být ručně spravovaná.

- \> 1: Tyto hodnoty nejsou definovány.

Konstruktor inicializuje svůj základní objekt pomocí [locale:: Face](../standard-library/locale-class.md#facet_class)( *_Refs*).

## <a name="see-also"></a>Viz také:

[\<> národního prostředí](../standard-library/locale.md)\
[time_base – třída](../standard-library/time-base-class.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
