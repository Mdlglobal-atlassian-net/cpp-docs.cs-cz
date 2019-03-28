---
title: basic_regex – třída
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: e3a38dc186a52c8431442d58bb10e56837396b07
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565448"
---
# <a name="basicregex-class"></a>basic_regex – třída

Zabalí regulární výraz.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>Parametry

*Elem*<br/>
Typ prvků, které se mají spárovat.

*RXtraits*<br/>
Třída vlastností prvků.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který obsahuje regulární výraz. Objekty této třídy šablony mohou být předány funkce šablony [regex_match –](../standard-library/regex-functions.md#regex_match), [regex_search –](../standard-library/regex-functions.md#regex_search), a [regex_replace –](../standard-library/regex-functions.md#regex_replace), spolu s vhodnými argumenty textového řetězce, Chcete-li vyhledat text, který odpovídá regulárnímu výrazu. Existují dvě specializace této třídy šablony, s definicemi typu [regulární výraz](../standard-library/regex-typedefs.md#regex) pro prvky typu **char**, a [wregex](../standard-library/regex-typedefs.md#wregex) pro prvky typu  **wchar_t**.

Argument šablony *RXtraits* popisuje různé důležité vlastnosti syntaxe regulárních výrazů, které třída šablony podporuje. Třída, která určuje tyto vlastnosti regulárního výrazu, musí mít stejné externí rozhraní jako objekt třídy šablony [regex_traits – třída](../standard-library/regex-traits-class.md).

Některé funkce provádějí sekvenci operandu, která definuje regulární výraz. Tuto sekvenci operandů můžete zadat několika způsoby:

`ptr` --sekvence zakončená hodnotou null (například řetězec C, pro *Elem* typu **char**) začínající na `ptr` (což nesmí být nulový ukazatel), kde ukončující prvek je hodnota `value_type()` a není součástí sekvence operandů

`ptr`, `count` --sekvence `count` prvky počínaje `ptr` (což nesmí být nulový ukazatel)

`str` --sekvence určená `basic_string` objektu `str`

`first`, `last` --sekvence prvků oddělená iterátory `first` a `last`, v rozsahu `[first, last)`

`right` – `basic_regex` objektu `right`

Tyto členské funkce také přijímají argument `flags` , který určuje různé možnosti pro výklad regulárního výrazu mimo těch popsaných *RXtraits* typu.

### <a name="members"></a>Členové

|Člen|Výchozí hodnota|
|-|-|
|Veřejné statické icase flag_type const|regex_constants::icase|
|Veřejné statické nosubs flag_type const|regex_constants::nosubs|
|Veřejné statické const flag_type optimalizace|regex_constants::optimize|
|COLLATE – veřejné statické flag_type const|regex_constants::collate|
|Veřejné statické const flag_type ECMAScript|regex_constants::ECMAScript|
|Veřejné statické const flag_type základní|regex_constants::basic|
|Veřejné statické const flag_type rozšířené|regex_constants::extended|
|Veřejné statické awk flag_type const|regex_constants::awk|
|Veřejné statické grep flag_type const|regex_constants::grep|
|Veřejné statické egrep flag_type const|regex_constants::egrep|
|privátní RXtraits osobnostní rysy||

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_regex](#basic_regex)|Vytvoření objektu regulárního výrazu.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[flag_type](#flag_type)|Typ syntaxe možnost příznaky.|
|[locale_type](#locale_type)|Typ objektu uloženého národního prostředí.|
|[value_type](#value_type)|Typ elementu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[assign](#assign)|Přiřadí hodnotu k objektu regulárního výrazu.|
|[příznaky](#flags)|Vrátí syntaxe možnost příznaky.|
|[getloc](#getloc)|Vrátí objekt uloženého národního prostředí.|
|[imbue](#imbue)|Změní objekt uloženého národního prostředí.|
|[mark_count](#mark_count)|Vrátí počet dílčích výrazů neodpovídají.|
|[swap](#swap)|Prohodí dva objekty regulárních výrazů.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnotu k objektu regulárního výrazu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regulární výraz >

**Namespace:** std

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

## <a name="assign"></a>  basic_regex::Assign

Přiřadí hodnotu k objektu regulárního výrazu.

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

*STtraits*<br/>
Třída vlastností pro zdrojový řetězec.

*STalloc*<br/>
Třída alokátoru pro zdrojový řetězec.

*Inicializace*<br/>
Typ vstupního iterátoru rozsahu zdroje.

*doprava*<br/>
Regulární výraz zdroje ke zkopírování.

*ptr*<br/>
Ukazatel na začátek pořadí ke kopírování.

*příznaky*<br/>
Syntaxe příznaky možnost přidat při kopírování.

*Len/TD >*<br/>
Délka sekvence ke kopírování.

*str*<br/>
Řetězec zkopírujte.

*první*<br/>
Začátek pořadí ke kopírování.

*last*<br/>
Konec pořadí ke kopírování.

*IList*<br/>
Objekt initializer_list ke kopírování.

### <a name="remarks"></a>Poznámky

Členské funkce jednotlivých nahrazení regulárních výrazů, které drží `*this` s regulárním výrazem popsal sekvenci operandů, pak se vraťte `*this`.

## <a name="basic_regex"></a>  basic_regex::basic_regex

Vytvoření objektu regulárního výrazu.

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

*STtraits*<br/>
Třída vlastností pro zdrojový řetězec.

*STalloc*<br/>
Třída alokátoru pro zdrojový řetězec.

*Inicializace*<br/>
Typ vstupního iterátoru rozsahu zdroje.

*doprava*<br/>
Regulární výraz zdroje ke zkopírování.

*ptr*<br/>
Ukazatel na začátek pořadí ke kopírování.

*příznaky*<br/>
Syntaxe příznaky možnost přidat při kopírování.

*Len/TD >*<br/>
Délka sekvence ke kopírování.

*str*<br/>
Řetězec zkopírujte.

*první*<br/>
Začátek pořadí ke kopírování.

*last*<br/>
Konec pořadí ke kopírování.

*IList*<br/>
Objekt initializer_list ke kopírování.

### <a name="remarks"></a>Poznámky

Všechny konstruktory ukládají objekt vytvořené s výchozím nastavením typu `RXtraits`.

První konstruktor vytvoří prázdnou `basic_regex` objektu. Vytvořit další konstruktory `basic_regex` objekt, který obsahuje regulární výraz popsal sekvenci operandů.

Prázdná `basic_regex` objekt neodpovídá žádné sekvence znaků při předání do [regex_match –](../standard-library/regex-functions.md#regex_match), [regex_search –](../standard-library/regex-functions.md#regex_search), nebo [regex_replace –](../standard-library/regex-functions.md#regex_replace).

## <a name="flag_type"></a>  basic_regex::flag_type

Typ syntaxe možnost příznaky.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="flags"></a>  basic_regex::Flags

Vrátí syntaxe možnost příznaky.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu `flag_type` argument předaný do posledního volání do jednoho z [basic_regex::assign](#assign) členských funkcí nebo pokud nebyla provedena žádná taková volání, hodnota předaná do konstruktoru.

## <a name="getloc"></a>  basic_regex::getloc

Vrátí objekt uloženého národního prostředí.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `traits.` [regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`.

## <a name="imbue"></a>  basic_regex::imbue

Změní objekt uloženého národního prostředí.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

*loc*<br/>
Objekt národního prostředí pro uložení.

### <a name="remarks"></a>Poznámky

Členská funkce vyprázdní `*this` a vrátí `traits.` [regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`.

## <a name="locale_type"></a>  basic_regex::locale_type

Typ objektu uloženého národního prostředí.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="mark_count"></a>  basic_regex::mark_count

Vrátí počet dílčích výrazů neodpovídají.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí počet skupin zachycení v regulárním výrazu.

## <a name="op_eq"></a>  basic_regex::Operator =

Přiřadí hodnotu k objektu regulárního výrazu.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Parametry

*STtraits*<br/>
Třída vlastností pro zdrojový řetězec.

*STalloc*<br/>
Třída alokátoru pro zdrojový řetězec.

*doprava*<br/>
Regulární výraz zdroje ke zkopírování.

*str*<br/>
Řetězec zkopírujte.

### <a name="remarks"></a>Poznámky

Operátory každý nahrazení regulárních výrazů, které drží `*this` s regulárním výrazem popsal sekvenci operandů, pak se vraťte `*this`.

## <a name="swap"></a>  basic_regex::swap

Prohodí dva objekty regulárních výrazů.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Objekt regulárního výrazu se Prohodit s.

### <a name="remarks"></a>Poznámky

Členská funkce Zamění regulární výrazy mezi `*this` a *správné*. Provádí se v konstantním času a vyvolá výjimku žádné výjimky.

## <a name="value_type"></a>  basic_regex::value_type

Typ elementu.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *Elem*.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)<br/>
[regex_match](../standard-library/regex-functions.md#regex_match)<br/>
[regex_search](../standard-library/regex-functions.md#regex_search)<br/>
[regex_replace](../standard-library/regex-functions.md#regex_replace)<br/>
[regex](../standard-library/regex-typedefs.md#regex)<br/>
[wregex](../standard-library/regex-typedefs.md#wregex)<br/>
[regex_traits – třída](../standard-library/regex-traits-class.md)<br/>
