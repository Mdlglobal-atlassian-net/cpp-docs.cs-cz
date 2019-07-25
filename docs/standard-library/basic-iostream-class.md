---
title: basic_iostream – třída
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: 052271e2e2cc929875489e27abde2147bc5c070a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460090"
---
# <a name="basiciostream-class"></a>basic_iostream – třída

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

Třída šablony popisuje objekt, který ovládá vložení prostřednictvím základní třídy [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`> a extrakce prostřednictvím své základní třídy [basic_istream](../standard-library/basic-istream-class.md) < . `Elem` ,`Tr`>. Tyto dva objekty sdílejí společnou virtuální základní třídu [basic_ios](../standard-library/basic-ios-class.md)< `Elem` `Tr`>. Spravují také běžné vyrovnávací paměti datového proudu s prvky typu `Elem`, jejichž znaky jsou určeny třídou. `Tr` Konstruktor inicializuje své základní třídy `basic_istream`prostřednictvím ( **strbuf**) a `basic_ostream`( **strbuf**).

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_iostream](#basic_iostream)|`basic_iostream` Vytvořte objekt.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[swap](#swap)|Vyměňuje obsah zadaného `basic_iostream` objektu pro obsah tohoto objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnotu zadaného `basic_iostream` objektu tomuto objektu. Toto je přiřazení přesunutí zahrnující `rvalue` , které neopouští kopii.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<IStream >

**Obor názvů:** std

## <a name="basic_iostream"></a>basic_iostream::basic_iostream

`basic_iostream` Vytvořte objekt.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Parametry

*strbuf*\
Existující objekt `basic_streambuf`.

*Kliknutím*\
Existující `basic_iostream` objekt, který se používá k vytvoření nového `basic_iostream`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní objekty `basic_istream(strbuf)` tak, že jsou a. `basic_ostream(strbuf)`

Druhý konstruktor inicializuje základní objekty voláním metody `move(right)`.

## <a name="op_eq"></a>basic_iostream:: operator =

Přiřaďte hodnotu zadaného `basic_iostream` objektu tomuto objektu. Toto je přiřazení přesunutí zahrnující rvalue, které neopouští kopii.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
`rvalue` Odkaz`basic_iostream` na objekt, ze kterého se má přiřadit.

### <a name="remarks"></a>Poznámky

Operátor členské volání `swap(right)`.

## <a name="swap"></a>  basic_iostream::swap

Vyměňuje obsah zadaného `basic_iostream` objektu pro obsah tohoto objektu.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
`basic_iostream` Objekt, který se má prohodit.

### <a name="remarks"></a>Poznámky

Členská funkce volá `swap(right)`.

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
