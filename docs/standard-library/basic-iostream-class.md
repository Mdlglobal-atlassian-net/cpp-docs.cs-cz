---
title: basic_iostream – třída
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: e2a892525afbbad6d5b42d0b836fee096a70c297
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376822"
---
# <a name="basic_iostream-class"></a>basic_iostream – třída

Třída datového proudu, která může provést vstup i výstup.

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

Šablona třídy popisuje objekt, který řídí vložení, [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`prostřednictvím `Tr` své základní třídy basic_ostream , `Tr`> a extrakce, a to prostřednictvím své základní třídy [basic_istream](../standard-library/basic-istream-class.md)< `Elem`,>. Tyto dva objekty sdílejí společnou `Tr` virtuální základní třídu [basic_ios](../standard-library/basic-ios-class.md)< `Elem`,>. Také spravují společnou vyrovnávací paměť datového proudu s prvky `Elem`typu `Tr`, jejichž znakové znaky jsou určeny třídou . Konstruktor inicializuje své základní `basic_istream`třídy prostřednictvím `basic_ostream`( **strbuf**) a ( **strbuf**).

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_iostream](#basic_iostream)|Vytvořte `basic_iostream` objekt.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Swap](#swap)|Vymění obsah zadaný `basic_iostream` objekt pro obsah tohoto objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí tomuto objektu hodnotu určeného `basic_iostream` objektu. Jedná se o přesunutí `rvalue` přiřazení zahrnující, který nezanechává kopii za sebou.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<istream>

**Obor názvů:** std

## <a name="basic_iostreambasic_iostream"></a><a name="basic_iostream"></a>basic_iostream::basic_iostream

Vytvořte `basic_iostream` objekt.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Parametry

*strbuf (Strbuf)*\
Existující objekt `basic_streambuf`.

*Právo*\
Existující `basic_iostream` objekt, který se používá `basic_iostream`k vytvoření nového .

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní objekty `basic_istream(strbuf)` `basic_ostream(strbuf)`prostřednictvím a .

Druhý konstruktor inicializuje základní objekty voláním `move(right)`.

## <a name="basic_iostreamoperator"></a><a name="op_eq"></a>basic_iostream::operátor=

Přiřaďte tomuto objektu hodnotu určeného `basic_iostream` objektu. Toto je přiřazení move zahrnující rvalue, která nezanechává kopii za sebou.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Odkaz `rvalue` na `basic_iostream` objekt, ze který chcete přiřadit.

### <a name="remarks"></a>Poznámky

Operátor člena `swap(right)`volá .

## <a name="basic_iostreamswap"></a><a name="swap"></a>basic_iostream::swap

Vymění obsah zadaný `basic_iostream` objekt pro obsah tohoto objektu.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt `basic_iostream` zaměnit.

### <a name="remarks"></a>Poznámky

Členské funkce `swap(right)`volá .

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
