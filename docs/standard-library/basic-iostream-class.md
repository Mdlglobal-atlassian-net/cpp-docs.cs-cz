---
title: basic_iostream – třída
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_iostream
- istream/std::basic_iostream::swap
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
ms.openlocfilehash: 80aad69f05b7473b508447d6f69f1d92edbeeca3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400640"
---
# <a name="basiciostream-class"></a>basic_iostream – třída

Datový proud třídu, která můžete provést jak vstupu a výstupu.

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

Třída šablony popisuje objekt, který řídí vkládání prostřednictvím její základní třídě [basic_ostream –](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`> a extrakce prostřednictvím její základní třídě [basic_ IStream](../standard-library/basic-istream-class.md)< `Elem`, `Tr`>. Dva objekty sdílejí společné virtuální základní třídy [basic_ios –](../standard-library/basic-ios-class.md)< `Elem`, `Tr`>. Spravují běžné vyrovnávací paměť datového proudu, s prvky typu `Elem`, jehož vlastnosti znaků určuje třídu `Tr`. Konstruktor inicializuje její základní třídy prostřednictvím `basic_istream`( **strbuf**) a `basic_ostream`( **strbuf**).

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_iostream](#basic_iostream)|Vytvoření `basic_iostream` objektu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[swap](#swap)|Vyměňuje obsahy zadaných `basic_iostream` objektu bude obsah tohoto objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnotu zadaného `basic_iostream` do tohoto objektu. Toto je zahrnující přiřazení pro přesun `rvalue` , nenechává kopii za sebou.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<istream >

**Namespace:** std

## <a name="basic_iostream"></a>  basic_iostream::basic_iostream

Vytvoření `basic_iostream` objektu.

```cpp
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```

### <a name="parameters"></a>Parametry

*strbuf*<br/>
Existující objekt `basic_streambuf`.

*doprava*<br/>
Existující `basic_iostream` objekt, který slouží k vytvoření nového `basic_iostream`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje základní objekty prostřednictvím `basic_istream(strbuf)` a `basic_ostream(strbuf)`.

Druhý konstruktor inicializuje pomocí volání základních objektech `move(right)`.

## <a name="op_eq"></a>  basic_iostream::Operator =

Přiřadí hodnotu zadaného `basic_iostream` do tohoto objektu. Toto je přiřazení pro přesun zahrnující rvalue kopii nenechává za sebou.

```cpp
basic_iostream& operator=(basic_iostream&& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
`rvalue` Odkaz `basic_iostream` objekt přiřadit ručně z.

### <a name="remarks"></a>Poznámky

Operátor volání člen `swap(right)`.

## <a name="swap"></a>  basic_iostream::swap

Vyměňuje obsahy zadaných `basic_iostream` objektu bude obsah tohoto objektu.

```cpp
void swap(basic_iostream& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
`basic_iostream` Objektu se prohodit.

### <a name="remarks"></a>Poznámky

Volání členských funkcí `swap(right)`.

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
