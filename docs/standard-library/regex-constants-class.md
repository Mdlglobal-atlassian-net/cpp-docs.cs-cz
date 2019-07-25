---
title: regex_constants – třída
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_constants
- regex/std::regex_constants::error_collate
- regex/std::regex_constants::error_ctype
- regex/std::regex_constants::error_escape
- regex/std::regex_constants::error_backref
- regex/std::regex_constants::error_brack
- regex/std::regex_constants::error_paren
- regex/std::regex_constants::error_brace
- regex/std::regex_constants::error_badbrace
- regex/std::regex_constants::error_range
- regex/std::regex_constants::error_space
- regex/std::regex_constants::error_badrepeat
- regex/std::regex_constants::error_complexity
- regex/std::regex_constants::error_stack
- regex/std::regex_constants::error_parse
- regex/std::regex_constants::error_syntax
- regex/std::regex_constants::match_default
- regex/std::regex_constants::match_not_bol
- regex/std::regex_constants::match_not_eol
- regex/std::regex_constants::match_not_bow
- regex/std::regex_constants::match_not_eow
- regex/std::regex_constants::match_any
- regex/std::regex_constants::match_not_null
- regex/std::regex_constants::match_continuous
- regex/std::regex_constants::match_prev_avail
- regex/std::regex_constants::format_default
- regex/std::regex_constants::format_sed
- regex/std::regex_constants::format_no_copy
- regex/std::regex_constants::format_first_only
- regex/std::regex_constants::ECMAScript
- regex/std::regex_constants::basic
- regex/std::regex_constants::extended
- regex/std::regex_constants::awk
- regex/std::regex_constants::grep
- regex/std::regex_constants::egrep
- regex/std::regex_constants::icase
- regex/std::regex_constants::nosubs
- regex/std::regex_constants::optimize
- regex/std::regex_constants::collate
helpviewer_keywords:
- std::regex_constants [C++]
- std::regex_constants [C++], error_collate
- std::regex_constants [C++], error_ctype
- std::regex_constants [C++], error_escape
- std::regex_constants [C++], error_backref
- std::regex_constants [C++], error_brack
- std::regex_constants [C++], error_paren
- std::regex_constants [C++], error_brace
- std::regex_constants [C++], error_badbrace
- std::regex_constants [C++], error_range
- std::regex_constants [C++], error_space
- std::regex_constants [C++], error_badrepeat
- std::regex_constants [C++], error_complexity
- std::regex_constants [C++], error_stack
- std::regex_constants [C++], error_parse
- std::regex_constants [C++], error_syntax
- std::regex_constants [C++], match_default
- std::regex_constants [C++], match_not_bol
- std::regex_constants [C++], match_not_eol
- std::regex_constants [C++], match_not_bow
- std::regex_constants [C++], match_not_eow
- std::regex_constants [C++], match_any
- std::regex_constants [C++], match_not_null
- std::regex_constants [C++], match_continuous
- std::regex_constants [C++], match_prev_avail
- std::regex_constants [C++], format_default
- std::regex_constants [C++], format_sed
- std::regex_constants [C++], format_no_copy
- std::regex_constants [C++], format_first_only
- std::regex_constants [C++], ECMAScript
- std::regex_constants [C++], basic
- std::regex_constants [C++], extended
- std::regex_constants [C++], awk
- std::regex_constants [C++], grep
- std::regex_constants [C++], egrep
- std::regex_constants [C++], icase
- std::regex_constants [C++], nosubs
- std::regex_constants [C++], optimize
- std::regex_constants [C++], collate
ms.assetid: 4a69c0ba-c46d-46e4-bd29-6f4efb805f26
ms.openlocfilehash: c8abca8109db9c781d63721b795feb01161fdb40
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451667"
---
# <a name="regexconstants-namespace"></a>regex_constants namespace

Obor názvů pro příznaky regulárního výrazu

## <a name="syntax"></a>Syntaxe

```cpp
namespace regex_constants {
    enum syntax_option_type;
    enum match_flag_type;
    enum error_type;
}
```

## <a name="remarks"></a>Poznámky

Obor názvů `regex_constants` zapouzdřuje několik typů příznaků a jejich přidružených hodnot příznaku.

