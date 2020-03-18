---
title: operátory &lt;string_view&gt;
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::operator!=
- xstring/basic_string_view::operator&gt;
- xstring/basic_string_view::operator&gt;=
- xstring/basic_string_view::operator&lt;
- xstring/basic_string_view::operator&lt;&lt;
- xstring/basic_string_view::operator&lt;=
- xstring/basic_string_view::operator+
- xstring/basic_string_view::operator==
helpviewer_keywords:
- std::basic_string_view::operator!=
- std::basic_string_view::operator&gt;
- std::basic_string_view::operator&gt;=
- std::basic_string_view::operator&lt;
- std::basic_string_view::operator&lt;&lt;
- std::basic_string_view::operator&lt;=, std::basic_string_view::operator==
ms.openlocfilehash: 699b1f1bddeb71ecbf03297d162a7e45ebd39609
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419418"
---
# <a name="ltstring_viewgt-operators"></a>operátory &lt;string_view&gt;

Tyto operátory použijte k porovnání dvou string_view objektů nebo string_view a nějakého jiného objektu řetězce (například [std:: String](basic-string-class.md)nebo **char\*** ), pro který je k dispozici implicitní převod. 

||||
|-|-|-|
|[operator!=](#op_neq)|[operátor&gt;](#op_gt)|[operátor&gt;=](#op_gt_eq)|
|[operátor&lt;](#op_lt)|[operátor&lt;&lt;](#op_lt_lt)|[operátor&lt;=](#op_lt_eq)|
|[operator = = – operátor](#op_eq_eq)|[sv – operátor](#op_sv)|

## <a name="op_neq"></a>! = – operátor

Testuje, zda objekt na levé straně operátoru není roven objektu na pravé straně.

```cpp
template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator!=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

*pravé*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud objekt na levé straně operátoru není lexikograficky rovný objektu na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Implicitní převod musí existovat z *convertible_string_type* na string_view na druhé straně. 

Porovnání je založeno na lexicographical porovnání sekvencí znaků. Pokud mají stejný počet prvků a všechny elementy jsou stejné, jsou oba objekty stejné. V opačném případě jsou nerovné.

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt na levé straně operátoru roven objektu na pravé straně.

```cpp
template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator==(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

*pravé*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt na levé straně operátoru lexikograficky rovný objektu na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Implicitní převod musí existovat z *convertible_string_type* na string_view na druhé straně. 

Porovnání je založeno na lexicographical porovnání sekvencí znaků. Pokud mají stejný počet prvků a všechny elementy jsou stejné, jsou oba objekty stejné.


## <a name="op_lt"></a>operátor&lt;

Testuje, zda je objekt na levé straně operátoru menší než objekt na pravé sidestring_view
```cpp
template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

*pravé*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt na levé straně operátoru lexikograficky menší než objekt na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Implicitní převod musí existovat z *convertible_string_type* na string_view na druhé straně. 

Porovnání je založeno na lexicographical porovnání sekvencí znaků. Při výskytu prvního nestejné dvojice znaků se vrátí výsledek tohoto porovnání. Pokud se nenajde žádné nestejné znaky, ale jedna sekvence je kratší, kratší sekvence bude menší než delší. Jinými slovy, "Cat" je menší než "kočky".

### <a name="example"></a>Příklad

```cpp
#include <string>
#include <string_view>

using namespace std;

int main()
{
    string_view sv1 { "ABA" };
    string_view sv2{ "ABAC" };
    string_view sv3{ "ABAD" };
    string_view sv4{ "ABACE" };

    bool result = sv2 > sv1; // true
    result = sv3 > sv2; // true
    result = sv3 != sv1; // true
    result = sv4 < sv3; // true because `C` < `D`
}
```

## <a name="op_lt_eq"></a>operátor&lt;=

Testuje, zda je objekt na levé straně operátoru menší než nebo roven objektu na pravé straně.

```cpp
template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

*pravé*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt na levé straně operátoru lexikograficky menší než nebo roven objektu na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Viz [operátor&lt;](#op_lt).

## <a name="op_lt_lt"></a>operátor&lt;&lt;

Zapíše string_view do výstupního datového proudu.

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>Parametry

*Ostr*\
výstupní datový proud, do kterého se zapisuje.

\ *str*
String_view, který se má zadat do výstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

výstupní datový proud, do kterého se zapisuje.

### <a name="remarks"></a>Poznámky

Tento operátor použijte k vložení obsahu string_view do výstupního datového proudu, například pomocí [std:: cout](iostream.md#cout).

## <a name="op_gt"></a>operátor&gt;

Testuje, zda je objekt na levé straně operátoru větší než objekt na pravé straně.

```cpp
template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

*pravé*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt na levé straně operátoru lexikograficky větší než objekt string_view na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Viz [operátor&lt;](#op_lt).

## <a name="op_gt_eq"></a>operátor&gt;=

Testuje, zda je objekt na levé straně operátoru větší než nebo roven objektu na pravé straně.

```cpp
template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

*pravé*\
Jakýkoli typ řetězce, který se dá převést, nebo objekt typu `basic_string_view`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt na levé straně operátoru lexikograficky větší než nebo roven objektu na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Viz [operátor&lt;](#op_lt).

## <a name="op_sv"></a>operátor "" sv (string_view Literal)

Sestaví string_view z řetězcového literálu. Vyžaduje `std::literals::string_view_literals`oboru názvů. 

### <a name="example"></a>Příklad

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>Viz také

[\<string_view >](../standard-library/string-view.md)
