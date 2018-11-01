---
title: istrstream – třída
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: 70e71ac5a6fd523f0b7589625f4e88fdb41ee0e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581932"
---
# <a name="istrstream-class"></a>istrstream – třída

Popisuje objekt, který řídí extrakce prvků a kódovaného objekty z vyrovnávací paměti datového proudu třídy [strstreambuf –](../standard-library/strstreambuf-class.md).

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
|[istrstream –](#istrstream)|Vytvoří objekt typu `istrstream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[rdbuf](#rdbuf)|Vrací ukazatel na datový proud přidružený k tomuto `strstreambuf` objektu.|
|[str](#str)|Volání [ukotvit](../standard-library/strstreambuf-class.md#freeze)a vrátí ukazatel na začátek řízené sekvence.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<strstream – >

**Namespace:** std

## <a name="istrstream"></a>  istrstream::istrstream

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

*Počet*<br/>
Délka vyrovnávací paměti (*ptr*).

*ptr*<br/>
Obsah, se kterými se inicializuje vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Všechny konstruktory inicializují základní třídy voláním [istream](../standard-library/istream-typedefs.md#istream)(**sb**), kde `sb` je uložený objekt třídy [strstreambuf –](../standard-library/strstreambuf-class.md). První dva konstruktory také inicializují `sb` voláním `strstreambuf`(( **const** `char` \*) `ptr`, 0). Místo toho volat zbývající dva konstruktory `strstreambuf`(( **const** `char` *) `ptr`, `count` ).

## <a name="rdbuf"></a>  istrstream::rdbuf

Vrací ukazatel na objekt přidružený strstreambuf – datového proudu.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na datový proud je přidružené strstreambuf – objektu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uloženou datový proud vyrovnávací paměti, typu ukazatele do [strstreambuf –](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Příklad

Zobrazit [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) ukázku, která používá `rdbuf`.

## <a name="str"></a>  istrstream::str

Volání [ukotvit](../standard-library/strstreambuf-class.md#freeze)a vrátí ukazatel na začátek řízené sekvence.

```cpp
char *str();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek řízené sekvence.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf –](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Příklad

Zobrazit [strstream::str](../standard-library/strstreambuf-class.md#str) ukázku, která používá `str`.

## <a name="see-also"></a>Viz také:

[IStream](../standard-library/istream-typedefs.md#istream)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
