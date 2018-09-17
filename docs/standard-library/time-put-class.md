---
title: time_put – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
dev_langs:
- C++
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27a200ba94be8c4937342820fadf89e4225ba97d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719950"
---
# <a name="timeput-class"></a>time_put – třída

Třída šablony popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodů hodnot času na sekvence typu `CharType`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ používaný v rámci programu ke kódování znaků.

*OutputIterator*<br/>
Typ iterátoru, do kterého časové funkce zapisují svůj výstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložené hodnotě uloží jedinečnou kladnou hodnotu v **id.**

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
|[do_put](#do_put)|Virtuální funkce, jejichž výstupem jsou informace data a času jako sekvenci `CharType`s.|
|[Vložit](#put)|Výstup informací data a času jako sekvenci `CharType`s.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="char_type"></a>  time_put::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `CharType`.

## <a name="do_put"></a>  time_put::do_put

Virtuální funkce, jejichž výstupem jsou informace data a času jako sekvenci `CharType`s.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parametry

*next*<br/>
Výstupní iterátor, kde posloupnost znaků představující datum a čas mají být vloženy.

*_Iosbase*<br/>
Nevyužité.

*_Pt*<br/>
Informace data a času vytváří výstup.

*_Fmt*<br/>
Formát výstupu. Zobrazit [strftime, wcsftime, _strftime_l, _wcsftime_l – –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

*_Mod*<br/>
Modifikátor formátu. Zobrazit [strftime, wcsftime, _strftime_l, _wcsftime_l – –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

### <a name="return-value"></a>Návratová hodnota

Iterátor na první pozici za posledním prvkem vložen.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce generuje sekvenční prvky počínaje `next` z hodnot čas uloženou v objektu \* `_Pt`, typu `tm`. Vrátí iterátor s vyznačením další místo na vkládání elementů nad rámec generovaný výstup.

Výstup je generován stejné pravidel používaných `strftime`, s poslední argument metody *_Pt*, pro generování posloupnosti **char** prvky do pole. Každé takové **char** element předpokládá, že je mapují na odpovídající element typu `CharType` mapováním jednoduché, 1: 1. Pokud *_Mod* rovná nule, efektivní formát je "%F", kde je nahrazena F *_Fmt*. V opačném případě efektivní formátu je "% MF", kde je nahrazena M *_Mod*.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [umístit](#put), který volá `do_put`.

## <a name="iter_type"></a>  time_put::iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `OutputIterator`.

## <a name="put"></a>  time_put::Put

Výstup informací data a času jako sekvenci `CharType`s.

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

*next*<br/>
Výstupní iterátor, kde posloupnost znaků představující datum a čas mají být vloženy.

*_Iosbase*<br/>
Nevyužité.

*_Fill*<br/>
Znak typu `CharType` používaného k vytvoření mezer.

*_Pt*<br/>
Informace data a času vytváří výstup.

*_Fmt*<br/>
Formát výstupu. Zobrazit [strftime, wcsftime, _strftime_l, _wcsftime_l – –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

*_Mod*<br/>
Modifikátor formátu. Zobrazit [strftime, wcsftime, _strftime_l, _wcsftime_l – –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

*první*<br/>
Začátek formátovací řetězce pro výstup. Zobrazit [strftime, wcsftime, _strftime_l, _wcsftime_l – –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

*poslední*<br/>
Konec formátovací řetězec pro výstup. Zobrazit [strftime, wcsftime, _strftime_l, _wcsftime_l – –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

### <a name="return-value"></a>Návratová hodnota

Iterátor na první pozici za posledním prvkem vložen.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [do_put –](#do_put)(`next`, `_Iosbase`, `_Fill`, `_Pt`, `_Fmt`, `_Mod`). Druhá členská funkce se zkopíruje do \* `next` ++ libovolný prvek v intervalu [ `first`, `last`) než procent (%). Procent následován znakem *C* v intervalu [ `first`, `last`), místo toho vyhodnocuje funkce `next`  =  `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) a přeskočí za *C*. Pokud však *C* je znak kvalifikátor ze sady EOQ # následovaný znakem `C2` v intervalu [ `first`, `last`), funkce vyhodnocuje místo toho `next`  =  `do_put` ( `next`, `_Iosbase`, `_Fill`, `_Pt`, `C2`, *C*) a přeskočí za `C2`.

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

## <a name="time_put"></a>  time_put::time_put

Konstruktor pro objekty typu `time_put`.

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*<br/>
Celočíselná hodnota určuje typ Správa paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* parametrů a jejich význam:

- 0: Životnost objektu se spravuje přes národní prostředí, které je obsahují.

- 1: doba života objektu je nutné ručně spravovat.

- \> 1: tyto hodnoty nejsou definovány.

Konstruktor inicializuje jeho základní objekt s [locale::facet](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="see-also"></a>Viz také:

[\<národní prostředí >](../standard-library/locale.md)<br/>
[time_base – třída](../standard-library/time-base-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
