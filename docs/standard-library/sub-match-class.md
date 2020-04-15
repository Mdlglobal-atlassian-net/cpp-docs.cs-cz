---
title: sub_match – třída
ms.date: 09/10/2018
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
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
ms.openlocfilehash: 460f79fe0f23643fafcebb64aecf2988bdb0debe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376583"
---
# <a name="sub_match-class"></a>sub_match – třída

Popisuje dílčí shodu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class BidIt>
class sub_match
    : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>Parametry

*BidIt*\
Typ iterátoru pro podzápasy.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který označuje posloupnost znaků, které odpovídají skupině zachycení ve volání [regex_match](../standard-library/regex-functions.md#regex_match) nebo [regex_search](../standard-library/regex-functions.md#regex_search). Objekty typu [match_results Class](../standard-library/match-results-class.md) drží pole těchto objektů, jeden pro každou skupinu zachycení v regulárním výrazu, který byl použit při hledání.

Pokud skupina sběru nebyla spárována, `matched` datový člen objektu obsahuje false `first` a `second` dva iterátory a (zděděné ze základny) `std::pair`jsou stejné. Pokud byla skupina zachycení `matched` spárována, platí, iterátor `first` odkazuje na první znak v cílové sekvenci, který `second` odpovídal skupině zachycení, a iterátor odkazuje na jednu pozici za posledním znakem v cílové sekvenci, která odpovídala skupině zachycení. Všimněte si, že pro `matched` zápas nulové délky člen platí, dva iterátory budou stejné a oba budou ukazovat na pozici zápasu.

Shoda nulové délky může dojít, pokud skupina zachycení se skládá výhradně z kontrolního výrazu nebo opakování, které umožňuje nula opakování. Příklad:

"^" odpovídá cílové sekvenci "a"; `sub_match` objekt odpovídající zachycení skupiny 0 obsahuje iterátory, které oba odkazují na první znak v sekvenci.

"b(a*)b" odpovídá cílové sekvenci "bb"; `sub_match` objekt odpovídající zachycení skupiny 1 obsahuje iterátory, které oba odkazují na druhý znak v sekvenci.

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ rozdílu iterátoru.|
|[Iterace](#iterator)|Typ iterátoru.|
|[value_type](#value_type)|Typ prvku|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Porovnat](#compare)|Porovnejte dílčí shodu s posloupností.|
|[Délka](#length)|Vrátí délku dílčí shody.|
|[Odpovídající](#matched)|Označuje, zda byla shoda úspěšná.|
|[Str](#str)|Převede dílčí shodu na řetězec.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor basic_string<basic_string>value_type](#op_basic_string_lt_value_type_gt)|Převrhne dílčí shodu na řetězec.|

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

**Záhlaví:** \<regex>

**Obor názvů:** std

## <a name="sub_matchcompare"></a><a name="compare"></a>sub_match::porovnat

Porovnejte dílčí shodu s posloupností.

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Dílčí shoda, se kterou chcete porovnat.

*Str*\
Řetězec, se který chcete porovnat.

*Ptr*\
Null ukončena sekvence porovnat.

### <a name="remarks"></a>Poznámky

První členská funkce porovná odpovídající `[first, second)` sekvenci `[right.first, right.second)`s odpovídající sekvenci . Druhá členská funkce porovná odpovídající `[first, second)` sekvenci s posloupností `[right.begin(), right.end())`znaků . Třetí členská funkce porovná odpovídající `[first, second)` sekvenci s posloupností `[right, right + std::char_traits<value_type>::length(right))`znaků .

Každá funkce vrátí:

záporná hodnota, pokud první rozdílná hodnota v posuzované sekvenci porovná `std::char_traits<value_type>::compare`méně než odpovídající prvek v sekvenci operandu (podle hodnoty ) nebo pokud mají obě hodnoty společnou předponu, ale cílová sekvence je delší

nula, pokud oba porovnávají stejný prvek po elementu a mají stejnou délku

kladná hodnota jinak

## <a name="sub_matchdifference_type"></a><a name="difference_type"></a>sub_match::difference_type

Typ rozdílu iterátoru.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem `iterator_traits<BidIt>::difference_type`pro .

## <a name="sub_matchiterator"></a><a name="iterator"></a>sub_match::iterátor

Typ iterátoru.

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem pro argument `Bidit`typu šablony .

## <a name="sub_matchlength"></a><a name="length"></a>sub_match::délka

Vrátí délku dílčí shody.

```cpp
difference_type length() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku odpovídající sekvence nebo nula, pokud nebyla žádná odpovídající sekvence.

## <a name="sub_matchmatched"></a><a name="matched"></a>sub_match::spárováno

Označuje, zda byla shoda úspěšná.

```cpp
bool matched;
```

### <a name="remarks"></a>Poznámky

Člen **platí** pouze v případě, `*this` že skupina zachycení přidružená byla součástí shody regulárního výrazu.

## <a name="sub_matchoperator-basic_stringltvalue_typegt"></a><a name="op_basic_string_lt_value_type_gt"></a>sub_match::value_type&lt;operátora basic_string&gt;

Převrhne dílčí shodu na řetězec.

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>Poznámky

Operátor člena `str()`vrátí .

## <a name="sub_matchstr"></a><a name="str"></a>sub_match::str

Převede dílčí shodu na řetězec.

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce `basic_string<value_type>(first, second)`vrátí .

## <a name="sub_matchvalue_type"></a><a name="value_type"></a>sub_match::value_type

Typ prvku

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem `iterator_traits<BidIt>::value_type`pro .

## <a name="see-also"></a>Viz také

[\<regulární>](../standard-library/regex.md)\
[sub_match](../standard-library/sub-match-class.md)
