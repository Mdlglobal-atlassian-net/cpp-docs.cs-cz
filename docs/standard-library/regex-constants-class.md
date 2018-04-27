---
title: regex_constants – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 239dbe69d32a5d9a463e33d9d3c1076aa0e79f50
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="regexconstants-class"></a>regex_constants – třída

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

Obor názvů `regex_constants` zapouzdří několik typů příznak a jejich přidružené příznak hodnoty.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex >

**Namespace:** – std

## <a name="error_type"></a>  regex_constants::error_type

Příznaky pro zasílání zpráv o chybách syntaxi regulárního výrazu.

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

Typ je výčtového typu, která popisuje objekt, který můžou obsahovat příznaky chyby. Příznak odlišné hodnoty jsou:

`error_backref` --výraz obsahovala neplatný odkaz na pozadí

`error_badbrace` --výraz obsažené neplatný počet ve výrazu {}

`error_badrepeat` – výraz opakování (jeden z ' *', '', '+', ' {' ve většině případů,) nebyla před sebou výrazu

`error_brace` --výraz obsažené neodpovídajícím ' {' nebo '}'

`error_brack` --výraz obsažené neodpovídajícím ' [' nebo ']'

`error_collate` --výraz obsahovala neplatný název elementu řazení

`error_complexity` --Pokus o shody se nezdařila, protože byl příliš složitý.

`error_ctype` --výraz obsažené název neplatný znak – třída

`error_escape` --výraz obsažené neplatná řídicí sekvence

`error_paren` --výraz obsažené neodpovídajícím '(' nebo').

`error_parse` – výrazu se nezdařila

`error_range` --výraz obsažené specifikátor rozsah neplatný znak

`error_space` --Analýza regulární výraz se nezdařila, protože nebyly dostatek prostředků k dispozici

`error_stack` --Pokus o shody se nezdařila, protože nebyl k dispozici dostatek paměti k dispozici

`error_syntax` --Analýza na chybu syntaxe se nezdařila.

`error_backref` --výraz obsahovala neplatný odkaz na pozadí

## <a name="match_flag_type"></a>  regex_constants::match_flag_type

Příznaky pro regulární výraz odpovídající možnosti.

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

Typ je typ bitová maska, který popisuje možnosti, které se používají při porovnávání text pořadí proti regulární výraz a formát flags má být použit při nahrazování textu. Možnosti mohou být kombinovány s `|`.

Porovnání možnosti jsou:

`match_default`

`match_not_bol` --není považovat za první pozici v pořadí cíl začátek řádku

`match_not_eol` --pozice minulosti the-end v pořadí cíl není považovat za konec řádku

`match_not_bow` --není považovat za první pozici v pořadí cíl začátku slova

`match_not_eow` --není považovat za pozice minulosti the-end v pořadí target konci slova

`match_any` – Pokud více než jednu shodu je možné je přijatelné všechny shody

`match_not_null` --nebude pracovat s prázdnou dalším jako shoda

`match_continuous` --Nevyhledávat odpovídá jinak než na začátek pořadí cíl

`match_prev_avail` -- `--first` je platné iterator; Ignorovat `match_not_bol` a `match_not_bow` -li nastavit

Formát příznaky jsou:

`format_default` – pomocí pravidel ECMAScript formátu

`format_sed` – pomocí pravidel menšit formátu

`format_no_copy` --Nekopírovat text, který se neshoduje s regulárním výrazem

`format_first_only` --Nevyhledávat odpovídá po první

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

Typ je typ bitová maska, který popisuje specifikátory jazyk a syntaxe modifikátory má být použit při kompilování regulární výraz. Možnosti mohou být kombinovány s `|`. Specifikátor více než jeden jazyk je třeba použít současně.

Specifikátory jazyk jsou:

`ECMAScript` --zkompilovat jako ECMAScript

`basic` --zkompilovat jako BRE

`extended` --zkompilovat jako ERE

`awk` --zkompilovat jako awk

`grep` --zkompilovat jako grep

`egrep` --zkompilovat jako egrep

Modifikátory syntaxe je:

`icase` – Zkontrolujte odpovídá velká a malá písmena

`nosubs` – implementaton nemusí udržování přehledu o obsah zachycení skupiny

`optimize` – implementace by měl zdůraznil rychlost odpovídajících spíš než rychlosti kompilace regulárních výrazů

`collate` – Zkontrolujte odpovídá konkrétní národní prostředí

## <a name="see-also"></a>Viz také

[\<regex>](../standard-library/regex.md)<br/>
[regex_error – třída](../standard-library/regex-error-class.md)<br/>
[\<regulární výraz > funkce](../standard-library/regex-functions.md)<br/>
[regex_iterator – třída](../standard-library/regex-iterator-class.md)<br/>
[\<regulární výraz > operátory](../standard-library/regex-operators.md)<br/>
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits – třída](../standard-library/regex-traits-class.md)<br/>
[\<regulární výraz > Definice TypeDef](../standard-library/regex-typedefs.md)<br/>
