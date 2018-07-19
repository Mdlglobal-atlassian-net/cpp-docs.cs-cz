---
title: '&lt;regulární výraz&gt; | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <regex>
dev_langs:
- C++
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ff0fffeffd10f382f4d0d4fe6361c2eddac55e3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963128"
---
# <a name="ltregexgt"></a>&lt;regex&gt;

Definuje třídu šablony analyzovat [regulární výrazy (C++)](../standard-library/regular-expressions-cpp.md)a několik šablon třídy a funkce pro hledání shody regulárního výrazu objektu text.

## <a name="syntax"></a>Syntaxe

```cpp
#include <regex>
```

## <a name="remarks"></a>Poznámky

Chcete-li vytvořit objekt regulárního výrazu, použijte šablony třídy [basic_regex – třída](../standard-library/basic-regex-class.md) nebo jeden z jeho specializace [regulární výraz](../standard-library/regex-typedefs.md#regex) a [wregex](../standard-library/regex-typedefs.md#wregex)společně s příznaky syntaxe typ [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

K vyhledání textu shody na objekt regulárního výrazu, pomocí funkce šablony [regex_match –](../standard-library/regex-functions.md#regex_match) a [regex_search –](../standard-library/regex-functions.md#regex_search)společně s příznaky shoda typu [regex_constants::match_ flag_type](../standard-library/regex-constants-class.md#match_flag_type). Tyto funkce vrátí výsledky pomocí šablony třídy [match_results – třída](../standard-library/match-results-class.md) a jeho specializace [cmatch](../standard-library/regex-typedefs.md#cmatch), [wcmatch](../standard-library/regex-typedefs.md#wcmatch), [smatch](../standard-library/regex-typedefs.md#smatch), a [wsmatch](../standard-library/regex-typedefs.md#wsmatch)společně s šablony třídy [sub_match – třída](../standard-library/sub-match-class.md) a jeho specializace [csub_match](../standard-library/regex-typedefs.md#csub_match), [wcsub_ odpovídá](../standard-library/regex-typedefs.md#wcsub_match), [ssub_match](../standard-library/regex-typedefs.md#ssub_match), a [wssub_match](../standard-library/regex-typedefs.md#wssub_match).

Nahradit text, který odpovídá objektu regulárního výrazu, použijte funkci šablony [regex_replace –](../standard-library/regex-functions.md#regex_replace)společně s příznaky shoda typu [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).

K iteraci v rámci více shod, regulární výraz objektu, použijte šablony třídy [regex_iterator – třída](../standard-library/regex-iterator-class.md) a [regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md) nebo jeden z jejich specializace [ cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator), [sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator), [wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator), [wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator), [cregex_token_iterator ](../standard-library/regex-typedefs.md#cregex_token_iterator), [sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator), [wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator), nebo [wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator)společně s příznaky shoda typu [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).

Pokud chcete upravit podrobnosti gramatika regulárních výrazů, zápis třídu, která implementuje vlastnosti regulárního výrazu.

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_regex](../standard-library/basic-regex-class.md)|Zabalí regulární výraz.|
|[match_results](../standard-library/match-results-class.md)|Obsahuje posloupnost dílčí shody.|
|[regex_constants –](../standard-library/regex-constants-class.md)|Obsahuje různé konstanty.|
|[regex_error](../standard-library/regex-error-class.md)|Sestavy chybný regulární výraz.|
|[regex_iterator](../standard-library/regex-iterator-class.md)|Iteruje přes výsledky porovnání.|
|[regex_traits –](../standard-library/regex-traits-class.md)|Popisuje charakteristiky elementů pro porovnání.|
|[regex_traits\<char>](../standard-library/regex-traits-char-class.md)|Popisuje charakteristiky **char** pro porovnání.|
|[regex_traits < wchar_t >](../standard-library/regex-traits-wchar-t-class.md)|Popisuje charakteristiky **wchar_t** pro porovnání.|
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|Iteruje přes dílčí shody.|
|[sub_match](../standard-library/sub-match-class.md)|Popisuje dílčí shoda.|

### <a name="type-definitions"></a>Definice typu

|||
|-|-|
|[cmatch](../standard-library/regex-typedefs.md#cmatch)|Zadejte definici **char** `match_results`.|
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)|Zadejte definici **char** `regex_iterator`.|
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)|Zadejte definici **char** `regex_token_iterator`.|
|[csub_match](../standard-library/regex-typedefs.md#csub_match)|Zadejte definici **char** `sub_match`.|
|[regex](../standard-library/regex-typedefs.md#regex)|Zadejte definici **char** `basic_regex`.|
|[smatch](../standard-library/regex-typedefs.md#smatch)|Zadejte definici `string` `match_results`.|
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)|Zadejte definici `string` `regex_iterator`.|
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)|Zadejte definici `string` `regex_token_iterator`.|
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match)|Zadejte definici `string` `sub_match`.|
|[wcmatch](../standard-library/regex-typedefs.md#wcmatch)|Zadejte definici **wchar_t** `match_results`.|
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)|Zadejte definici **wchar_t** `regex_iterator`.|
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)|Zadejte definici **wchar_t** `regex_token_iterator`.|
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)|Zadejte definici **wchar_t** `sub_match`.|
|[wregex](../standard-library/regex-typedefs.md#wregex)|Zadejte definici **wchar_t** `basic_regex`.|
|[wsmatch](../standard-library/regex-typedefs.md#wsmatch)|Zadejte definici `wstring` `match_results`.|
|[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator)|Zadejte definici `wstring` `regex_iterator`.|
|[wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator)|Zadejte definici `wstring` `regex_token_iterator`.|
|[wssub_match](../standard-library/regex-typedefs.md#wssub_match)|Zadejte definici `wstring` `sub_match`.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[regex_match](../standard-library/regex-functions.md#regex_match)|Přesně shoduje s regulárním výrazem.|
|[regex_replace](../standard-library/regex-functions.md#regex_replace)|Nahradí odpovídající regulární výrazy.|
|[regex_search](../standard-library/regex-functions.md#regex_search)|Hledání regulárního výrazu shody.|
|[Prohození](../standard-library/regex-functions.md#swap)|Zamění `basic_regex` nebo `match_results` objekty.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator==](../standard-library/regex-operators.md#op_eq_eq)|Porovnání různých objektů, které jsou stejné.|
|[operator!=](../standard-library/regex-operators.md#op_neq)|Porovnání různých objektů, není rovno.|
|[Operator <](../standard-library/regex-operators.md#op_lt)|Porovnání různých objektů, menší než.|
|[– Operátor\<=](../standard-library/regex-operators.md#op_gt_eq)|Porovnání různých objektů, menší než nebo rovno.|
|[Operator >](../standard-library/regex-operators.md#op_gt)|Porovnání různých objektů, které jsou větší než.|
|[operator>=](../standard-library/regex-operators.md#op_gt_eq)|Porovnání různých objektů, větší než nebo rovno.|
|[operátor <<](../standard-library/regex-operators.md#op_lt_lt)|Vloží `sub_match` v datovém proudu.|

## <a name="see-also"></a>Viz také:

[Regulární výrazy (C++)](../standard-library/regular-expressions-cpp.md)<br/>
[regex_constants – třída](../standard-library/regex-constants-class.md)<br/>
[regex_error – třída](../standard-library/regex-error-class.md)<br/>
[\<regulární výraz > funkce](../standard-library/regex-functions.md)<br/>
[regex_iterator – třída](../standard-library/regex-iterator-class.md)<br/>
[\<regulární výraz > operátory](../standard-library/regex-operators.md)<br/>
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits – třída](../standard-library/regex-traits-class.md)<br/>
[\<regulární výraz > – Definice TypeDef](../standard-library/regex-typedefs.md)<br/>
