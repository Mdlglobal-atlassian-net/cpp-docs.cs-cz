---
title: strstream – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ba0d46f567232c36eb3dcd7845792bdbe8b6eac
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955732"
---
# <a name="strstream-class"></a>strstream – třída

Popisuje objekt, který řídí vkládání a extrakci prvků a kódovaného objektů pomocí vyrovnávací paměť datového proudu třídy [strstreambuf –](../standard-library/strstreambuf-class.md).

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
|[strstream –](#strstream)|Vytvoří objekt typu `strstream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[zablokování](#freeze)|Způsobí, že vyrovnávací paměť datového proudu do nedostupný prostřednictvím operací vyrovnávací paměť datového proudu.|
|[pcount –](#pcount)|Vrátí počet prvků zapsaných pro řízenou sekvenci.|
|[rdbuf](#rdbuf)|Vrací ukazatel na datový proud přidružený k tomuto `strstreambuf` objektu.|
|[str](#str)|Volání [ukotvit](../standard-library/strstreambuf-class.md#freeze)a vrátí ukazatel na začátek řízené sekvence.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<strstream – >

**Namespace:** std

## <a name="freeze"></a>  strstream::freeze

Způsobí, že vyrovnávací paměť datového proudu do nedostupný prostřednictvím operací vyrovnávací paměť datového proudu.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*  
 A **bool** označující, zda chcete datového proudu k zmrazit.

### <a name="remarks"></a>Poznámky

Volání členských funkcí [rdbuf –](#rdbuf) -> [ukotvit](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Příklad

Zobrazit [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze) příklad, který používá `freeze`.

## <a name="pcount"></a>  strstream::pcount

Vrátí počet prvků zapsaných pro řízenou sekvenci.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet zapsaných pro řízenou sekvenci prvků.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf –](#rdbuf) -> [pcount –](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Příklad

Zobrazit [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) ukázku použití pcount –.

## <a name="rdbuf"></a>  strstream::rdbuf

Vrací ukazatel na objekt přidružený strstreambuf – datového proudu.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na datový proud je přidružené strstreambuf – objektu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uloženou datový proud vyrovnávací paměti typu `pointer` k [strstreambuf –](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Příklad

Zobrazit [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) ukázku, která používá `rdbuf`.

## <a name="str"></a>  strstream::str

Volání [ukotvit](../standard-library/strstreambuf-class.md#freeze)a vrátí ukazatel na začátek řízené sekvence.

```cpp
char *str();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek řízené sekvence.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf –](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Příklad

Zobrazit [strstreambuf::str](../standard-library/strstreambuf-class.md#str) ukázku, která používá `str`.

## <a name="strstream"></a>  strstream::strstream

Vytvoří objekt typu `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*Počet*  
 Velikost vyrovnávací paměti.

*Reži_m*  
 Režim vstupní a výstupní vyrovnávací paměti. Zobrazit [ios_base::openmode](../standard-library/ios-base-class.md#openmode) Další informace.

*ptr*  
 Vyrovnávací paměť.

### <a name="remarks"></a>Poznámky

Obě konstruktory inicializují základní třídy voláním [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **sb**), kde `sb` je uložený objekt třídy [strstreambuf –](../standard-library/strstreambuf-class.md). První konstruktor také inicializuje `sb` voláním [strstreambuf –](../standard-library/strstreambuf-class.md#strstreambuf). Druhý konstruktor inicializuje základní třídu, jedním ze dvou způsobů:

- Pokud `_Mode`  &  **ios_base::app**== 0, pak *ptr* musíte rovněž první prvek v poli `count` elementy a volá konstruktor `strstreambuf`( `ptr`, `count`, `ptr`).

- V opačném případě *ptr* musíte rovněž první prvek v poli Počet prvků, který obsahuje řetězec C jehož první prvek je stanovena podle prvku *ptr*a volá konstruktor `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) ).

## <a name="see-also"></a>Viz také:

[iostream –](../standard-library/istream-typedefs.md#iostream)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
