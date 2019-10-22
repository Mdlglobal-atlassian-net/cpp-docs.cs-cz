---
title: match_results – třída
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: c282791fb0ff85c0c8818c6905c51703614f4675
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689390"
---
# <a name="match_results-class"></a>match_results – třída

Obsahuje posloupnost dílčích shod.

## <a name="syntax"></a>Syntaxe

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>Parametry

@No__t_1 *BiDi*
Typ iterátoru pro podshody.

@No__t_1 *přidělení*
Typ alokátoru pro správu úložiště

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který ovládá neupravitelnou sekvenci prvků typu `sub_match<BidIt>` generovaných hledáním regulárního výrazu. Každý prvek odkazuje na dílčí sekvenci, která odpovídá skupině zachycení odpovídající tomuto prvku.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[match_results](#match_results)|Vytvoří objekt.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ alokátoru pro správu úložiště|
|[char_type](#char_type)|Typ prvku|
|[const_iterator](#const_iterator)|Typ iterátoru const pro podshody.|
|[const_reference](#const_reference)|Typ odkazu const elementu.|
|[difference_type](#difference_type)|Typ rozdílu iterátoru.|
|[iterátor](#iterator)|Typ iterátoru pro podshody.|
|[odkaz](#reference)|Typ odkazu elementu.|
|[size_type](#size_type)|Typ počtu odpovídajících položek.|
|[string_type](#string_type)|Typ řetězce.|
|[value_type](#value_type)|Typ podshody.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[ifunctiondiscovery](#begin)|Určuje začátek posloupnosti porovnávání.|
|[obsahovat](#empty)|Testuje neshody.|
|[účelu](#end)|Označuje konec posloupnosti porovnávání.|
|[formátovat](#format)|Formátuje dílčí shody.|
|[get_allocator](#get_allocator)|Vrátí uložený Alokátor.|
|[časový](#length)|Vrátí délku podshody.|
|[max_size](#max_size)|Získá největší počet podshod.|
|[poziční](#position)|Získá počáteční posun podskupiny.|
|[směr](#prefix)|Získá sekvenci před prvním podshodou.|
|[hodnota](#size)|Spočítá počet podshod.|
|[str](#str)|Vrátí podshodu.|
|[auditování](#suffix)|Získá sekvenci po poslední shodě.|
|[adresu](#swap)|Zahodí dva objekty match_results.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Zkopírujte objekt match_results.|
|[operátor \[ \]](#op_at)|Přístup k podobjektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex >

**Obor názvů:** std

## <a name="example"></a>Příklad

```cpp
// std__regex__match_results.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::cout << "prefix: matched == " << std::boolalpha
        << mr.prefix().matched
        << ", value == " << mr.prefix() << std::endl;
    std::cout << "whole match: " << mr.length() << " chars, value == "
        << mr.str() << std::endl;
    std::cout << "suffix: matched == " << std::boolalpha
        << mr.suffix().matched
        << ", value == " << mr.suffix() << std::endl;
    std::cout << std::endl;

    std::string fmt("\"c(a*)|(b)\" matched \"$&\"\n"
        "\"(a*)\" matched \"$1\"\n"
        "\"(b)\" matched \"$2\"\n");
    std::cout << mr.format(fmt) << std::endl;
    std::cout << std::endl;

    // index through submatches
    for (size_t n = 0; n < mr.size(); ++n)
    {
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha
            << mr[n].matched <<
            " at position " << mr.position(n) << std::endl;
        std::cout << "  " << mr.length(n)
            << " chars, value == " << mr[n] << std::endl;
    }
    std::cout << std::endl;

    // iterate through submatches
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)
    {
        std::cout << "next submatch: matched == " << std::boolalpha
            << it->matched << std::endl;
        std::cout << "  " << it->length()
            << " chars, value == " << *it << std::endl;
    }
    std::cout << std::endl;

    // other members
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;

    std::cmatch::allocator_type al = mr.get_allocator();
    std::cmatch::string_type str = std::string("x");
    std::cmatch::size_type maxsiz = mr.max_size();
    std::cmatch::char_type ch = 'x';
    std::cmatch::difference_type dif = mr.begin() - mr.end();
    std::cmatch::const_iterator cit = mr.begin();
    std::cmatch::value_type val = *cit;
    std::cmatch::const_reference cref = val;
    std::cmatch::reference ref = val;

    maxsiz = maxsiz;  // to quiet "unused" warnings
    if (ref == cref)
        ch = ch;
    dif = dif;

    return (0);
}
```

```Output
prefix: matched == true, value == x
whole match: 4 chars, value == caaa
suffix: matched == true, value == y

"c(a*)|(b)" matched "caaa"
"(a*)" matched "aaa"
"(b)" matched ""

submatch[0]: matched == true at position 1
  4 chars, value == caaa
submatch[1]: matched == true at position 2
  3 chars, value == aaa
submatch[2]: matched == false at position 6
  0 chars, value ==

next submatch: matched == true
  4 chars, value == caaa
next submatch: matched == true
  3 chars, value == aaa
next submatch: matched == false
  0 chars, value ==

empty == false
```

## <a name="allocator_type"></a>match_results::allocator_type

Typ alokátoru pro správu úložiště

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro *přidělení*argumentu šablony.

## <a name="begin"></a>match_results:: begin

Určuje začátek posloupnosti porovnávání.

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor náhodného přístupu, který odkazuje na první prvek sekvence (nebo těsně za konec prázdné sekvence).

## <a name="char_type"></a>match_results::char_type

Typ prvku

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ `iterator_traits<BidIt>::value_type`, což je typ prvku hledané sekvence znaků.

## <a name="const_iterator"></a>match_results::const_iterator

Typ iterátoru const pro podshody.

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>Poznámky

Definice typedef popisuje objekt, který může sloužit jako konstantní iterátor náhodného přístupu pro řízenou sekvenci.

## <a name="const_reference"></a>match_results::const_reference

Typ odkazu const elementu.

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

Definice typedef popisuje objekt, který může sloužit jako konstantní odkaz na prvek řízené sekvence.

## <a name="difference_type"></a>match_results::d ifference_type

Typ rozdílu iterátoru.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ `iterator_traits<BidIt>::difference_type`; popisuje objekt, který může představovat rozdíl mezi dvěma iterátory, které ukazují na prvky řízené sekvence.

## <a name="empty"></a>match_results:: Empty

Testuje neshody.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pouze v případě, že se nepovedlo hledání regulárního výrazu.

## <a name="end"></a>match_results:: end

Označuje konec posloupnosti porovnávání.

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který ukazuje hned za konec sekvence.

## <a name="format"></a>match_results:: Format

Formátuje dílčí shody.

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>Parametry

*OutIt* \
Typ výstupního iterátoru.

*\*
Výstupní tok, do kterého se má zapisovat.

*fmt* \
Řetězec formátu.

\ *příznaků*
Příznaky formátu.

### <a name="remarks"></a>Poznámky

Každá členská funkce generuje formátovaný text v ovládacím prvku formát *FMT*. První členská funkce zapíše formátovaný text do sekvence definované podle jeho argumentu *out* *a vrátí hodnotu*. Druhá členská funkce vrátí objekt String obsahující kopii formátovaného textu.

K vygenerování formátovaného textu. textový literál v řetězci formátu je obvykle zkopírován do cílové sekvence. Každá sekvence escape v řetězci formátu je nahrazena textem, který reprezentuje. Podrobnosti kopírování a nahrazování jsou ovládány příznaky formátu předanými funkci.

## <a name="get_allocator"></a>match_results::get_allocator

Vrátí uložený Alokátor.

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí kopii objektu přidělování používaného `*this` k přidělení svých objektů `sub_match`.

## <a name="iterator"></a>match_results:: iterátor

Typ iterátoru pro podshody.

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako iterátor náhodného přístupu pro řízenou sekvenci.

## <a name="length"></a>match_results:: Length

Vrátí délku podshody.

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*dílčí* \
Index podshody.

### <a name="remarks"></a>Poznámky

Členská funkce vrací `(*this)[sub].length()`.

## <a name="match_results"></a>match_results::match_results

Vytvoří objekt.

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>Parametry

\ *přidělení*
Objekt alokátoru, který se má uložit.

*pravé* \
Objekt match_results, který se má zkopírovat

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt `match_results`, který obsahuje žádné podshody. Druhý konstruktor vytvoří objekt `match_results`, který je kopií *pravého*.

## <a name="max_size"></a>match_results::max_size

Získá největší počet podshod.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku nejdelší sekvence, kterou může objekt ovládat.

## <a name="op_eq"></a>match_results:: operator =

Zkopírujte objekt match_results.

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Objekt match_results, který se má zkopírovat

### <a name="remarks"></a>Poznámky

Členský operátor nahradí sekvenci řízenou `*this` s kopií sekvence řízenou *vpravo*.

## <a name="op_at"></a>match_results:: operator [] – operátor

Přístup k podobjektu.

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>Parametry

*n* \
Index podshody

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na prvek *n* řízené sekvence nebo odkaz na prázdný objekt `sub_match`, pokud `size() <= n` nebo pokud skupina zachycení *n* nebyla součástí shody.

## <a name="position"></a>match_results::p ozice

Získá počáteční posun podskupiny.

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*dílčí* \
Index podshody

### <a name="remarks"></a>Poznámky

Členská funkce vrací `std::distance(prefix().first, (*this)[sub].first)`, to znamená, že vzdálenost od prvního znaku v cílové sekvenci k prvnímu znaku v dílčí shodě, na kterou odkazuje element `n` řízené sekvence.

## <a name="prefix"></a>match_results::p refix

Získá sekvenci před prvním podshodou.

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na objekt typu `sub_match<BidIt>`, který odkazuje na sekvenci znaků, která začíná na začátku cílové sekvence a končí v `(*this)[0].first`, tedy odkazuje na text, který předchází odpovídající podsekvenci.

## <a name="reference"></a>match_results:: Reference

Typ odkazu elementu.

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro typ `const_reference`.

## <a name="size"></a>match_results:: size

Spočítá počet podshod.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí více než počet skupin zachycení v regulárním výrazu, který byl použit pro hledání, nebo nula, pokud nebylo provedeno žádné hledání.

## <a name="size_type"></a>match_results::size_type

Typ počtu odpovídajících položek.

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro typ `Alloc::size_type`.

## <a name="str"></a>match_results:: str

Vrátí podshodu.

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*dílčí* \
Index podshody

### <a name="remarks"></a>Poznámky

Členská funkce vrací `string_type((*this)[sub])`.

## <a name="string_type"></a>match_results::string_type

Typ řetězce.

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro typ `basic_string<char_type>`.

## <a name="suffix"></a>match_results:: Přípona

Získá sekvenci po poslední shodě.

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na objekt typu `sub_match<BidIt>`, který odkazuje na sekvenci znaků, která začíná na `(*this)[size() - 1].second` a končí na konci cílové sekvence, to znamená, že odkazuje na text, který následuje v odpovídající podsekvenci.

## <a name="swap"></a>match_results:: swap

Zahodí dva objekty match_results.

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>Parametry

*pravé* \
Objekt match_results pro prohození.

### <a name="remarks"></a>Poznámky

Členská funkce odměňuje obsah `*this` a *Right* v konstantním čase a nevyvolává výjimky.

## <a name="value_type"></a>match_results::value_type

Typ podshody.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ `sub_match<BidIt>`.

## <a name="see-also"></a>Viz také:

[\<regex >](../standard-library/regex.md)
