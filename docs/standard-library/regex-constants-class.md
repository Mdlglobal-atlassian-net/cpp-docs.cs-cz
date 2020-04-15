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
ms.openlocfilehash: ee016e5cee1bde94a49a1b339d6910d60db4cea1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331952"
---
# <a name="regex_constants-namespace"></a>regex_constants – obor názvů

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

Obor `regex_constants` názvů zapouzdřuje několik typů příznaku a jejich přidružené hodnoty příznaku.

|||
|-|-|
|[error_type](#error_type)|Příznaky pro hlášení chyb syntaxe regulárních výrazů.|
|[match_flag_type](#match_flag_type)|Příznaky pro možnosti porovnávání regulárních výrazů.|
|[syntax_option_type](#syntax_option_type)|Příznaky pro výběr možností syntaxe.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex>

**Obor názvů:** std

## <a name="regex_constantserror_type"></a><a name="error_type"></a>regex_constants::error_type

Příznaky pro hlášení chyb syntaxe regulárních výrazů.

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

Typ je výčtový typ, který popisuje objekt, který může obsahovat příznaky chyb. Odlišné hodnoty příznaku jsou:

`error_backref`-- výraz obsahoval neplatný zpětný odkaz

`error_badbrace`-- výraz obsahoval neplatný počet ve výrazu { }

`error_badrepeat`-- výraz opakování (jeden z '*', '', '+', '{' ve většině kontextů) nebyl ve většině kontextů předchází výraz

`error_brace`-- výraz obsahoval neporovnaný {nebo '}'

`error_brack`-- výraz obsahoval neporovnané "[' nebo "]"

`error_collate`-- výraz obsahoval neplatný název kompletačního prvku

`error_complexity`-- pokus o shodu se nezdařil, protože byl příliš složitý.

`error_ctype`-- výraz obsahoval neplatný název třídy znaků

`error_escape`-- výraz obsahoval neplatnou řídicí sekvenci.

`error_paren`-- výraz obsahoval neporovnané '(' nebo ')'

`error_parse`-- výraz se nepodařilo analyzovat

`error_range`-- výraz obsahoval neplatný specifikátor rozsahu znaků

`error_space`-- analýza regulárního výrazu se nezdařila, protože nebylo k dispozici dostatek zdrojů.

`error_stack`-- pokus o shodu se nezdařil, protože nebylo k dispozici dostatek paměti.

`error_syntax`-- analýza se nezdařila při chybě syntaxe.

`error_backref`-- výraz obsahoval neplatný zpětný odkaz

## <a name="regex_constantsmatch_flag_type"></a><a name="match_flag_type"></a>regex_constants::match_flag_type

Příznaky pro možnosti porovnávání regulárních výrazů.

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

Typ je typ bitové masky, který popisuje možnosti, které mají být použity při porovnávání textové sekvence s regulárním výrazem a příznaky formátu, které mají být použity při nahrazování textu. Možnosti lze kombinovat `|`s .

Možnosti shody jsou:

`match_default`

`match_not_bol`-- nezacházejte s první pozicí v cílové sekvenci jako s začátkem řádku

`match_not_eol`-- nezacházejte s pozicí minulosti v cílové sekvenci jako s koncem řádku

`match_not_bow`-- nezacházejte s první pozicí v cílové sekvenci jako s začátkem slova

`match_not_eow`-- nezacházejte s pozicí minulosti v cílové sekvenci jako s koncem slova

`match_any`-- pokud je možné více než jednu shodu, je jakákoli shoda přijatelná

`match_not_null`-- nezacházejte s prázdnou dílčí sekvenci jako se shodou

`match_continuous`-- nevyhledávejte jiné shody než na začátku cílové sekvence

`match_prev_avail` -- `--first`je platným iterátorem; ignorovat `match_not_bol` `match_not_bow` a pokud je nastaveno

Příznaky formátu jsou:

`format_default`-- použití pravidel formátu ECMAScript

`format_sed`-- použití pravidel formátu sed

`format_no_copy`-- nekopírujte text, který neodpovídá regulárnímu výrazu

`format_first_only`-- nevyhledávejte shody po prvním

## <a name="regex_constantssyntax_option_type"></a><a name="syntax_option_type"></a>regex_constants::syntax_option_type

Příznaky pro výběr možností syntaxe.

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

Typ je typ bitové masky, který popisuje specifikátory jazyka a modifikátory syntaxe, které mají být použity při kompilaci regulárního výrazu. Možnosti lze kombinovat `|`s . Současně by měl být použit maximálně jeden specifikátor jazyka.

Specifikátory jazyka jsou:

`ECMAScript`-- kompilace jako ECMAScript

`basic`-- kompilovat jako BRE

`extended`-- kompilovat jako ERE

`awk`-- kompilovat jako awk

`grep`-- kompilovat jako grep

`egrep`-- kompilovat jako egrep

Syntaxe modifikátory jsou:

`icase`-- aby shody nerozlišují malá a velká písmena

`nosubs`-- implementaton nemusí sledovat obsah zachytávacích skupin

`optimize`-- implementace by měla zdůraznit rychlost párování spíše než rychlost kompilace regulárních výrazů

`collate`-- provést shody citlivé na národní prostředí

## <a name="see-also"></a>Viz také

[\<regulární>](../standard-library/regex.md)\
[regex_error třída](../standard-library/regex-error-class.md)\
[\<funkce> regulárních výrazů](../standard-library/regex-functions.md)\
[regex_iterator třída](../standard-library/regex-iterator-class.md)\
[\<operátory> regulárních výrazů](../standard-library/regex-operators.md)\
[regex_token_iterator třída](../standard-library/regex-token-iterator-class.md)\
[třída regex_traits](../standard-library/regex-traits-class.md)\
[\<regulární> typedefs](../standard-library/regex-typedefs.md)
