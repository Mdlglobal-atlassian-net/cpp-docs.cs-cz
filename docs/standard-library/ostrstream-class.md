---
title: ostrstream – třída
ms.date: 11/04/2016
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
ms.openlocfilehash: b52ba70607a5214a6aa28f04cdded0b19a56b2f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373535"
---
# <a name="ostrstream-class"></a>ostrstream – třída

Popisuje objekt, který řídí vkládání prvků a kódovaných objektů do vyrovnávací paměti datového proudu třídy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>Poznámky

Objekt ukládá objekt třídy `strstreambuf`.

> [!NOTE]
> Tato třída je zastaralá. Zvažte použití [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) nebo [wostringstream](../standard-library/sstream-typedefs.md#wostringstream) místo.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ostrstream](#ostrstream)|Vytvoří objekt typu `ostrstream`.|

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

## <a name="ostrstreamfreeze"></a><a name="freeze"></a>ostrstream::zmrazení

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

Viz [strstream::freeze](../standard-library/strstreambuf-class.md#freeze) pro příklad, který používá `freeze`.

## <a name="ostrstreamostrstream"></a><a name="ostrstream"></a>ostrstream::ostrstream

Vytvoří objekt typu `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Vyrovnávací paměť.

*Počet*\
Velikost vyrovnávací paměti v bajtů.

*_Mode*\
Vstupní a výstupní režim vyrovnávací paměti. Další informace naleznete [ios_base::openmode.](../standard-library/ios-base-class.md#openmode)

### <a name="remarks"></a>Poznámky

Oba konstruktory inicializovat základní třídy voláním `sb` [ostream](../standard-library/ostream-typedefs.md#ostream)(**sb**), kde je uložený objekt třídy [strstreambuf](../standard-library/strstreambuf-class.md). První konstruktor také `sb` inicializuje `strstreambuf`voláním . Druhý konstruktor inicializuje základní třídu jedním ze dvou způsobů:

- Pokud `_Mode`  &  **ios_base::app**== `ptr` 0, pak musí určit `count` první prvek pole prvků `strstreambuf``ptr`a `count` `ptr`konstruktor volání ( , , ).

- V `ptr` opačném případě musí být určen první prvek pole elementů počtu, `ptr`který obsahuje řetězec `strstreambuf`C, jehož první prvek je určen aplikací , a volání konstruktoru`ptr`( `count`, , `ptr`  +  `strlen`, ). `ptr`

## <a name="ostrstreampcount"></a><a name="pcount"></a>ostrstream::ppočet

Vrátí počet počtu prvků zapsaných do řízené sekvence.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků zapsaných do řízené sekvence.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Příklad

Viz [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) pro vzorek, který používá `pcount`.

## <a name="ostrstreamrdbuf"></a><a name="rdbuf"></a>ostrstream::rdbuf

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

## <a name="ostrstreamstr"></a><a name="str"></a>ostrstream::str

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

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
