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
ms.openlocfilehash: 2c0ae501693a8abffc72a23be9c427f31bad65b6
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867310"
---
# <a name="time_put-class"></a>time_put – třída

Šablona třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu časových hodnot na sekvence typu `CharType`.

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
|[do_put](#do_put)|Virtuální funkce, která vypisuje informace o čase a datu jako posloupnost `CharType`s.|
|[převést](#put)|Vytvoří výstup informací o čase a datu v posloupnosti `CharType`s.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Obor názvů:** std

## <a name="char_type"></a>time_put:: char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `CharType`.

## <a name="do_put"></a>time_put::d o_put

Virtuální funkce, která vypisuje informace o čase a datu jako posloupnost `CharType`s.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parametry

*další*\
Výstupní iterátor, kde má být vložena posloupnost znaků reprezentujících čas a datum.

*_Iosbase*\
Nepoužívá se.

*_Pt*\
Výstup informací o čase a datu.

*_Fmt*\
Formát výstupu. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

*_Mod*\
Modifikátor pro formát. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

### <a name="return-value"></a>Návratová hodnota

Iterátor na první pozici po vložení posledního elementu.

### <a name="remarks"></a>Poznámky

Členská funkce Virtual Protected generuje sekvenční prvky začínající na `next` z hodnot času uložených v objektu \* `_Pt`, typu `tm`. Funkce vrátí iterátor, který určuje další místo pro vložení elementu za generovaný výstup.

Výstup je vygenerován stejnými pravidly, které používá `strftime`, s posledním argumentem *_Pt*pro generování řady elementů typu **char** v poli. U každého takového elementu **char** se předpokládá mapování na ekvivalentní prvek typu `CharType` jednoduchým mapováním 1:1. Pokud je *_Mod* rovna nule, je platný formát "% F", kde F je nahrazen *_Fmt*. V opačném případě je platný formát "% MF", kde M je nahrazeno *_Mod*.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Put](#put), který volá `do_put`.

## <a name="iter_type"></a>time_put:: iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `OutputIterator`.

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

*další*\
Výstupní iterátor, kde má být vložena posloupnost znaků reprezentujících čas a datum.

*_Iosbase*\
Nepoužívá se.

*_Fill*\
Znak typu `CharType` použitý pro mezery

*_Pt*\
Výstup informací o čase a datu.

*_Fmt*\
Formát výstupu. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

*_Mod*\
Modifikátor pro formát. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

*první*\
Začátek formátovacího řetězce pro výstup. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

*poslední*\
Konec formátovacího řetězce pro výstup. Platné hodnoty najdete v tématu [strftime, wcsftime, _strftime_l _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) .

### <a name="return-value"></a>Návratová hodnota

Iterátor na první pozici po vložení posledního elementu.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [do_put](#do_put)(`next`, `_Iosbase`, `_Fill`, `_Pt`, `_Fmt`, `_Mod`). Druhá členská funkce kopíruje do \* `next` + + libovolný prvek v intervalu [`first`, `last`) jiné než procento (%). V procentech, po kterých následuje znak *C* v intervalu [`first`, `last`), funkce místo toho vyhodnotí `next` = `do_put`(`next`, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) a přeskočí předchozí *C*. Pokud *je však* znak kvalifikátoru ze sady EOQ # následovaný znakem `C2` v intervalu [`first`, `last`), funkce místo toho vyhodnotí `next` = `do_put`(`next`, `_Iosbase`, `_Fill`, `_Pt`, `C2`, *C*) a přeskočí minulé `C2`.

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

## <a name="time_put"></a>time_put:: time_put

Konstruktor pro objekty typu `time_put`.

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *_Refs* a jejich význam jsou:

- 0: životnost objektu je spravována místními objekty, které jej obsahují.

- 1: životnost objektu musí být ručně spravovaná.

- \> 1: tyto hodnoty nejsou definovány.

Konstruktor inicializuje svůj základní objekt pomocí [locale:: Face](../standard-library/locale-class.md#facet_class)( *_Refs*).

## <a name="see-also"></a>Viz také

[\<> národního prostředí](../standard-library/locale.md)\
[time_base\ třídy](../standard-library/time-base-class.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
