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
ms.openlocfilehash: f3e733bced407f96414783612165984c71b63775
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369563"
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

Obor názvů `regex_constants` zapouzdřuje několik typů příznaků a jejich přidružené hodnoty.

|||
|-|-|
|[error_type](#error_type)|Příznaky pro hlášení chyb syntaxe regulárního výrazu.|
|[match_flag_type](#match_flag_type)|Příznaky pro porovnávání možnosti regulárních výrazů.|
|[syntax_option_type](#syntax_option_type)|Příznaky pro výběr možnosti syntaxe.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regulární výraz >

**Namespace:** std

## <a name="error_type"></a>  regex_constants::error_type

Příznaky pro hlášení chyb syntaxe regulárního výrazu.

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

Typ je výčtového typu, který popisuje objekt, který může obsahovat chyby příznaky. Příznak odlišné hodnoty jsou:

`error_backref` --výraz obsahovala neplatný zpětný odkaz

`error_badbrace` – výraz obsahuje neplatný počet ve výrazu {}

`error_badrepeat` --výrazu opakování (jednu z "*", ", '+', ' {" ve většině případů) nebyla před výrazem

`error_brace` --obsažené žádným výraz ' {"nebo"} "

`error_brack` – výraz obsažené žádným ' [' nebo ']'

`error_collate` – výraz obsahuje neplatný název kolační prvek

`error_complexity` --Pokus o shodu se nezdařila, protože byl příliš složitý.

`error_ctype` --výraz obsažené názvu neplatný znak třídy

`error_escape` --výraz obsahovala neplatnou řídicí sekvenci

`error_paren` --výraz obsažené žádným '(' nebo')'

`error_parse` – Analýza výrazu se nezdařila

`error_range` --výraz obsažených specifikátor rozsahu je neplatný znak

`error_space` --parsování regulárního výrazu se nezdařila, protože nebyl dostatek prostředků k dispozici

`error_stack` --Pokus o shodu se nezdařila, protože nebyl k dispozici dostatek paměti k dispozici

`error_syntax` --nepovedlo se parsovat Chyba syntaxe

`error_backref` --výraz obsahovala neplatný zpětný odkaz

## <a name="match_flag_type"></a>  regex_constants::match_flag_type

Příznaky pro porovnávání možnosti regulárních výrazů.

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

Typ je typ bitová maska, která popisuje možnosti, jak se dá použít při porovnávání posloupnost textu regulárního výrazu a formát příznaky, které se dá použít při nahrazování textu. Možnosti lze kombinovat s `|`.

Možnosti porovnání jsou následující:

*match_default*<br/>

`match_not_bol` --nelze považovat za první pozice v cílové sekvenci na začátek řádku

`match_not_eol` --není považovat za posledních koncem pozice v cílové sekvenci konce řádku

`match_not_bow` --nelze považovat za první pozice v cílové sekvenci začátku slova

`match_not_eow` --nelze považovat za posledních koncem pozice v cílové sekvenci konci slova

`match_any` --Pokud více než jedna shoda je možné je přijatelné vyhledání jakékoli shody

`match_not_null` --nelze považovat za prázdný dílčí sekvenci odpovídající

`match_continuous` --Nevyhledávat odpovídá jiné než na začátku cílové sekvence

`match_prev_avail` -- `--first` je platný iterátor; Ignorovat `match_not_bol` a `match_not_bow` -li nastavit

Příznaky formátu jsou:

`format_default` – Použijte pravidla formátu ECMAScript

`format_sed` – Použijte pravidla formátu sed

`format_no_copy` --Nekopírovat text, který se neshoduje s regulárním výrazem

`format_first_only` --Nevyhledávat shody po první z nich

## <a name="syntax_option_type"></a>  regex_constants::syntax_option_type

Příznaky pro výběr možnosti syntaxe.

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

Typ je typ bitová maska, která popisuje specifikátory jazyka a modifikátory syntaxe se dá použít při kompilování regulárního výrazu. Možnosti lze kombinovat s `|`. Současně by měl použít specifikátor více než jeden jazyk.

Specifikátory jazyka jsou:

`ECMAScript` --zkompiluje kód jako ECMAScript

`basic` --zkompiluje kód jako BRE

`extended` --zkompiluje kód jako ERE

`awk` --zkompiluje kód jako awk

`grep` --zkompiluje kód jako grep

`egrep` --zkompiluje kód jako egrep

Modifikátory syntaxe jsou:

`icase` – Ujistěte se, odpovídá velká a malá písmena

`nosubs` – implementaton nemusí udržovat přehled o obsah skupin zachycení

`optimize` --implementace, měli byste zdůraznit rychlost porovnávání spíše než rychlost regulárního výrazu

`collate` – Zkontrolujte odpovídá citlivé na národní prostředí

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)<br/>
[regex_error – třída](../standard-library/regex-error-class.md)<br/>
[\<regulární výraz > funkce](../standard-library/regex-functions.md)<br/>
[regex_iterator – třída](../standard-library/regex-iterator-class.md)<br/>
[\<regulární výraz > operátory](../standard-library/regex-operators.md)<br/>
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits – třída](../standard-library/regex-traits-class.md)<br/>
[\<regulární výraz > – Definice TypeDef](../standard-library/regex-typedefs.md)<br/>
