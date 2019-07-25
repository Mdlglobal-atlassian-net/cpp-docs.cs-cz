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
ms.openlocfilehash: 07ec6f0dc9daaec19fa97a6220da4d4ea93b254b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447432"
---
# <a name="submatch-class"></a>sub_match – třída

Popisuje podshodu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class BidIt>
class sub_match
    : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>Parametry

*BidI*\
Typ iterátoru pro podshody.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který určuje sekvenci znaků, která se shoduje se skupinou zachycení ve volání [regex_match](../standard-library/regex-functions.md#regex_match) nebo [regex_search](../standard-library/regex-functions.md#regex_search). Objekty typu [třídy match_results](../standard-library/match-results-class.md) obsahují pole těchto objektů, jeden pro každou skupinu zachycení v regulárním výrazu, který byl použit ve vyhledávání.

Pokud se skupina zachycení neshodovala `matched` s datovým členem objektu, je uložena hodnota false a dva `first` iterátory `second` a (zděděné ze `std::pair`základní) jsou stejné. Pokud se skupina zachycení shodovala, `matched` je hodnota true, iterátor `first` ukazuje na první znak v cílové sekvenci, který se shoduje se skupinou zachycení, a iterátor `second` ukazuje jednu pozici za posledním znakem v cíli. sekvence, která se shodovala se skupinou zachycení. Všimněte si, že u hodnoty s nulovou délkou `matched` má člen hodnotu true, dva iterátory budou stejné a obě budou ukazovat na pozici shody.

Pokud se skupina zachycení skládá výhradně z kontrolního výrazu nebo opakování, které umožňuje nula opakování, může dojít k porovnávání s nulovou délkou. Příklad:

"^" odpovídá cílové sekvenci "a"; `sub_match` objekt odpovídající skupině zachycení 0 uchovává iterátory, které odkazují na první znak v sekvenci.

"b (a *) b" odpovídá cílové sekvenci "BB"; `sub_match` objekt odpovídající skupině zachycení 1 obsahuje iterátory, které odkazují na druhý znak v sekvenci.

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ rozdílu iterátoru.|
|[iterator](#iterator)|Typ iterátoru.|
|[value_type](#value_type)|Typ prvku|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[compare](#compare)|Porovnat dílčí shodu s posloupností.|
|[length](#length)|Vrátí délku podshody.|
|[vzájem](#matched)|Určuje, zda shoda proběhla úspěšně.|
|[str](#str)|Převede dílčí shodu na řetězec.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator basic_string < value_type >](#op_basic_string_lt_value_type_gt)|Přetypování odpovídá na řetězec.|

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

**Hlavička:** \<> regulárního výrazu

**Obor názvů:** std

## <a name="compare"></a>sub_match:: Compare

Porovnat dílčí shodu s posloupností.

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Shoda pro porovnání s.

*str*\
Řetězec, na který se má porovnat.

*střed*\
Sekvence zakončená hodnotou null pro porovnání.

### <a name="remarks"></a>Poznámky

První členská funkce porovná odpovídající `[first, second)` sekvenci s odpovídající sekvencí. `[right.first, right.second)` Druhá členská funkce porovnává odpovídající sekvenci `[first, second)` se sekvencí `[right.begin(), right.end())`znaků. Třetí členská funkce porovnává odpovídající sekvenci `[first, second)` se sekvencí `[right, right + std::char_traits<value_type>::length(right))`znaků.

Každá funkce vrátí:

záporná hodnota v případě, že první odlišná hodnota v porovnané sekvenci porovnává méně než odpovídající element v sekvenci operandů (jak `std::char_traits<value_type>::compare`je určeno), nebo pokud mají dva společný prefix, ale cílová sekvence je delší

nula, pokud dva porovnat rovnající se elementu a mají stejnou délku

kladná hodnota, jinak

## <a name="difference_type"></a>sub_match::d ifference_type

Typ rozdílu iterátoru.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro `iterator_traits<BidIt>::difference_type`.

## <a name="iterator"></a>sub_match:: iterátor

Typ iterátoru.

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro argument `Bidit`typu šablony.

## <a name="length"></a>sub_match:: Length

Vrátí délku podshody.

```cpp
difference_type length() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku porovnané sekvence nebo hodnotu nula, pokud neexistuje odpovídající sekvence.

## <a name="matched"></a>sub_match:: matched

Určuje, zda shoda proběhla úspěšně.

```cpp
bool matched;
```

### <a name="remarks"></a>Poznámky

Člen má **hodnotu true** pouze v případě, že skupina zachycení `*this` přidružená k byla součástí regulárního výrazu.

## <a name="op_basic_string_lt_value_type_gt"></a>sub_match:: operator basic_string&lt;value_type&gt;

Přetypování odpovídá na řetězec.

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>Poznámky

Vrátí `str()`operátor member.

## <a name="str"></a>sub_match:: str

Převede dílčí shodu na řetězec.

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>Poznámky

Vrátí `basic_string<value_type>(first, second)`členské funkce.

## <a name="value_type"></a>sub_match::value_type

Typ prvku

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro `iterator_traits<BidIt>::value_type`.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)\
[sub_match](../standard-library/sub-match-class.md)
