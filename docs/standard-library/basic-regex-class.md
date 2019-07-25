---
title: basic_regex – třída
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 8df9e927c430f3b94f5857bf18f575e79d6b922a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453438"
---
# <a name="basicregex-class"></a>basic_regex – třída

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

Třída šablony popisuje objekt, který obsahuje regulární výraz. Objekty této třídy šablony lze předat do šablon Functions [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)a [regex_replace](../standard-library/regex-functions.md#regex_replace)spolu s vhodnými textovými řetězci řetězce pro hledání textu, který odpovídá regulárnímu výrazu. Existují dvě specializace této třídy šablony s definicemi typu [regulárního výrazu](../standard-library/regex-typedefs.md#regex) pro prvky typu **char**a [wregex –](../standard-library/regex-typedefs.md#wregex) pro prvky typu **wchar_t**.

Argument šablony *RXtraits* popisuje různé důležité vlastnosti syntaxe regulárních výrazů, které podporuje třída šablony. Třída, která určuje tyto vlastnosti regulárního výrazu, musí mít stejné externí rozhraní jako objekt třídy Template třídy [regex_traits](../standard-library/regex-traits-class.md).

Některé funkce provádějí sekvenci operandu, která definuje regulární výraz. Tuto sekvenci operandů můžete zadat několika způsoby:

`ptr`--sekvence zakončená hodnotou null (například řetězec jazyka C, pro *elem* typu **char** `ptr` ) od (nesmí se jednat o nulový ukazatel), kde ukončující prvek je hodnota `value_type()` a není součástí posloupnosti operandů.

`ptr`, `count` -- `count` sekvence elementů začínajících na `ptr` (nesmí být ukazatel s hodnotou null)

`str`--sekvence určená `basic_string` objektem`str`

`first`, `last` --posloupnost prvků oddělených `first` iterátory a `last`v rozsahu`[first, last)`

`right`-- `basic_regex` objekt`right`

Tyto členské funkce také přebírají argument `flags` , který určuje různé možnosti pro výklad regulárního výrazu kromě těch, které jsou popsány typem *RXtraits* .

### <a name="members"></a>Členové

|Člen|Výchozí hodnota|
|-|-|
|veřejné statické const flag_type icase|regex_constants::icase|
|flag_type veřejné statické const|regex_constants::nosubs|
|flag_type optimalizovat veřejné statické const|regex_constants::optimize|
|flag_type kompletování veřejných statických const|regex_constants::collate|
|public static const flag_type ECMAScript|regex_constants::ECMAScript|
|veřejné statické const flag_type Basic|regex_constants::basic|
|veřejný statický const flag_type – rozšířený|regex_constants::extended|
|veřejné statické const flag_type awk mají|regex_constants::awk|
|veřejný statický const flag_type grep|regex_constants::grep|
|veřejné statické const flag_type egrep|regex_constants::egrep|
|soukromé vlastnosti RXtraits||

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_regex](#basic_regex)|Vytvořte objekt regulárního výrazu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[flag_type](#flag_type)|Typ příznaků možností syntaxe.|
|[locale_type](#locale_type)|Typ uloženého objektu národního prostředí.|
|[value_type](#value_type)|Typ elementu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[assign](#assign)|Přiřadí hodnotu objektu regulárního výrazu.|
|[Flag](#flags)|Vrátí příznaky možnosti syntaxe.|
|[getloc](#getloc)|Vrátí uložený objekt národního prostředí.|
|[imbue –](#imbue)|Změní uložený objekt národního prostředí.|
|[mark_count](#mark_count)|Vrátí počet odpovídajících dílčích výrazů.|
|[swap](#swap)|Prohodí dva objekty regulárních výrazů.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnotu objektu regulárního výrazu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> regulárního výrazu

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

## <a name="assign"></a>basic_regex:: Assign

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
Třída vlastností pro zdroj řetězce

*STalloc*\
Třída přidělování pro zdroj řetězce

*For*\
Typ iterátoru vstupu pro zdroj rozsahu.

*Kliknutím*\
Zdroj regulárního výrazu, který se má zkopírovat

*střed*\
Ukazatel na začátek sekvence ke zkopírování.

*Flag*\
Příznaky možností syntaxe, které se mají přidat při kopírování

*len/TD >* \
Délka sekvence, která se má zkopírovat

*str*\
Řetězec, který se má zkopírovat

*první*\
Začátek sekvence, která se má zkopírovat

*posledního*\
Konec sekvence ke zkopírování.

*IList*\
Initializer_list, který se má zkopírovat

### <a name="remarks"></a>Poznámky

Členské funkce každé nahradí regulární výraz uložený `*this` pomocí regulárního výrazu popsanýho sekvencí operandu a pak vrátí. `*this`

## <a name="basic_regex"></a>basic_regex::basic_regex

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
Třída vlastností pro zdroj řetězce

*STalloc*\
Třída přidělování pro zdroj řetězce

*For*\
Typ iterátoru vstupu pro zdroj rozsahu.

*Kliknutím*\
Zdroj regulárního výrazu, který se má zkopírovat

*střed*\
Ukazatel na začátek sekvence ke zkopírování.

*Flag*\
Příznaky možností syntaxe, které se mají přidat při kopírování

*len/TD >* \
Délka sekvence, která se má zkopírovat

*str*\
Řetězec, který se má zkopírovat

*první*\
Začátek sekvence, která se má zkopírovat

*posledního*\
Konec sekvence ke zkopírování.

*IList*\
Initializer_list, který se má zkopírovat

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt typu `RXtraits`default-konstruovaný.

První konstruktor vytvoří prázdný `basic_regex` objekt. Ostatní konstruktory vytvoří `basic_regex` objekt, který obsahuje regulární výraz popsaný sekvencí operandu.

Prázdný `basic_regex` objekt neodpovídá žádné sekvenci znaků, pokud je předán do [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)nebo [regex_replace](../standard-library/regex-functions.md#regex_replace).

## <a name="flag_type"></a>  basic_regex::flag_type

Typ příznaků možností syntaxe.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro [regex_constants:: syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="flags"></a>basic_regex:: Flags

Vrátí příznaky možnosti syntaxe.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrací hodnotu `flag_type` argumentu předaného k poslednímu volání jedné z [basic_regex:: Assign](#assign) Member functions nebo, pokud žádné takové volání nebylo provedeno, hodnota předaná konstruktoru.

## <a name="getloc"></a>basic_regex:: getloc

Vrátí uložený objekt národního prostředí.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `traits.` [regex_traits:: getloc](../standard-library/regex-traits-class.md#getloc)`()`.

## <a name="imbue"></a>basic_regex:: imbue –

Změní uložený objekt národního prostředí.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Objekt národního prostředí, který se má uložit

### <a name="remarks"></a>Poznámky

Členská funkce se `*this` vyprázdní `traits.`a vrátí [regex_traits:: imbue –](../standard-library/regex-traits-class.md#imbue)`(loc)`.

## <a name="locale_type"></a>basic_regex::locale_type

Typ uloženého objektu národního prostředí.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro [regex_traits:: locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="mark_count"></a>basic_regex::mark_count

Vrátí počet odpovídajících dílčích výrazů.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet skupin zachycení v regulárním výrazu.

## <a name="op_eq"></a>basic_regex:: operator =

Přiřadí hodnotu objektu regulárního výrazu.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Parametry

*STtraits*\
Třída vlastností pro zdroj řetězce

*STalloc*\
Třída přidělování pro zdroj řetězce

*Kliknutím*\
Zdroj regulárního výrazu, který se má zkopírovat

*str*\
Řetězec, který se má zkopírovat

### <a name="remarks"></a>Poznámky

Jednotlivé operátory nahrazují regulární výraz uložený `*this` pomocí regulárního výrazu popsanýho sekvencí operandu a pak vrátí. `*this`

## <a name="swap"></a>  basic_regex::swap

Prohodí dva objekty regulárních výrazů.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Objekt regulárního výrazu, pomocí kterého se má prohodit.

### <a name="remarks"></a>Poznámky

Členská funkce odměňuje regulární výrazy mezi `*this` a *vpravo*. Provede to v konstantním čase a nevyvolává žádné výjimky.

## <a name="value_type"></a>basic_regex::value_type

Typ elementu.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *elem*.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)\
[regex_match](../standard-library/regex-functions.md#regex_match)\
[regex_search](../standard-library/regex-functions.md#regex_search)\
[regex_replace](../standard-library/regex-functions.md#regex_replace)\
[regex](../standard-library/regex-typedefs.md#regex)\
[wregex](../standard-library/regex-typedefs.md#wregex)\
[regex_traits – třída](../standard-library/regex-traits-class.md)
