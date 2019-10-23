---
title: basic_iostream – třída
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: 190c9aa23493cea67bae44be93fd3fdbdecc4447
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690009"
---
# <a name="basic_iostream-class"></a>basic_iostream – třída

Třída streamu, která může provádět vstup i výstup.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_iostream : public basic_istream<Elem, Tr>,
    public basic_ostream<Elem, Tr>
{
public:
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};
```

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který ovládá vložení prostřednictvím základní třídy [basic_ostream](../standard-library/basic-ostream-class.md) <  `Elem`, `Tr` > a extrakce, prostřednictvím základní třídy [basic_istream](../standard-library/basic-istream-class.md) <  `Elem` `Tr`. Tyto dva objekty sdílejí společnou virtuální základní třídu [basic_ios](../standard-library/basic-ios-class.md) <  `Elem` `Tr` >. Spravují také běžné vyrovnávací paměti datového proudu s prvky typu `Elem`, jejichž vlastnosti znaků jsou určeny třídou `Tr`. Konstruktor inicializuje své základní třídy prostřednictvím `basic_istream` ( **strbuf**) a `basic_ostream` ( **strbuf**).

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_iostream](#basic_iostream)|Vytvořte objekt `basic_iostream`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[adresu](#swap)|Vyměňuje obsah zadaného `basic_iostream` objektu pro obsah tohoto objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnotu zadaného objektu `basic_iostream` tomuto objektu. Jedná se o přiřazení přesunutí zahrnující `rvalue`, která neopouští kopii.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<istream >

**Obor názvů:** std

## <a name="basic_iostream"></a>basic_iostream::basic_iostream

Vytvořte objekt `basic_iostream`.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Parametry

*strbuf* \
Existující objekt `basic_streambuf`.

*pravé* \
Existující objekt `basic_iostream`, který se používá k vytvoření nového `basic_iostream`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní objekty pomocí způsobu `basic_istream(strbuf)` a `basic_ostream(strbuf)`.

Druhý konstruktor inicializuje základní objekty voláním `move(right)`.

## <a name="op_eq"></a>basic_iostream:: operator =

Přiřaďte k tomuto objektu hodnotu zadaného `basic_iostream` objektu. Toto je přiřazení přesunutí zahrnující rvalue, které neopouští kopii.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
@No__t_0 odkaz na objekt `basic_iostream`, ze kterého se má přiřadit.

### <a name="remarks"></a>Poznámky

Operátor členu volá `swap(right)`.

## <a name="swap"></a>basic_iostream:: swap

Vyměňuje obsah zadaného `basic_iostream` objektu pro obsah tohoto objektu.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Objekt `basic_iostream`, který se má prohodit.

### <a name="remarks"></a>Poznámky

Členská funkce volá `swap(right)`.

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[iostream – programování](../standard-library/iostream-programming.md) \
[iostreams – konvence](../standard-library/iostreams-conventions.md)
