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
ms.openlocfilehash: c73ab13d3cb2531ff3d741766bc86f8354a0be9d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458064"
---
# <a name="ostrstream-class"></a>ostrstream – třída

Popisuje objekt, který řídí vložení prvků a zakódovaných objektů do vyrovnávací paměti datového proudu třídy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>Poznámky

Objekt ukládá objekt třídy `strstreambuf`.

> [!NOTE]
> Tato třída je zastaralá. Místo toho zvažte použití [ostringstream –](../standard-library/sstream-typedefs.md#ostringstream) nebo [wostringstream –](../standard-library/sstream-typedefs.md#wostringstream) .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ostrstream](#ostrstream)|Vytvoří objekt typu `ostrstream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[uvolnění](#freeze)|Způsobí, že vyrovnávací paměť datového proudu nebude k dispozici prostřednictvím operací vyrovnávací paměti datového proudu.|
|[pcount](#pcount)|Vrátí počet prvků zapsaných do řízené sekvence.|
|[rdbuf](#rdbuf)|Vrátí ukazatel na přidružený `strstreambuf` objekt datového proudu.|
|[str](#str)|Volání [](../standard-library/strstreambuf-class.md#freeze)se zablokují a pak vrátí ukazatel na začátek řízené sekvence.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<strstream >

**Obor názvů:** std

## <a name="freeze"></a>ostrstream:: zmrazit

Způsobí, že vyrovnávací paměť datového proudu nebude k dispozici prostřednictvím operací vyrovnávací paměti datového proudu.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*\
**Logická** hodnota označující, zda má být datový proud zmrazen.

### <a name="remarks"></a>Poznámky

Členská funkce volá [rdbuf](#rdbuf) -> [zmrazení](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Příklad

Viz [strstream:: zmrazit](../standard-library/strstreambuf-class.md#freeze) pro příklad, který používá `freeze`.

## <a name="ostrstream"></a>ostrstream:: ostrstream

Vytvoří objekt typu `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

*střed*\
Vyrovnávací paměť.

*výpočtu*\
Velikost vyrovnávací paměti v bajtech.

*_Mode*\
Vstupní a výstupní režim vyrovnávací paměti. Další informace naleznete v tématu [ios_base:: openmode](../standard-library/ios-base-class.md#openmode) .

### <a name="remarks"></a>Poznámky

Oba konstruktory inicializují základní třídu voláním [ostream](../standard-library/ostream-typedefs.md#ostream)(**SB**), kde `sb` je uložený objekt třídy [strstreambuf](../standard-library/strstreambuf-class.md). První konstruktor se také inicializuje `sb` voláním `strstreambuf`. Druhý konstruktor inicializuje základní třídu jedním ze dvou způsobů:

- Pokud `_Mode` **ios_base::** `count` `strstreambuf` `count``ptr`App = = 0, jenutnéurčitprvníprvekpoleprvkůakonstruktorvolá(,,`ptr`  &  `ptr`).

- `ptr` `ptr` `strstreambuf`V opačném případě `count`je nutné určit první prvek pole počtu prvků, který obsahuje řetězec jazyka C, jehož první prvek je určen a konstruktor volá (,, `ptr` `ptr` + `strlen`( `ptr`) ).

## <a name="pcount"></a>ostrstream: počet:p

Vrátí počet prvků zapsaných do řízené sekvence.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků zapsaných do řízené sekvence.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Příklad

Viz [strstream::p Count](../standard-library/strstreambuf-class.md#pcount) pro ukázku, která používá `pcount`.

## <a name="rdbuf"></a>ostrstream:: rdbuf

Vrátí ukazatel na přidružený objekt strstreambuf datového proudu.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidružený objekt strstreambuf datového proudu.

### <a name="remarks"></a>Poznámky

Členská funkce vrací adresu vyrovnávací paměti uloženého datového proudu typu `pointer` do [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Příklad

Viz [strstreambuf::p Count](../standard-library/strstreambuf-class.md#pcount) pro ukázku, která používá `rdbuf`.

## <a name="str"></a>ostrstream:: str

Volání [](../standard-library/strstreambuf-class.md#freeze)se zablokují a pak vrátí ukazatel na začátek řízené sekvence.

```cpp
char *str();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek řízené sekvence.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Příklad

Ukázku, kterou používá `str`, najdete v tématu [strstream:: str](../standard-library/strstreambuf-class.md#str) .

## <a name="see-also"></a>Viz také:

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
