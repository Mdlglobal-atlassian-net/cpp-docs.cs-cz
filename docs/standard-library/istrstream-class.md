---
title: istrstream – třída
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: 59b69d3f862715840e1557a10d6087350488a3c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448078"
---
# <a name="istrstream-class"></a>istrstream – třída

Popisuje objekt, který ovládá extrakci prvků a kódovaných objektů z vyrovnávací paměti datového proudu třídy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>Poznámky

Objekt ukládá objekt třídy `strstreambuf`.

> [!NOTE]
> Tato třída je zastaralá. Místo toho zvažte použití [istringstream –](../standard-library/sstream-typedefs.md#istringstream) nebo [wistringstream –](../standard-library/sstream-typedefs.md#wistringstream) .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[istrstream](#istrstream)|Vytvoří objekt typu `istrstream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrátí ukazatel na přidružený `strstreambuf` objekt datového proudu.|
|[str](#str)|Volání [](../standard-library/strstreambuf-class.md#freeze)se zablokují a pak vrátí ukazatel na začátek řízené sekvence.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<strstream >

**Obor názvů:** std

## <a name="istrstream"></a>istrstream –:: istrstream –

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

*výpočtu*\
Délka vyrovnávací paměti (*PTR*).

*střed*\
Obsah, se kterým se inicializuje vyrovnávací paměť

### <a name="remarks"></a>Poznámky

Všechny konstruktory inicializují základní třídu voláním [IStream](../standard-library/istream-typedefs.md#istream)(**SB**), kde `sb` je uložený objekt třídy [strstreambuf](../standard-library/strstreambuf-class.md). První `sb` dva konstruktory se také inicializují voláním `ptr` `strstreambuf`(  `char` (const \*), 0). Zbývající dva konstruktory místo toho volají `strstreambuf`(( **const** `char` * `ptr`) `count` ,).

## <a name="rdbuf"></a>istrstream –:: rdbuf

Vrátí ukazatel na přidružený objekt strstreambuf datového proudu.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidružený objekt strstreambuf datového proudu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uložené vyrovnávací paměti datového proudu typu ukazatel na [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Příklad

Viz [strstreambuf::p Count](../standard-library/strstreambuf-class.md#pcount) pro ukázku, která používá `rdbuf`.

## <a name="str"></a>istrstream –:: str

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

[IStream](../standard-library/istream-typedefs.md#istream)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
