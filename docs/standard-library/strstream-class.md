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
ms.openlocfilehash: 53baa350121796d5198211e1fdb08f4341df6b80
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459106"
---
# <a name="strstream-class"></a>strstream – třída

Popisuje objekt, který ovládá vkládání a extrakci prvků a kódovaných objektů pomocí vyrovnávací paměti datového proudu třídy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Poznámky

Objekt ukládá objekt třídy `strstreambuf`.

> [!NOTE]
> Tato třída je zastaralá. Místo toho zvažte použití [stringstream](../standard-library/sstream-typedefs.md#stringstream) nebo [wstringstream –](../standard-library/sstream-typedefs.md#wstringstream) .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[strstream](#strstream)|Vytvoří objekt typu `strstream`.|

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

## <a name="freeze"></a>strstream:: zmrazit

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

Viz [strstreambuf:: zmrazit](../standard-library/strstreambuf-class.md#freeze) pro příklad, který používá `freeze`.

## <a name="pcount"></a>strstream: počet:p

Vrátí počet prvků zapsaných do řízené sekvence.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků zapsaných do řízené sekvence.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Příklad

Ukázku použití pcount naleznete v tématu [strstreambuf::p Count](../standard-library/strstreambuf-class.md#pcount) .

## <a name="rdbuf"></a>strstream:: rdbuf

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

## <a name="str"></a>strstream:: str

Volání [](../standard-library/strstreambuf-class.md#freeze)se zablokují a pak vrátí ukazatel na začátek řízené sekvence.

```cpp
char *str();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek řízené sekvence.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Příklad

Ukázku, kterou používá `str`, najdete v tématu [strstreambuf:: str](../standard-library/strstreambuf-class.md#str) .

## <a name="strstream"></a>strstream:: strstream

Vytvoří objekt typu `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*výpočtu*\
Velikost vyrovnávací paměti.

*_Mode*\
Vstupní a výstupní režim vyrovnávací paměti. Další informace naleznete v tématu [ios_base:: openmode](../standard-library/ios-base-class.md#openmode) .

*střed*\
Vyrovnávací paměť.

### <a name="remarks"></a>Poznámky

Oba konstruktory inicializují základní třídu voláním [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **SB**), kde `sb` je uložený objekt třídy [strstreambuf](../standard-library/strstreambuf-class.md). První konstruktor se také inicializuje `sb` voláním [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). Druhý konstruktor inicializuje základní třídu jedním ze dvou způsobů:

- Pokud `_Mode` `strstreambuf` `ptr` `count` `count` `ptr`  ios_base:: App = = 0, pak PTR musí označovat první prvek pole prvků a volání konstruktoru (,,).  &  .

- V opačném případě musí *PTR* určit první prvek pole počtu prvků, který obsahuje řetězec jazyka C, jehož první prvek je určen jako *PTR*, a volání `strstreambuf`konstruktoru ( `ptr`,, `ptr` `count`  +  `strlen`( `ptr`) ).

## <a name="see-also"></a>Viz také:

[iostream –](../standard-library/istream-typedefs.md#iostream)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
