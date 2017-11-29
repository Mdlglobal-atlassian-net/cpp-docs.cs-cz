---
title: "&lt;regulární výraz&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <regex>
dev_langs: C++
helpviewer_keywords: regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 50aaf3f695b023d6316fdd5d601962435903e15c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltregexgt"></a>&lt;regulární výraz&gt;
Definuje třídu šablony analyzovat [regulární výrazy (C++)](../standard-library/regular-expressions-cpp.md)a několik šablony třídy a funkce pro vyhledání text odpovídá na objekt regulárního výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <regex>  
```  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit objekt regulárního výrazu, použijte třídu šablony [basic_regex – třída](../standard-library/basic-regex-class.md) nebo jednoho z jeho specializací [regex](../standard-library/regex-typedefs.md#regex) a [wregex –](../standard-library/regex-typedefs.md#wregex), společně s příznaky syntaxe typ [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).  
  
 Hledat text odpovídá na objekt regulárního výrazu, použijte šablonu funkce [regex_match –](../standard-library/regex-functions.md#regex_match) a [regex_search –](../standard-library/regex-functions.md#regex_search), společně s příznaky shoda typu [regex_constants::match_ flag_type –](../standard-library/regex-constants-class.md#match_flag_type). Tyto funkce vrátí výsledky pomocí šablony třídy [match_results – třída](../standard-library/match-results-class.md) a jeho specializací [cmatch –](../standard-library/regex-typedefs.md#cmatch), [wcmatch –](../standard-library/regex-typedefs.md#wcmatch), [smatch –](../standard-library/regex-typedefs.md#smatch), a [wsmatch –](../standard-library/regex-typedefs.md#wsmatch), společně s třídou šablony [sub_match – třída](../standard-library/sub-match-class.md) a jeho specializací [csub_match –](../standard-library/regex-typedefs.md#csub_match), [wcsub_ odpovídat](../standard-library/regex-typedefs.md#wcsub_match), [ssub_match –](../standard-library/regex-typedefs.md#ssub_match), a [wssub_match –](../standard-library/regex-typedefs.md#wssub_match).  
  
 Pokud chcete nahradit text, který odpovídá objekt regulárního výrazu, použijte funkci šablony [regex_replace –](../standard-library/regex-functions.md#regex_replace), společně s příznaky shoda typu [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).  
  
 K iteraci v rámci více shod objekt regulárního výrazu, použijte šablonu třídy [regex_iterator – třída](../standard-library/regex-iterator-class.md) a [regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md) nebo jeden z jejich specializací [ cregex_iterator –](../standard-library/regex-typedefs.md#cregex_iterator), [sregex_iterator –](../standard-library/regex-typedefs.md#sregex_iterator), [wcregex_iterator –](../standard-library/regex-typedefs.md#wcregex_iterator), [wsregex_iterator –](../standard-library/regex-typedefs.md#wsregex_iterator), [cregex_token_iterator – ](../standard-library/regex-typedefs.md#cregex_token_iterator), [sregex_token_iterator –](../standard-library/regex-typedefs.md#sregex_token_iterator), [wcregex_token_iterator –](../standard-library/regex-typedefs.md#wcregex_token_iterator), nebo [wsregex_token_iterator –](../standard-library/regex-typedefs.md#wsregex_token_iterator), společně s příznaky shoda typu [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type).  
  
 Chcete-li upravit podrobnosti o gramatika regulárních výrazů, napište třídu, která implementuje vlastnosti regulární výraz.  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[basic_regex –](../standard-library/basic-regex-class.md)|Zabalí regulární výraz.|  
|[match_results –](../standard-library/match-results-class.md)|Obsahuje posloupnost submatches.|  
|[regex_constants](../standard-library/regex-constants-class.md)|Blokování vybraných konstanty.|  
|[regex_error –](../standard-library/regex-error-class.md)|Sestavy chybný regulární výraz.|  
|[regex_iterator –](../standard-library/regex-iterator-class.md)|Iteruje porovnání výsledků.|  
|[regex_traits –](../standard-library/regex-traits-class.md)|Popisuje vlastností elementů k porovnání.|  
|[regex_traits –\<char >](../standard-library/regex-traits-char-class.md)|Popisuje vlastnosti `char` k porovnání.|  
|[regex_traits – < wchar_t >](../standard-library/regex-traits-wchar-t-class.md)|Popisuje vlastnosti `wchar_t` k porovnání.|  
|[regex_token_iterator –](../standard-library/regex-token-iterator-class.md)|Iteruje submatches.|  
|[sub_match](../standard-library/sub-match-class.md)|Popisuje submatch.|  
  
### <a name="type-definitions"></a>Definice typů  
  
|||  
|-|-|  
|[cmatch –](../standard-library/regex-typedefs.md#cmatch)|Zadejte definici `char` `match_results`.|  
|[cregex_iterator –](../standard-library/regex-typedefs.md#cregex_iterator)|Zadejte definici `char` `regex_iterator`.|  
|[cregex_token_iterator –](../standard-library/regex-typedefs.md#cregex_token_iterator)|Zadejte definici `char` `regex_token_iterator`.|  
|[csub_match –](../standard-library/regex-typedefs.md#csub_match)|Zadejte definici `char` `sub_match`.|  
|[regulární výraz](../standard-library/regex-typedefs.md#regex)|Zadejte definici `char` `basic_regex`.|  
|[smatch –](../standard-library/regex-typedefs.md#smatch)|Zadejte definici `string` `match_results`.|  
|[sregex_iterator –](../standard-library/regex-typedefs.md#sregex_iterator)|Zadejte definici `string` `regex_iterator`.|  
|[sregex_token_iterator –](../standard-library/regex-typedefs.md#sregex_token_iterator)|Zadejte definici `string` `regex_token_iterator`.|  
|[ssub_match –](../standard-library/regex-typedefs.md#ssub_match)|Zadejte definici `string` `sub_match`.|  
|[wcmatch –](../standard-library/regex-typedefs.md#wcmatch)|Zadejte definici `wchar_t` `match_results`.|  
|[wcregex_iterator –](../standard-library/regex-typedefs.md#wcregex_iterator)|Zadejte definici `wchar_t` `regex_iterator`.|  
|[wcregex_token_iterator –](../standard-library/regex-typedefs.md#wcregex_token_iterator)|Zadejte definici `wchar_t` `regex_token_iterator`.|  
|[wcsub_match –](../standard-library/regex-typedefs.md#wcsub_match)|Zadejte definici `wchar_t` `sub_match`.|  
|[wregex –](../standard-library/regex-typedefs.md#wregex)|Zadejte definici `wchar_t` `basic_regex`.|  
|[wsmatch –](../standard-library/regex-typedefs.md#wsmatch)|Zadejte definici `wstring` `match_results`.|  
|[wsregex_iterator –](../standard-library/regex-typedefs.md#wsregex_iterator)|Zadejte definici `wstring` `regex_iterator`.|  
|[wsregex_token_iterator –](../standard-library/regex-typedefs.md#wsregex_token_iterator)|Zadejte definici `wstring` `regex_token_iterator`.|  
|[wssub_match –](../standard-library/regex-typedefs.md#wssub_match)|Zadejte definici `wstring` `sub_match`.|  
  
### <a name="functions"></a>Funkce  
  
|||  
|-|-|  
|[regex_match –](../standard-library/regex-functions.md#regex_match)|Přesně odpovídá regulárnímu výrazu.|  
|[regex_replace –](../standard-library/regex-functions.md#regex_replace)|Nahradí odpovídající regulární výrazy.|  
|[regex_search –](../standard-library/regex-functions.md#regex_search)|Vyhledá shoda s regulárním výrazem.|  
|[swap](../standard-library/regex-functions.md#swap)|Prohození `basic_regex` nebo `match_results` objekty.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[Operator ==](../standard-library/regex-operators.md#op_eq_eq)|Porovnání různých objektů, které jsou stejné.|  
|[Operator! =](../standard-library/regex-operators.md#op_neq)|Porovnání různých objektů, není rovno.|  
|[operátor <](../standard-library/regex-operators.md#op_lt)|Porovnání různých objektů, menší než.|  
|[operátor\<=](../standard-library/regex-operators.md#op_gt_eq)|Porovnání různých objektů, menší nebo rovno.|  
|[operátor >](../standard-library/regex-operators.md#op_gt)|Porovnání různých objektů, které jsou větší než.|  
|[Operator > =](../standard-library/regex-operators.md#op_gt_eq)|Porovnání různých objektů, větší než nebo rovno.|  
|[operátor <<](../standard-library/regex-operators.md#op_lt_lt)|Vloží `sub_match` v datovém proudu.|  
  
## <a name="see-also"></a>Viz také  
[Regulární výrazy (C++)](../standard-library/regular-expressions-cpp.md)  
[regex_constants – třída](../standard-library/regex-constants-class.md)  
[regex_error – třída](../standard-library/regex-error-class.md)  
[\<regulární výraz > funkce](../standard-library/regex-functions.md)  
[regex_iterator – třída](../standard-library/regex-iterator-class.md)  
[\<regulární výraz > operátory](../standard-library/regex-operators.md)  
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)  
[regex_traits – třída](../standard-library/regex-traits-class.md)  
[\<regulární výraz > Definice TypeDef](../standard-library/regex-typedefs.md)  


