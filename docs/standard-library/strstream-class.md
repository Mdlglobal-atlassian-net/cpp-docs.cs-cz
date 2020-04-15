---
title: strstream – třída
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
ms.openlocfilehash: 047b7e9d7fdece75137980b013d43abf1d5e3ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376619"
---
# <a name="strstream-class"></a>strstream – třída

Popisuje objekt, který řídí vkládání a extrakci prvků a kódovaných objektů pomocí vyrovnávací paměti datového proudu třídy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Poznámky

Objekt ukládá objekt třídy `strstreambuf`.

> [!NOTE]
> Tato třída je zastaralá. Zvažte použití [stringstream](../standard-library/sstream-typedefs.md#stringstream) nebo [wstringstream](../standard-library/sstream-typedefs.md#wstringstream) místo.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[strstream](#strstream)|Vytvoří objekt typu `strstream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Zmrazit](#freeze)|Způsobí, že vyrovnávací paměť datového proudu není k dispozici prostřednictvím operací vyrovnávací paměti datového proudu.|
|[pcount](#pcount)|Vrátí počet počtu prvků zapsaných do řízené sekvence.|
|[rdbuf](#rdbuf)|Vrátí ukazatel na přidružený `strstreambuf` objekt datového proudu.|
|[Str](#str)|Volání [zmrazit](../standard-library/strstreambuf-class.md#freeze)a potom vrátí ukazatel na začátek řízené sekvence.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<strstream>

**Obor názvů:** std

## <a name="strstreamfreeze"></a><a name="freeze"></a>strstream::zmrazit

Způsobí, že vyrovnávací paměť datového proudu není k dispozici prostřednictvím operací vyrovnávací paměti datového proudu.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*\
**Bool** označující, zda chcete, aby byl datový proud zmrazen.

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit).*

### <a name="example"></a>Příklad

Viz [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze) pro příklad, který používá `freeze`.

## <a name="strstreampcount"></a><a name="pcount"></a>strstream::ppočet

Vrátí počet počtu prvků zapsaných do řízené sekvence.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků zapsaných do řízené sekvence.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Příklad

Viz [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) pro vzorek pomocí pcount.

## <a name="strstreamrdbuf"></a><a name="rdbuf"></a>strstream::rdbuf

Vrátí ukazatel na přidružený objekt strstreambuf datového proudu.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidružený objekt strstreambuf datového proudu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uložené hodové vyrovnávací paměti typu `pointer` [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Příklad

Viz [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) pro vzorek, který používá `rdbuf`.

## <a name="strstreamstr"></a><a name="str"></a>strstream::str

Volání [zmrazit](../standard-library/strstreambuf-class.md#freeze)a potom vrátí ukazatel na začátek řízené sekvence.

```cpp
char *str();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek řízené sekvence.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [hodnotu rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Příklad

Viz [strstreambuf::str](../standard-library/strstreambuf-class.md#str) pro vzorek, který používá `str`.

## <a name="strstreamstrstream"></a><a name="strstream"></a>strstream::strstream

Vytvoří objekt typu `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*Počet*\
Velikost vyrovnávací paměti.

*_Mode*\
Vstupní a výstupní režim vyrovnávací paměti. Další informace naleznete [ios_base::openmode.](../standard-library/ios-base-class.md#openmode)

*Ptr*\
Vyrovnávací paměť.

### <a name="remarks"></a>Poznámky

Oba konstruktory inicializovat základní třídy voláním [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **sb**), kde `sb` je uložený objekt třídy [strstreambuf](../standard-library/strstreambuf-class.md). První konstruktor také inicializuje `sb` voláním [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). Druhý konstruktor inicializuje základní třídu jedním ze dvou způsobů:

- Pokud `_Mode`  &  **ios_base::app**== 0, pak *ptr* musí určit `count` první prvek pole `strstreambuf`prvků `ptr` `count`a `ptr`konstruktor volání ( , , ).

- V opačném případě *musí ptr* určit první prvek pole elementů počtu, který obsahuje řetězec C, jehož `count` `ptr`  +  `strlen`první `ptr`prvek je určen *ptr*, a volání `strstreambuf`konstruktoru ( `ptr`, , ( ).

## <a name="see-also"></a>Viz také

[iostream](../standard-library/istream-typedefs.md#iostream)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
