---
title: istrstream – třída
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: d548a8c2c47a5a345be725afdedb47524344f720
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337524"
---
# <a name="istrstream-class"></a>istrstream – třída

Popisuje objekt, který řídí extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu třídy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>Poznámky

Objekt ukládá objekt třídy `strstreambuf`.

> [!NOTE]
> Tato třída je zastaralá. Zvažte použití [istringstream](../standard-library/sstream-typedefs.md#istringstream) nebo [wistringstream](../standard-library/sstream-typedefs.md#wistringstream) místo.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[istrstream](#istrstream)|Vytvoří objekt typu `istrstream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrátí ukazatel na přidružený `strstreambuf` objekt datového proudu.|
|[Str](#str)|Volání [zmrazit](../standard-library/strstreambuf-class.md#freeze)a potom vrátí ukazatel na začátek řízené sekvence.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<strstream>

**Obor názvů:** std

## <a name="istrstreamistrstream"></a><a name="istrstream"></a>istrstream::istrstream

Vytvoří objekt typu `istrstream`.

```cpp
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```

### <a name="parameters"></a>Parametry

*Počet*\
Délka pufru (*ptr*).

*Ptr*\
Obsah, s nímž je inicializována vyrovnávací paměť.

### <a name="remarks"></a>Poznámky

Všechny konstruktory inicializovat základní třídy voláním [istream](../standard-library/istream-typedefs.md#istream)(**sb**), kde `sb` je uložený objekt třídy [strstreambuf](../standard-library/strstreambuf-class.md). První dva konstruktory také `sb` `strstreambuf`inicializovat voláním `ptr`( ( **const** `char` \*) , 0 ). Zbývající dva konstruktory místo `strstreambuf`volání ( ( `ptr` `count` **const** `char` *) , ).

## <a name="istrstreamrdbuf"></a><a name="rdbuf"></a>istrstream::rdbuf

Vrátí ukazatel na přidružený objekt strstreambuf datového proudu.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidružený objekt strstreambuf datového proudu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uložené vyrovnávací paměti datového proudu, ukazatele typu [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Příklad

Viz [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) pro vzorek, který používá `rdbuf`.

## <a name="istrstreamstr"></a><a name="str"></a>istrstream::str

Volání [zmrazit](../standard-library/strstreambuf-class.md#freeze)a potom vrátí ukazatel na začátek řízené sekvence.

```cpp
char *str();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek řízené sekvence.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [hodnotu rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Příklad

Viz [strstream::str](../standard-library/strstreambuf-class.md#str) pro vzorek, který používá `str`.

## <a name="see-also"></a>Viz také

[istream](../standard-library/istream-typedefs.md#istream)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
