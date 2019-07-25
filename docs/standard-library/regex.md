---
title: '&lt;regex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <regex>
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
ms.openlocfilehash: 3e3f3b49b3672042e0376e7738a8cf8924e1c2a8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451451"
---
# <a name="ltregexgt"></a>&lt;regex&gt;

Definuje třídu šablony pro analýzu [regulárních výrazů (C++)](../standard-library/regular-expressions-cpp.md)a několik tříd šablon a funkcí pro hledání shody s objektem regulárního výrazu.

## <a name="syntax"></a>Syntaxe

```cpp
#include <regex>
```

## <a name="remarks"></a>Poznámky

Chcete-li vytvořit objekt regulárního výrazu, použijte třídu Template třídy [basic_regex](../standard-library/basic-regex-class.md) nebo jednu z jejích specializací, [Regex](../standard-library/regex-typedefs.md#regex) a [wregex –](../standard-library/regex-typedefs.md#wregex)spolu s příznaky syntaxe typu [regex_constants:: syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

Chcete-li vyhledat text shody s objektem regulárního výrazu, použijte šablony Functions [regex_match](../standard-library/regex-functions.md#regex_match) a [regex_search](../standard-library/regex-functions.md#regex_search)spolu s příznaky shody typu [regex_constants:: match_flag_type](../standard-library/regex-constants-class.md#match_flag_type). Tyto funkce vrátí výsledky pomocí [třídy Template match_results](../standard-library/match-results-class.md) a jejích specializace, [cmatch –](../standard-library/regex-typedefs.md#cmatch), [wcmatch –](../standard-library/regex-typedefs.md#wcmatch), [Smatch –](../standard-library/regex-typedefs.md#smatch)a [wsmatch –](../standard-library/regex-typedefs.md#wsmatch), společně s třídou Template třídy [sub_match](../standard-library/sub-match-class.md) a jejím specializace, [csub_match](../standard-library/regex-typedefs.md#csub_match), [wcsub_match](../standard-library/regex-typedefs.md#wcsub_match), [ssub_match](../standard-library/regex-typedefs.md#ssub_match)a [wssub_match](../standard-library/regex-typedefs.md#wssub_match).

Chcete-li nahradit text, který odpovídá objektu regulárního výrazu, použijte funkci šablony [regex_replace](../standard-library/regex-functions.md#regex_replace)spolu s příznaky shody typu [regex_constants:: match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).

Chcete-li iterovat více shod objektu regulárního výrazu, použijte třídy šablon třídy [regex_iterator](../standard-library/regex-iterator-class.md) a [třídu regex_token_iterator](../standard-library/regex-token-iterator-class.md) nebo jednu z jejich specializace, [cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator), [sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator), [wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator), [wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator), [cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator), [sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator), [wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)nebo [wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator), spolu s příznaky shody typu [regex_ konstanty:: match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).

Chcete-li upravit podrobnosti gramatiky regulárních výrazů, napište třídu, která implementuje vlastnosti regulárního výrazu.

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_regex](../standard-library/basic-regex-class.md)|Zabalí regulární výraz.|
|[match_results](../standard-library/match-results-class.md)|Obsahuje posloupnost dílčích shod.|
|[regex_constants](../standard-library/regex-constants-class.md)|Obsahuje roztříděné konstanty.|
|[regex_error](../standard-library/regex-error-class.md)|Oznamuje chybný regulární výraz.|
|[regex_iterator](../standard-library/regex-iterator-class.md)|Iterace prostřednictvím výsledků hledání shody.|
|[regex_traits](../standard-library/regex-traits-class.md)|Popisuje charakteristiky prvků pro porovnání.|
|[regex_traits\<char>](../standard-library/regex-traits-char-class.md)|Popisuje charakteristiky **znaku** pro porovnání.|
|[regex_traits<wchar_t>](../standard-library/regex-traits-wchar-t-class.md)|Popisuje charakteristiky **wchar_t** pro porovnání.|
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|Provede iteraci pomocí podshod.|
|[sub_match](../standard-library/sub-match-class.md)|Popisuje podshodu.|

### <a name="type-definitions"></a>Definice typů

|||
|-|-|
|[cmatch](../standard-library/regex-typedefs.md#cmatch)|Zadejte definici typu **char** `match_results`.|
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)|Zadejte definici typu **char** `regex_iterator`.|
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)|Zadejte definici typu **char** `regex_token_iterator`.|
|[csub_match](../standard-library/regex-typedefs.md#csub_match)|Zadejte definici typu **char** `sub_match`.|
|[regex](../standard-library/regex-typedefs.md#regex)|Zadejte definici typu **char** `basic_regex`.|
|[Smatch –](../standard-library/regex-typedefs.md#smatch)|Zadejte definici pro `string`. `match_results`|
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)|Zadejte definici pro `string`. `regex_iterator`|
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)|Zadejte definici pro `string`. `regex_token_iterator`|
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match)|Zadejte definici pro `string`. `sub_match`|
|[wcmatch](../standard-library/regex-typedefs.md#wcmatch)|Zadejte definici pro **wchar_t** `match_results`.|
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)|Zadejte definici pro **wchar_t** `regex_iterator`.|
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)|Zadejte definici pro **wchar_t** `regex_token_iterator`.|
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)|Zadejte definici pro **wchar_t** `sub_match`.|
|[wregex](../standard-library/regex-typedefs.md#wregex)|Zadejte definici pro **wchar_t** `basic_regex`.|
|[wsmatch](../standard-library/regex-typedefs.md#wsmatch)|Zadejte definici pro `wstring`. `match_results`|
|[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator)|Zadejte definici pro `wstring`. `regex_iterator`|
|[wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator)|Zadejte definici pro `wstring`. `regex_token_iterator`|
|[wssub_match](../standard-library/regex-typedefs.md#wssub_match)|Zadejte definici pro `wstring`. `sub_match`|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[regex_match](../standard-library/regex-functions.md#regex_match)|Přesně odpovídá regulárnímu výrazu.|
|[regex_replace](../standard-library/regex-functions.md#regex_replace)|Nahradí párové regulární výrazy.|
|[regex_search](../standard-library/regex-functions.md#regex_search)|Vyhledá shodu regulárního výrazu.|
|[swap](../standard-library/regex-functions.md#swap)|Prohodí objekty `match_results`nebo. `basic_regex`|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator==](../standard-library/regex-operators.md#op_eq_eq)|Porovnání různých objektů, stejné.|
|[operator!=](../standard-library/regex-operators.md#op_neq)|Porovnání různých objektů, není rovno.|
|[operátor <](../standard-library/regex-operators.md#op_lt)|Porovnání různých objektů, které jsou menší než.|
|[podnikatel\<=](../standard-library/regex-operators.md#op_gt_eq)|Porovnání různých objektů je menší nebo rovno.|
|[operátor >](../standard-library/regex-operators.md#op_gt)|Porovnání různých objektů, které jsou větší než.|
|[operator>=](../standard-library/regex-operators.md#op_gt_eq)|Porovnání různých objektů, které jsou větší nebo rovny.|
|[operátor < <](../standard-library/regex-operators.md#op_lt_lt)|`sub_match` Vloží do datového proudu.|

## <a name="see-also"></a>Viz také:

[Regulární výrazy (C++)](../standard-library/regular-expressions-cpp.md)\
[regex_constants – třída](../standard-library/regex-constants-class.md)\
[regex_error – třída](../standard-library/regex-error-class.md)\
[\<regulární funkce >](../standard-library/regex-functions.md)\
[regex_iterator – třída](../standard-library/regex-iterator-class.md)\
[\<operátory > Regex](../standard-library/regex-operators.md)\
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)\
[regex_traits – třída](../standard-library/regex-traits-class.md)\
[\<Regex > definice typedef](../standard-library/regex-typedefs.md)