|||
|-|-|
|[error_type](#error_type)|Příznaky pro vytváření sestav chyb syntaxe regulárních výrazů.|
|[match_flag_type](#match_flag_type)|Příznaky pro možnosti odpovídajícího regulárního výrazu.|
|[syntax_option_type](#syntax_option_type)|Příznaky pro výběr možností syntaxe|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> regulárního výrazu

**Obor názvů:** std

## <a name="error_type"></a>  regex_constants::error_type

Příznaky pro vytváření sestav chyb syntaxe regulárních výrazů.

```cpp
enum error_type
    {    // identify error
    error_collate,
    error_ctype,
    error_escape,
    error_backref,
    error_brack,
    error_paren,
    error_brace,
    error_badbrace,
    error_range,
    error_space,
    error_badrepeat,
    error_complexity,
    error_stack,
    error_parse,
    error_syntax
    };
```

### <a name="remarks"></a>Poznámky

Typ je výčtový typ, který popisuje objekt, který může obsahovat příznaky chyby. Jednotlivé hodnoty příznaku jsou:

`error_backref`--výraz obsahoval neplatný odkaz zpět.

`error_badbrace`--výraz obsahoval neplatný počet ve výrazu {}.

`error_badrepeat`--výraz opakování (jedna z těchto ' * ', ' ', ' + ', ' {' v největším kontextu) nebyl před výrazem.

`error_brace`--výraz obsahoval nespárované "{" nebo "}"

`error_brack`--výraz obsahoval nespárované závorky [nebo].

`error_collate`--výraz obsahoval neplatný název řadicího elementu.

`error_complexity`--shoda se nezdařila, protože byla příliš složitá.

`error_ctype`--výraz obsahoval neplatný název třídy znaků.

`error_escape`--výraz obsahoval neplatnou řídicí sekvenci.

`error_paren`--výraz obsahoval nespárovaný znak (nebo).

`error_parse`--výraz se nepovedlo analyzovat.

`error_range`--výraz obsahoval Neplatný specifikátor rozsahu znaků.

`error_space`--Analýza regulárního výrazu se nezdařila, protože k dispozici není dostatek prostředků.

`error_stack`--shoda se nezdařila, protože k dispozici není dostatek paměti.

`error_syntax`--při analýze došlo k chybě syntaxe.

`error_backref`--výraz obsahoval neplatný odkaz zpět.

## <a name="match_flag_type"></a>  regex_constants::match_flag_type

Příznaky pro možnosti odpovídajícího regulárního výrazu.

```cpp
enum match_flag_type
    {    // specify matching and formatting rules
    match_default = 0x0000,
    match_not_bol = 0x0001,
    match_not_eol = 0x0002,
    match_not_bow = 0x0004,
    match_not_eow = 0x0008,
    match_any = 0x0010,
    match_not_null = 0x0020,
    match_continuous = 0x0040,
    match_prev_avail = 0x0100,
    format_default = 0x0000,
    format_sed = 0x0400,
    format_no_copy = 0x0800,
    format_first_only = 0x1000,
    _Match_not_null = 0x2000
    };
```

### <a name="remarks"></a>Poznámky

Typ je typ maskování, který popisuje možnosti, které se mají použít při porovnání textových sekvencí s regulárním výrazem a příznaky formátu, které se mají použít při nahrazování textu. Možnosti lze kombinovat s `|`.

Možnosti shody jsou:

`match_default`

`match_not_bol`--nepovažuje první pozici v cílové sekvenci za začátek řádku.

`match_not_eol`--nepovažuje za konec řádku pozici za poslední a koncovou pozicí v cílové sekvenci.

`match_not_bow`– nepovažujte první pozici v cílové sekvenci za začátek slova.

`match_not_eow`--nepovažuje za konec slova pozici za poslední a koncovou pozicí v cílové sekvenci.

`match_any`--Pokud je možné, že je k dispozici více než jedna shoda, je přijatelná shoda.

`match_not_null`nepovažujte za shodu prázdnou dílčí sekvenci.

`match_continuous`--Nevyhledávat shody jiné než na začátku cílové sekvence

`match_prev_avail` -- `--first`je platný iterátor; ignorovat `match_not_bol` a`match_not_bow` v případě nastavení

Příznaky formátu jsou:

`format_default`--použít pravidla formátu ECMAScript

`format_sed`--použít pravidla formátu SED

`format_no_copy`nekopíruje text, který se neshoduje s regulárním výrazem.

`format_first_only`--Nevyhledávat shody za první z nich

## <a name="syntax_option_type"></a>  regex_constants::syntax_option_type

Příznaky pro výběr možností syntaxe

```cpp
enum syntax_option_type
    {    // specify RE syntax rules
    ECMAScript = 0x01,
    basic = 0x02,
    extended = 0x04,
    awk = 0x08,
    grep = 0x10,
    egrep = 0x20,
    _Gmask = 0x3F,

    icase = 0x0100,
    nosubs = 0x0200,
    optimize = 0x0400,
    collate = 0x0800
    };
```

### <a name="remarks"></a>Poznámky

Typ je typ maskování, který popisuje specifikátory jazyka a modifikátory syntaxe, které mají být použity při kompilování regulárního výrazu. Možnosti lze kombinovat s `|`. V jednom okamžiku by neměl být použit více než jeden specifikátor jazyka.

Specifikátory jazyka jsou:

`ECMAScript`--kompilovat jako ECMAScript

`basic`--kompilovat jako BRE

`extended`--kompilovat jako ERE

`awk`--kompilovat jako awk mají

`grep`--kompilovat jako grep

`egrep`--kompilovat jako egrep

Modifikátory syntaxe jsou:

`icase`– Zajistěte, aby odpovídaly malá a velká písmena.

`nosubs`--implementaton nemusí sledovat obsah skupin zachycení.

`optimize`--Implementace by měla zdůraznit rychlost porovnání namísto rychlosti kompilace regulárního výrazu.

`collate`--Udělejte shodu s národním prostředím.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)\
[regex_error – třída](../standard-library/regex-error-class.md)\
[\<regulární funkce >](../standard-library/regex-functions.md)\
[regex_iterator – třída](../standard-library/regex-iterator-class.md)\
[\<operátory > Regex](../standard-library/regex-operators.md)\
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)\
[regex_traits – třída](../standard-library/regex-traits-class.md)\
[\<Regex > definice typedef](../standard-library/regex-typedefs.md)
