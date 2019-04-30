---
title: '&lt;string_view&gt; operátory'
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
ms.openlocfilehash: 1fbb7faf7d6fc92a053c0f4d47575c5c53c7968e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346629"
---
# <a name="ltstringviewgt-operators"></a>&lt;string_view&gt; operátory

Pomocí těchto operátorů můžete porovnat dva objekty string_view nebo string_view a druhý objekt řetězce (například [std::string](basic-string-class.md), nebo **char\***) pro který je k dispozici implicitní převod. 

||||
|-|-|-|
|[operator!=](#op_neq)|[– Operátor&gt;](#op_gt)|[– Operátor&gt;=](#op_gt_eq)|
|[– Operátor&lt;](#op_lt)|[– Operátor&lt;&lt;](#op_lt_lt)|[– Operátor&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|[operator""sv](#op_sv)|

## <a name="op_neq"></a> Operator! =

Testuje, zda je objekt na levé straně operátoru není roven objektu na pravé straně.

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

*doleva*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

*doprava*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud objekt na levé straně operátoru není lexikograficky stejný objekt na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Musí existovat implicitní převod z *convertible_string_type* k string_view na druhé straně. 

Porovnání je založen na pairwise lexicographical porovnání sekvence znaků. Pokud mají stejný počet prvků a elementů jsou na stejné úrovni, jsou oba objekty stejné. V opačném případě nerovnost.

## <a name="op_eq_eq"></a> Operator ==

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

*doleva*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

*doprava*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je objekt na levé straně operátoru lexikograficky stejný objekt na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Musí existovat implicitní převod z *convertible_string_type* k string_view na druhé straně. 

Porovnání je založen na pairwise lexicographical porovnání sekvence znaků. Pokud mají stejný počet prvků a elementů jsou na stejné úrovni, jsou oba objekty stejné.


## <a name="op_lt"></a> – Operátor&lt;

Testuje, zda je objekt na levé straně operátoru menší než objekt na správný sidestring_view
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

*doleva*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

*doprava*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je objekt na levé straně operátoru méně lexikografický, než objekt na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Musí existovat implicitní převod z *convertible_string_type* k string_view na druhé straně. 

Porovnání je založen na pairwise lexicographical porovnání sekvence znaků. Při první nerovnost pár znaků nalezen, výsledek tohoto porovnání se vrátí. Pokud se nenajdou žádné nerovnost znaky, ale jedním sekvenčním je kratší, kratší pořadí je menší než ten, který delší dobu. Jinými slovy "cat" je menší než "cats".

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

## <a name="op_lt_eq"></a> – Operátor&lt;=

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

*doleva*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

*doprava*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je objekt na levé straně operátoru méně lexikografický, než nebo roven objektu na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Zobrazit [operátor&lt;](#op_lt).

## <a name="op_lt_lt"></a> – Operátor&lt;&lt;

String_view zapíše do výstupního proudu.

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>Parametry

*Ostr*<br/>
výstupní datový proud do.

*Str*<br/>
String_view se zapisují do výstupního proudu.

### <a name="return-value"></a>Návratová hodnota

výstupní datový proud do.

### <a name="remarks"></a>Poznámky

Operátor vložení obsahu string_view do výstupní datový proud, třeba v [std::cout](iostream.md#cout).

## <a name="op_gt"></a> – Operátor&gt;

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

*doleva*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

*doprava*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je objekt na levé straně operátoru lexikograficky větší než string_view objekt na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Zobrazit [operátor&lt;](#op_lt).

## <a name="op_gt_eq"></a> – Operátor&gt;=

Testuje, zda je objekt na levé straně operátoru větší než nebo stejný jako objekt na pravé straně.

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

*doleva*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

*doprava*<br/>
Jakýkoli typ lze převést řetězec nebo objekt typu `basic_string_view` k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je objekt na levé straně operátoru lexikograficky větší než nebo roven objektu na pravé straně; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Zobrazit [operátor&lt;](#op_lt).

## <a name="op_sv"></a> operátor"" sv (string_view literál)

Sestaví string_view z řetězcového literálu. Obor názvů vyžaduje `std::literals::string_view_literals`. 

### <a name="example"></a>Příklad

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>Viz také:

[\<string_view>](../standard-library/string-view.md)<br/>
