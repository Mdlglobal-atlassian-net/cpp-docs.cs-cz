---
title: sub_match – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
dev_langs:
- C++
helpviewer_keywords:
- std::sub_match [C++]
- std::sub_match [C++], matched
- std::sub_match [C++], compare
- std::sub_match [C++], length
- std::sub_match [C++], str
- std::sub_match [C++], difference_type
- std::sub_match [C++], iterator
- std::sub_match [C++], value_type
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2349beadb5983c85059be83ee5a933689913886
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722719"
---
# <a name="submatch-class"></a>sub_match – třída

Popisuje dílčí shoda.

## <a name="syntax"></a>Syntaxe

```cpp
template <class BidIt>
class sub_match
 : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>Parametry

*BidIt*<br/>
Typ iterátoru pro dílčí shody.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který určuje posloupnost znaků, které odpovídá skupině zachycení ve volání [regex_match –](../standard-library/regex-functions.md#regex_match) nebo [regex_search –](../standard-library/regex-functions.md#regex_search). Objekty typu [match_results – třída](../standard-library/match-results-class.md) obsahují pole hodnot tyto objekty, jeden pro každou skupinou zachycení v regulárním výrazu, který byl použit v hledání.

Pokud se skupina zachycení odpovídá objektu datový člen `matched` obsahuje hodnotu false a dvěma iterátory `first` a `second` (zděděné ze základní třídy `std::pair`) jsou si rovny. Pokud byla odpovídající skupina zachycení, `matched` obsahuje hodnotu true, iterátor `first` odkazuje na první znak v cílové sekvenci, který odpovídá skupině zachycení a iterátor `second` odkazuje jednu pozici za posledním znakem v cíli pořadí, který odpovídá skupině zachycení. Všimněte si, že pro nulové délky odpovídat členu `matched` obsahuje hodnotu true, bude rovnat dvěma iterátory a obě bude odkazovat na pozici shody.

Shoda nulovou délkou může dojít při zachycení skupina se skládá pouze z kontrolní výraz nebo o opakování, který umožňuje nula opakování. Příklad:

"^" odpovídá cílové sekvenci "a"; `sub_match` objektu odpovídající skupinu 0 zachycení obsahuje iterátory obě přejděte prvního znaku v sekvenci.

"b(a*) b" odpovídá cílové sekvenci "bb"; `sub_match` objektu odpovídající skupinu zachycení 1 obsahuje iterátory obě přejděte na druhém znaku v sekvenci.

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ rozdílu iterátoru.|
|[iterátor](#iterator)|Typ iterátoru.|
|[value_type](#value_type)|Typ prvku|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[compare](#compare)|Porovnejte dílčí shoda proti sekvenci.|
|[Délka](#length)|Vrátí délku objektu dílčí shoda.|
|[Shoda](#matched)|Označuje, pokud byla úspěšná shoda.|
|[str](#str)|Dílčí shoda převede na řetězec.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[Operator basic_string < value_type >](#op_basic_string_lt_value_type_gt)|Dílčí shoda přetypování na řetězec.|

## <a name="example"></a>Příklad

```cpp
// std__regex__sub_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;

    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);
    std::cout << "difference == " << dif << std::endl;

    std::csub_match::iterator first = sub.first;
    std::csub_match::iterator last = sub.second;
    std::cout << "range == " << std::string(first, last)
        << std::endl;
    std::cout << "string == " << sub << std::endl;

    std::csub_match::value_type const *ptr = "aab";
    std::cout << "compare(\"aab\") == "
        << sub.compare(ptr) << std::endl;
    std::cout << "compare(string) == "
        << sub.compare(std::string("AAA")) << std::endl;
    std::cout << "compare(sub) == "
        << sub.compare(sub) << std::endl;

    return (0);
    }
```

```Output
matched == true
length == 3
difference == 3
range == aaa
string == aaa
compare("aab") == -1
compare(string) == 1
compare(sub) == 0
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regulární výraz >

**Namespace:** std

## <a name="compare"></a>  sub_match::Compare

Porovnejte dílčí shoda proti sekvenci.

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Dílčí shoda pro porovnání.

*str*<br/>
Řetězec, který má být porovnán s.

*ptr*<br/>
Posloupnost zakončená hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

První členská funkce porovná odpovídající pořadí `[first, second)` odpovídající pořadí `[right.first, right.second)`. Druhá členská funkce porovná odpovídající pořadí `[first, second)` na sekvenci znaků `[right.begin(), right.end())`. Třetí členská funkce porovná odpovídající pořadí `[first, second)` na sekvenci znaků `[right, right + std::char_traits<value_type>::length(right))`.

Každá funkce vrátí:

Záporná hodnota, pokud první různý hodnotu odpovídající postupně porovnává méně než odpovídající element v sekvenci operandů (počítáno od `std::char_traits<value_type>::compare`), nebo pokud máte dva běžnou předponu, ale cílové sekvenci je delší

nula, pokud dva porovnání rovna prvek po prvku a mít stejnou délku

jinak kladnou hodnotu

## <a name="difference_type"></a>  sub_match::difference_type

Typ rozdílu iterátoru.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro `iterator_traits<BidIt>::difference_type`.

## <a name="iterator"></a>  sub_match::iterator

Typ iterátoru.

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro argument šablony typu `Bidit`.

## <a name="length"></a>  sub_match::length

Vrátí délku objektu dílčí shoda.

```cpp
difference_type length() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku odpovídající pořadí nebo nula, pokud se žádný odpovídající pořadí.

## <a name="matched"></a>  sub_match::matched

Označuje, pokud byla úspěšná shoda.

```cpp
bool matched;
```

### <a name="remarks"></a>Poznámky

Obsahuje člen **true** pouze v případě, že přidružené skupině zachycení `*this` byla součástí shoda s regulárním výrazem.

## <a name="op_basic_string_lt_value_type_gt"></a>  sub_match::Operator basic_string&lt;value_type&gt;

Dílčí shoda přetypování na řetězec.

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>Poznámky

Členský operátor vrátí `str()`.

## <a name="str"></a>  sub_match::str

Dílčí shoda převede na řetězec.

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `basic_string<value_type>(first, second)`.

## <a name="value_type"></a>  sub_match::value_type

Typ prvku

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro `iterator_traits<BidIt>::value_type`.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)<br/>
[sub_match](../standard-library/sub-match-class.md)<br/>
