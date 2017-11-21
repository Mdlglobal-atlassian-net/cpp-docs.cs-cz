---
title: "&lt;regulární výraz&gt; – definice TypeDef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex/std::cmatch
- regex/std::cregex_iterator
- regex/std::cregex_token_iterator
- regex/std::csub_match
- regex/std::regex
- regex/std::smatch
- regex/std::sregex_iterator
- regex/std::sregex_token_iterator
- regex/std::ssub_match
- regex/std::wcmatch
- regex/std::wcregex_iterator
- regex/std::wcregex_token_iterator
- regex/std::wcsub_match
- regex/std::wregex
- regex/std::wsmatch
- regex/std::wsregex_iterator
- regex/std::wsregex_token_iterator
- regex/std::wssub_match
dev_langs: C++
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7dad87e2d6e402333db5f51bdf8deaee1090df86
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltregexgt-typedefs"></a>&lt;regulární výraz&gt; – definice TypeDef
||||  
|-|-|-|  
|[cmatch –](#cmatch)|[cregex_iterator –](#cregex_iterator)|[cregex_token_iterator –](#cregex_token_iterator)|  
|[csub_match –](#csub_match)|[regulární výraz](#regex)|[smatch –](#smatch)|  
|[sregex_iterator –](#sregex_iterator)|[sregex_token_iterator –](#sregex_token_iterator)|[ssub_match –](#ssub_match)|  
|[wcmatch –](#wcmatch)|[wcregex_iterator –](#wcregex_iterator)|[wcregex_token_iterator –](#wcregex_token_iterator)|  
|[wcsub_match –](#wcsub_match)|[wregex –](#wregex)|[wsmatch –](#wsmatch)|  
|[wsregex_iterator –](#wsregex_iterator)|[wsregex_token_iterator –](#wsregex_token_iterator)|[wssub_match –](#wssub_match)|  
  
##  <a name="cmatch"></a>cmatch – Typedef  
 Zadejte definici char match_results.  
  
```  
typedef match_results<const char*> cmatch;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [match_results – třída](../standard-library/match-results-class.md) pro iterátory typu `const char*`.  
  
##  <a name="cregex_iterator"></a>cregex_iterator – Typedef  
 Zadejte definici char regex_iterator.  
  
```  
typedef regex_iterator<const char*> cregex_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [regex_iterator – třída](../standard-library/regex-iterator-class.md) pro iterátory typu `const char*`.  
  
##  <a name="cregex_token_iterator"></a>cregex_token_iterator – Typedef  
 Definice typu char regex_token_iterator  
  
```  
typedef regex_token_iterator<const char*> cregex_token_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md) pro iterátory typu `const char*`.  
  
##  <a name="csub_match"></a>csub_match – Typedef  
 Zadejte definici char sub_match.  
  
```  
typedef sub_match<const char*> csub_match;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [sub_match – třída](../standard-library/sub-match-class.md) pro iterátory typu `const char*`.  
  
##  <a name="regex"></a>Regex – Typedef  
 Zadejte definici char basic_regex.  
  
```  
typedef basic_regex<char> regex;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [basic_regex – třída](../standard-library/basic-regex-class.md) pro elementy typu `char`.  
  
> [!NOTE]
>  Rozšířené znaky, bude mít nepředvídatelné výsledky s `regex`. Hodnoty mimo rozsah od 0 do 127 může vést k nedefinované chování.  
  
##  <a name="smatch"></a>smatch – Typedef  
 Zadejte definici match_results řetězec.  
  
```  
typedef match_results<string::const_iterator> smatch;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [match_results – třída](../standard-library/match-results-class.md) pro iterátory typu `string::const_iterator`.  
  
##  <a name="sregex_iterator"></a>sregex_iterator – Typedef  
 Zadejte definici regex_iterator řetězec.  
  
```  
typedef regex_iterator<string::const_iterator> sregex_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [regex_iterator – třída](../standard-library/regex-iterator-class.md) pro iterátory typu `string::const_iterator`.  
  
##  <a name="sregex_token_iterator"></a>sregex_token_iterator – Typedef  
 Zadejte definici regex_token_iterator řetězec.  
  
```  
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md) pro iterátory typu `string::const_iterator`.  
  
##  <a name="ssub_match"></a>ssub_match – Typedef  
 Zadejte definici sub_match řetězce.  
  
```  
typedef sub_match<string::const_iterator> ssub_match;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [sub_match – třída](../standard-library/sub-match-class.md) pro iterátory typu `string::const_iterator`.  
  
##  <a name="wcmatch"></a>wcmatch – Typedef  
 Zadejte definici wchar_t match_results.  
  
```  
typedef match_results<const wchar_t *> wcmatch;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [match_results – třída](../standard-library/match-results-class.md) pro iterátory typu `const wchar_t*`.  
  
##  <a name="wcregex_iterator"></a>wcregex_iterator – Typedef  
 Zadejte definici wchar_t regex_iterator.  
  
```  
typedef regex_iterator<const wchar_t*> wcregex_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [regex_iterator – třída](../standard-library/regex-iterator-class.md) pro iterátory typu `const wchar_t*`.  
  
##  <a name="wcregex_token_iterator"></a>wcregex_token_iterator – Typedef  
 Zadejte definici wchar_t regex_token_iterator.  
  
```  
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md) pro iterátory typu `const wchar_t*`.  
  
##  <a name="wcsub_match"></a>wcsub_match – Typedef  
 Zadejte definici wchar_t sub_match.  
  
```  
typedef sub_match<const wchar_t*> wcsub_match;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [sub_match – třída](../standard-library/sub-match-class.md) pro iterátory typu `const wchar_t*`.  
  
##  <a name="wregex"></a>wregex – Typedef  
 Zadejte definici wchar_t basic_regex.  
  
```  
typedef basic_regex<wchar_t> wregex;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [basic_regex – třída](../standard-library/basic-regex-class.md) pro elementy typu `wchar_t`.  
  
##  <a name="wsmatch"></a>wsmatch – Typedef  
 Zadejte definici wstring match_results.  
  
```  
typedef match_results<wstring::const_iterator> wsmatch;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [match_results – třída](../standard-library/match-results-class.md) pro iterátory typu `wstring::const_iterator`.  
  
##  <a name="wsregex_iterator"></a>wsregex_iterator – Typedef  
 Zadejte definici wstring regex_iterator.  
  
```  
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [regex_iterator – třída](../standard-library/regex-iterator-class.md) pro iterátory typu `wstring::const_iterator`.  
  
##  <a name="wsregex_token_iterator"></a>wsregex_token_iterator – Typedef  
 Zadejte definici wstring regex_token_iterator.  
  
```  
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md) pro iterátory typu `wstring::const_iterator`.  
  
##  <a name="wssub_match"></a>wssub_match – Typedef  
 Zadejte definici wstring sub_match.  
  
```  
typedef sub_match<wstring::const_iterator> wssub_match;  
```  
  
### <a name="remarks"></a>Poznámky  
 Popisuje typ specializace šablon třídy [sub_match – třída](../standard-library/sub-match-class.md) pro iterátory typu `wstring::const_iterator`.  
  
## <a name="see-also"></a>Viz také  
[\<regulární výraz >](../standard-library/regex.md)  
[regex_constants – třída](../standard-library/regex-constants-class.md)  
[regex_error – třída](../standard-library/regex-error-class.md)  
[\<regulární výraz > funkce](../standard-library/regex-functions.md)  
[regex_iterator – třída](../standard-library/regex-iterator-class.md)  
[\<regulární výraz > operátory](../standard-library/regex-operators.md)  
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)  
[regex_traits – třída](../standard-library/regex-traits-class.md)  
