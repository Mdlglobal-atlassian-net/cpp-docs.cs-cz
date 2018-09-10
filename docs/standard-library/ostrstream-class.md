---
title: ostrstream – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 526ed4340446e78a723af97f43fbed401f574764
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106041"
---
# <a name="ostrstream-class"></a>ostrstream – třída

Popisuje objekt, který řídí vkládání prvků a kódovaného objekty do vyrovnávací paměti datového proudu třídy [strstreambuf –](../standard-library/strstreambuf-class.md).

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
|[ostrstream –](#ostrstream)|Vytvoří objekt typu `ostrstream`.|

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

## <a name="freeze"></a>  ostrstream::freeze

Způsobí, že vyrovnávací paměť datového proudu do nedostupný prostřednictvím operací vyrovnávací paměť datového proudu.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*<br/>
A **bool** označující, zda chcete datového proudu k zmrazit.

### <a name="remarks"></a>Poznámky

Volání členských funkcí [rdbuf –](#rdbuf) -> [ukotvit](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Příklad

Zobrazit [strstream::freeze](../standard-library/strstreambuf-class.md#freeze) příklad, který používá `freeze`.

## <a name="ostrstream"></a>  ostrstream::ostrstream

Vytvoří objekt typu `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Vyrovnávací paměť.

*Počet*<br/>
Velikost vyrovnávací paměti v bajtech.

*Reži_m*<br/>
Režim vstupní a výstupní vyrovnávací paměti. Zobrazit [ios_base::openmode](../standard-library/ios-base-class.md#openmode) Další informace.

### <a name="remarks"></a>Poznámky

Obě konstruktory inicializují základní třídy voláním [ostream](../standard-library/ostream-typedefs.md#ostream)(**sb**), kde `sb` je uložený objekt třídy [strstreambuf –](../standard-library/strstreambuf-class.md). První konstruktor také inicializuje `sb` voláním `strstreambuf`. Druhý konstruktor inicializuje základní třídu, jedním ze dvou způsobů:

- Pokud `_Mode`  &  **ios_base::app**== 0, pak `ptr` musíte rovněž první prvek v poli `count` elementy a volá konstruktor `strstreambuf`(`ptr`, `count`, `ptr`).

- V opačném případě `ptr` musíte rovněž první prvek v poli Počet prvků, který obsahuje řetězec C jehož první prvek je stanovena podle prvku `ptr`a volá konstruktor `strstreambuf`(`ptr`, `count`, `ptr` + `strlen`( `ptr`) ).

## <a name="pcount"></a>  ostrstream::pcount

Vrátí počet prvků zapsaných pro řízenou sekvenci.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet zapsaných pro řízenou sekvenci prvků.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [rdbuf –](#rdbuf) -> [pcount –](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Příklad

Zobrazit [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) ukázku, která používá `pcount`.

## <a name="rdbuf"></a>  ostrstream::rdbuf

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

## <a name="str"></a>  ostrstream::str

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

[ostream](../standard-library/ostream-typedefs.md#ostream)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
