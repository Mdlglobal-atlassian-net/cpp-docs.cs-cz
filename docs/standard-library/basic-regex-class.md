---
title: basic_regex – třída
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 74a8684c619e2cfbd5417950aa6108ad93511bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376751"
---
# <a name="basic_regex-class"></a>basic_regex – třída

Zabalí regulární výraz.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>Parametry

*Elem*\
Typ prvků, které se mají spárovat.

*RXtraits*\
Třída vlastností prvků.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který obsahuje regulární výraz. Objekty této šablony třídy mohou být předány funkcím šablony [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)a [regex_replace](../standard-library/regex-functions.md#regex_replace)spolu s vhodnými argumenty textového řetězce, aby se vyhledal text, který odpovídá regulárnímu výrazu. Existují dvě specializace této šablony třídy s [regulárním výrazem](../standard-library/regex-typedefs.md#regex) definice typu pro prvky typu **char**a [wregex](../standard-library/regex-typedefs.md#wregex) pro prvky typu **wchar_t**.

Argument šablony *RXtraits* popisuje různé důležité vlastnosti syntaxe regulárních výrazů, které šablona třídy podporuje. Třída, která určuje tyto znaky regulárních výrazů, musí mít stejné externí rozhraní jako objekt typu [regex_traits Class](../standard-library/regex-traits-class.md).

Některé funkce provádějí sekvenci operandu, která definuje regulární výraz. Tuto sekvenci operandů můžete zadat několika způsoby:

`ptr`-- sekvence ukončená hodnotou null (například řetězec C, pro `ptr` *Elem* typu **char)** začínající na (což nesmí `value_type()` být ukazatel null), kde ukončující prvek je hodnota a není součástí operandské sekvence

`ptr`, `count` -- posloupnost prvků začínajících `count` na `ptr` (což nesmí být ukazatel null)

`str`-- pořadí určené `basic_string` objektem`str`

`first`, `last` -- posloupnost prvků vymezených iterátory `first` a `last`, v rozsahu`[first, last)`

`right`-- `basic_regex` objekt`right`

Tyto členské funkce také `flags` přijmout argument, který určuje různé možnosti pro interpretaci regulárního výrazu kromě těch, které jsou popsány typu *RXtraits.*

### <a name="members"></a>Členové

|Člen|Výchozí hodnota|
|-|-|
|veřejné statické const flag_type icase|regex_constants::icase|
|veřejné statické const flag_type nosubs|regex_constants::nosubs|
|veřejné statické const flag_type optimalizovat|regex_constants::optimalizace|
|veřejné statické const flag_type shrnout|regex_constants::kompletovat|
|veřejné statické const flag_type ECMAScript|regex_constants::ECMAScript|
|veřejné statické const flag_type základní|regex_constants::základní|
|veřejné statické const flag_type rozšířené|regex_constants::prodlouženo|
|veřejné statické const flag_type awk|regex_constants::awk|
|veřejné statické const flag_type grep|regex_constants::grep|
|veřejné statické const flag_type egrep|regex_constants::egrep|
|soukromé RXtraits rysy||

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_regex](#basic_regex)|Vytvořte objekt regulárního výrazu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[flag_type](#flag_type)|Typ příznaků možností syntaxe.|
|[locale_type](#locale_type)|Typ uloženého objektu národního prostředí.|
|[value_type](#value_type)|Typ prvku.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Přiřadit](#assign)|Přiřadí hodnotu objektu regulárního výrazu.|
|[příznaky](#flags)|Vrátí příznaky možností syntaxe.|
|[getloc](#getloc)|Vrátí uložený objekt národního prostředí.|
|[Naplnit](#imbue)|Změní uložený objekt národního prostředí.|
|[mark_count](#mark_count)|Vrátí odpovídající počet podvýrazů.|
|[Swap](#swap)|Zamění dva objekty regulárních výrazů.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnotu objektu regulárního výrazu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex>

**Obor názvů:** std

## <a name="example"></a>Příklad

```cpp
// std__regex__basic_regex.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);
    cout << "match(\"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}
```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
match("abc") == true
```

## <a name="basic_regexassign"></a><a name="assign"></a>basic_regex::přiřadit

Přiřadí hodnotu objektu regulárního výrazu.

```cpp
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,
    size_type len,
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags = ECMAScript);

template <class InIt>
basic_regex& assign(
    InIt first, InIt last,
    flag_type flags = ECMAScript);
```

### <a name="parameters"></a>Parametry

*STtraits*\
Vlastnosti třídy pro zdroj řetězce.

*STalloc*\
Třída alokátoru pro zdroj řetězce.

*Init*\
Zadejte typ iterátoru pro zdroj rozsahu.

*Právo*\
Regex zdroj ke kopírování.

*Ptr*\
Ukazatel na začátek sekvence ke kopírování.

*Příznaky*\
Příznaky možností Syntaxe, které chcete přidat při kopírování.

*>*\
Délka sekvence ke kopírování.

*Str*\
Řetězec ke kopírování.

*První*\
Začátek sekvence ke kopírování.

*Poslední*\
Konec sekvence ke kopírování.

*Ilist*\
initializer_list kopírovat.

### <a name="remarks"></a>Poznámky

Členské funkce nahradí regulární `*this` výraz, který je v držení, regulárním výrazem popsaným operandovou sekvencí a poté vrátí `*this`.

## <a name="basic_regexbasic_regex"></a><a name="basic_regex"></a>basic_regex::basic_regex

Vytvořte objekt regulárního výrazu.

```cpp
basic_regex();

explicit basic_regex(
    const Elem* ptr,
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,
    size_type len,
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,
    flag_type flags);

template <class STtraits, class STalloc>
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags);

template <class InIt>
explicit basic_regex(
    InIt first,
    InIt last,
    flag_type flags);
```

### <a name="parameters"></a>Parametry

*STtraits*\
Vlastnosti třídy pro zdroj řetězce.

*STalloc*\
Třída alokátoru pro zdroj řetězce.

*Init*\
Zadejte typ iterátoru pro zdroj rozsahu.

*Právo*\
Regex zdroj ke kopírování.

*Ptr*\
Ukazatel na začátek sekvence ke kopírování.

*Příznaky*\
Příznaky možností Syntaxe, které chcete přidat při kopírování.

*>*\
Délka sekvence ke kopírování.

*Str*\
Řetězec ke kopírování.

*První*\
Začátek sekvence ke kopírování.

*Poslední*\
Konec sekvence ke kopírování.

*Ilist*\
initializer_list kopírovat.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají výchozí objekt `RXtraits`typu .

První konstruktor vytvoří prázdný `basic_regex` objekt. Ostatní konstruktory vytvořit `basic_regex` objekt, který obsahuje regulární výraz popsaný operand sekvence.

Prázdný `basic_regex` objekt neodpovídá žádné posloupnosti znaků při předání [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)nebo [regex_replace](../standard-library/regex-functions.md#regex_replace).

## <a name="basic_regexflag_type"></a><a name="flag_type"></a>basic_regex::flag_type

Typ příznaků možností syntaxe.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="basic_regexflags"></a><a name="flags"></a>basic_regex::příznaky

Vrátí příznaky možností syntaxe.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu argumentu `flag_type` předaného poslednímu volání jedné z [basic_regex::assign](#assign) member functions nebo, pokud nebylo provedeno žádné takové volání, hodnotu předanou konstruktoru.

## <a name="basic_regexgetloc"></a><a name="getloc"></a>basic_regex::getloc

Vrátí uložený objekt národního prostředí.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce `traits.`vrátí [regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`.

## <a name="basic_regeximbue"></a><a name="imbue"></a>basic_regex::imbue

Změní uložený objekt národního prostředí.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Objekt národního prostředí, který chcete uložit.

### <a name="remarks"></a>Poznámky

Členská funkce `*this` vyprázdní a `traits.`vrátí [regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`.

## <a name="basic_regexlocale_type"></a><a name="locale_type"></a>basic_regex::locale_type

Typ uloženého objektu národního prostředí.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="basic_regexmark_count"></a><a name="mark_count"></a>basic_regex::mark_count

Vrátí odpovídající počet podvýrazů.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet skupin zachycení v regulárním výrazu.

## <a name="basic_regexoperator"></a><a name="op_eq"></a>basic_regex::operátor=

Přiřadí hodnotu objektu regulárního výrazu.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Parametry

*STtraits*\
Vlastnosti třídy pro zdroj řetězce.

*STalloc*\
Třída alokátoru pro zdroj řetězce.

*Právo*\
Regex zdroj ke kopírování.

*Str*\
Řetězec ke kopírování.

### <a name="remarks"></a>Poznámky

Každý operátor nahradí regulární `*this` výraz, který je v držení, regulárním výrazem popsaným operandovou sekvencí a poté vrátí `*this`.

## <a name="basic_regexswap"></a><a name="swap"></a>basic_regex::swap

Zamění dva objekty regulárních výrazů.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt regulárního výrazu, se kterým chcete zaměnit.

### <a name="remarks"></a>Poznámky

Členská funkce zamění regulární výrazy mezi `*this` a *vpravo*. Činí tak v konstantním čase a nevyvolá žádné výjimky.

## <a name="basic_regexvalue_type"></a><a name="value_type"></a>basic_regex::value_type

Typ prvku.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony *Elem*.

## <a name="see-also"></a>Viz také

[\<regulární>](../standard-library/regex.md)\
[regex_match](../standard-library/regex-functions.md#regex_match)\
[regex_search](../standard-library/regex-functions.md#regex_search)\
[regex_replace](../standard-library/regex-functions.md#regex_replace)\
[Regex](../standard-library/regex-typedefs.md#regex)\
[wregex](../standard-library/regex-typedefs.md#wregex)\
[regex_traits – třída](../standard-library/regex-traits-class.md)
