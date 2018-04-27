---
title: time_put – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5eb3e868280b254a8f7583a4fa5408710f604005
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="timeput-class"></a>time_put – třída

Šablony třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převody hodnot času pořadí typu `CharType`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

`CharType` Typ v rámci programu použitá ke kódování znaků.

`OutputIterator` Typ iterator, do kterého čas put funkce zápisu jejich výstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[time_put](#time_put)|V konstruktoru pro objekty typu `time_put`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje výstupní iterátor.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_put](#do_put)|Virtuální funkce, která výstupy o datu a času jako posloupnost `CharType`s.|
|[PUT](#put)|Výstupy o datu a času jako posloupnost `CharType`s.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="char_type"></a>  time_put::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="do_put"></a>  time_put::do_put

Virtuální funkce, která výstupy o datu a času jako posloupnost **CharType**s.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Parametry

`next` Iterátor výstup, kde posloupnost znaků představující datum a čas se má být vložen.

`_Iosbase` Nepoužívá se.

`_Pt` Datum a čas informace se výstup.

`_Fmt` Formát výstupu. V tématu [strftime wcsftime –, _strftime_l –, _wcsftime_l –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

`_Mod` Modifikátor pro formát. V tématu [strftime wcsftime –, _strftime_l –, _wcsftime_l –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

### <a name="return-value"></a>Návratová hodnota

Iterátor na první pozici za posledním elementem vložit.

### <a name="remarks"></a>Poznámky

Funkce virtuální chráněného člena generuje sekvenční elementy začínající na `next` z hodnot čas uložené v objektu \* `_Pt`, typu **tm**. Funkce vrátí hodnotu iterator určení další místo vložte element nad rámec generovaný výstup.

Výstup je generován stejná pravidla používané `strftime`, s argumentem poslední ve `_Pt`, pro generování řadu `char` elementy do pole. Každý například `char` element se předpokládá, že k mapování na ekvivalentní element typu **CharType** mapováním jednoduchý, 1: 1. Pokud `_Mod` rovná nule, efektivní formát je "%F", kde je nahrazena F `_Fmt`. V opačném efektivní formát je "% MF", kde je nahrazena M `_Mod`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [put](#put), který volá `do_put`.

## <a name="iter_type"></a>  time_put::iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **OutputIterator**.

## <a name="put"></a>  time_put::Put

Výstupy o datu a času jako posloupnost **CharType**s.

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

`next` Iterátor výstup, kde posloupnost znaků představující datum a čas se má být vložen.

`_Iosbase` Nepoužívá se.

`_Fill` Znak typu **CharType** používaného k vytvoření mezer.

`_Pt` Datum a čas informace se výstup.

`_Fmt` Formát výstupu. V tématu [strftime wcsftime –, _strftime_l –, _wcsftime_l –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

`_Mod` Modifikátor pro formát. V tématu [strftime wcsftime –, _strftime_l –, _wcsftime_l –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

`first` Začátek formátování řetězce pro výstup. V tématu [strftime wcsftime –, _strftime_l –, _wcsftime_l –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

`last` Konce formátování řetězce pro výstup. V tématu [strftime wcsftime –, _strftime_l –, _wcsftime_l –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) platné hodnoty.

### <a name="return-value"></a>Návratová hodnota

Iterátor na první pozici za posledním elementem vložit.

### <a name="remarks"></a>Poznámky

Vrátí první členská funkce [do_put –](#do_put)( `next`, `_Iosbase`, `_Fill`, `_Pt`, `_Fmt`, `_Mod`). Druhý členská funkce zkopíruje do \* `next` ++ libovolný element v intervalu [ `first`, `last`) než procent (%). Pro procento následuje znak *C* v intervalu [ `first`, `last`), místo toho vyhodnocuje funkce `next`  =  `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) a přeskočí po *C*. V případě, ale *C* je znak kvalifikátor ze sady EOQ #, za nímž následuje znak `C2` v intervalu [ `first`, `last`), místo toho vyhodnocuje funkce `next`  =  `do_put` ( `next`, `_Iosbase`, `_Fill`, `_Pt`, `C2`, *C*) a přeskočí po `C2`.

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

`_Refs` Celočíselná hodnota určuje typ správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty `_Refs` parametrů a jejich významu jsou:

- 0: doba života objektu spravuje národní prostředí, které je obsahují.

- 1: doba života objektu, se musí ručně spravovat.

- \> 1: tyto hodnoty nejsou definovány.

Konstruktor inicializuje jeho základní objekt s [locale::facet](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="see-also"></a>Viz také

[\<národní prostředí >](../standard-library/locale.md)<br/>
[time_base – třída](../standard-library/time-base-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
