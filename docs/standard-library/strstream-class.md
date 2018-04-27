---
title: strstream – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4432848164973c7d74416f19208e1667e198fb7
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="strstream-class"></a>strstream – třída

Popisuje objekt, který řídí vložení a extrakce elementů a kódovaného objekty pomocí datového proudu vyrovnávací paměti třídy [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Poznámky

Objekt uloží objekt třídy `strstreambuf`.

> [!NOTE]
> Tato třída je zastaralá. Zvažte použití [stringstream –](../standard-library/sstream-typedefs.md#stringstream) nebo [wstringstream –](../standard-library/sstream-typedefs.md#wstringstream) místo.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[strstream –](#strstream)|Vytvoří objekt typu `strstream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Zablokování](#freeze)|Způsobí, že vyrovnávací paměť datového proudu být k dispozici prostřednictvím operace s datovými proudy vyrovnávací paměti.|
|[pcount –](#pcount)|Vrátí počet prvků zapsána do řízené sekvenci.|
|[rdbuf](#rdbuf)|Vrátí přidruženému ukazatel na datový proud `strstreambuf` objektu.|
|[str –](#str)|Volání [freeze](../standard-library/strstreambuf-class.md#freeze)a vrátí ukazatel na začátek řízené sekvenci.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<strstream – >

**Namespace:** – std

## <a name="freeze"></a>  strstream::freeze

Způsobí, že vyrovnávací paměť datového proudu být k dispozici prostřednictvím operace s datovými proudy vyrovnávací paměti.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

`_Freezeit` A `bool` označující, zda chcete datového proudu k zablokováno.

### <a name="remarks"></a>Poznámky

Volání členských funkcí [rdbuf –](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Příklad

V tématu [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze) pro příklad, který používá **freeze**.

## <a name="pcount"></a>  strstream::pcount

Vrátí počet prvků zapsána do řízené sekvenci.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet elementů zapsána do řízené sekvenci.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [rdbuf –](#rdbuf) -> [pcount –](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Příklad

V tématu [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) pro ukázkové použití pcount –.

## <a name="rdbuf"></a>  strstream::rdbuf

Vrátí ukazatel datový proud přidružený strstreambuf objektu.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na datový proud je související objekt strstreambuf.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uložené datového proudu vyrovnávací paměti typu **ukazatel** k [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Příklad

V tématu [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) příklad, který používá `rdbuf`.

## <a name="str"></a>  strstream::str

Volání [freeze](../standard-library/strstreambuf-class.md#freeze)a vrátí ukazatel na začátek řízené sekvenci.

```cpp
char *str();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek řízené sekvenci.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [rdbuf –](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Příklad

V tématu [strstreambuf::str](../standard-library/strstreambuf-class.md#str) příklad, který používá **str**.

## <a name="strstream"></a>  strstream::strstream

Vytvoří objekt typu `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

`count` Velikost vyrovnávací paměti.

`_Mode` Režim vstupní a výstupní vyrovnávací paměti. V tématu [ios_base::openmode](../standard-library/ios-base-class.md#openmode) Další informace.

`ptr` Vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Konstruktory inicializovat základní třídu voláním [streambuf –](../standard-library/streambuf-typedefs.md#streambuf)( **sb**), kde **sb** je objekt uložené třídy [strstreambuf](../standard-library/strstreambuf-class.md) . První konstruktor inicializuje také **sb** voláním [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). Druhý konstruktor inicializuje základní třídu jedním ze dvou způsobů:

- Pokud `_Mode`  &  **ios_base::app**== 0, pak `ptr` musí určit první prvek pole `count` elementy a volá konstruktor `strstreambuf`( `ptr`, `count`, `ptr`).

- V opačném `ptr` musí určit první prvek pole počet elementů obsahující řetězec C jejichž první prvek je určen podle `ptr`a volá konstruktor `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) ).

## <a name="see-also"></a>Viz také

[iostream](../standard-library/istream-typedefs.md#iostream)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
