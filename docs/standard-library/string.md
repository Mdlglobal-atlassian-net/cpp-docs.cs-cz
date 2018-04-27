---
title: '&lt;řetězec&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- string/std::<string>
- <string>
dev_langs:
- C++
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f915ab0378784b9a8979a422b061c4ef7c155ee6
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltstringgt"></a>&lt;string&gt;

Definuje třídu šablony kontejneru `basic_string` a různé podpůrné šablony.

Další informace o `basic_string`, najdete v části [basic_string – třída](../standard-library/basic-string-class.md)

## <a name="syntax"></a>Syntaxe

```cpp
#include <string>
```

## <a name="remarks"></a>Poznámky

Jazyk C++ a standardní knihovny C++ podporují dva typy řetězců:

- Často označuje jako C řetězce ukončené hodnotou null znak pole.

- Objekty třídy šablony, typu `basic_string`, které zpracovávají všechny `char`-jako argumenty pro šablony.

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|Typ, který popisuje specializace šablon třídy `basic_string` elementy typu `char` jako `string`.|
|[wstring](../standard-library/string-typedefs.md#wstring)|Typ, který popisuje specializace šablon třídy `basic_string` elementy typu `wchar_t` jako `wstring`.|
|[u16string](../standard-library/string-typedefs.md#u16string)|Typ, který popisuje specializace šablon třídy `basic_string` podle elementy typu `char16_t`.|
|[u32string –](../standard-library/string-typedefs.md#u32string)|Typ, který popisuje specializace šablon třídy `basic_string` podle elementy typu `char32_t`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor +](../standard-library/string-operators.md#op_add)|Zřetězí dva objekty řetězce.|
|[operator!=](../standard-library/string-operators.md#op_neq)|Testy, pokud řetězec objekt na levé straně operátoru není stejný jako řetězec objekt na pravé straně.|
|[operator==](../standard-library/string-operators.md#op_eq_eq)|Testy, pokud řetězec objekt na levé straně operátoru rovná řetězec objekt na pravé straně.|
|[operátor <](../standard-library/string-operators.md#op_lt)|Testuje, pokud objekt na levé straně operátoru řetězce je menší než na objekt řetězce na pravé straně.|
|[Operator < =](../standard-library/string-operators.md#op_lt_eq)|Pokud řetězec objekt na levé straně operátoru testů je menší než nebo rovna hodnotě objekt řetězce na pravé straně.|
|[operátor <\<](../standard-library/string-operators.md#op_lt_lt)|Funkce šablony, která vloží řetězec do výstupního datového proudu.|
|[operátor >](../standard-library/string-operators.md#op_gt)|Testy, pokud je řetězec objekt na levé straně operátoru větší než na objekt řetězce na pravé straně.|
|[operator>=](../standard-library/string-operators.md#op_gt_eq)|Testy, pokud je řetězec objekt na levé straně operátoru větší než nebo rovna hodnotě řetězec objekt na pravé straně.|
|[operátor >>](../standard-library/string-operators.md#op_gt_gt)|Funkce šablony, která extrahuje řetězec ze vstupního datového proudu.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|||
|-|-|
|[Swap](../standard-library/string-functions.md#swap)|Výměny pole znaků dva řetězce.|
|[stod –](../standard-library/string-functions.md#stod)|Převede posloupnost znaků pro `double.`|
|[stof –](../standard-library/string-functions.md#stof)|Převede posloupnost znaků do `float`.|
|[stoi –](../standard-library/string-functions.md#stoi)|Převede posloupnost znaků na celé číslo.|
|[stold –](../standard-library/string-functions.md#stold)|Převede posloupnost znaků do `long double`.|
|[stoll –](../standard-library/string-functions.md#stoll)|Převede posloupnost znaků do `long long`.|
|[stoul –](../standard-library/string-functions.md#stoul)|Převede posloupnost znaků do `unsigned long`.|
|[stoull –](../standard-library/string-functions.md#stoull)|Převede posloupnost znaků do `unsigned long long`.|
|[to_string](../standard-library/string-functions.md#to_string)|Převede hodnotu na `string`.|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Převede hodnotu na široké `string`.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[getline šablony](../standard-library/string-functions.md#getline)|Extrahujte řetězce ze vstupního proudu řádek po řádku.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_string – třída](../standard-library/basic-string-class.md)|Šablony třídy, která popisuje objekty, které můžete ukládat posloupnost libovolný znak jako objekty.|
|[char_traits – struktura](../standard-library/char-traits-struct.md)|Třídu šablony, která popisuje atributy přidružené znak typu CharType|

### <a name="specializations"></a>Specializace

|||
|-|-|
|[char_traits –\<char > – Struktura](../standard-library/char-traits-char-struct.md)|Struktura, která je specializace šablony struktura `char_traits` \<CharType > elementu typu `char`.|
|[char_traits<wchar_t> – struktura](../standard-library/char-traits-wchar-t-struct.md)|Struktura, která je specializace šablony struktura `char_traits` \<CharType > elementu typu `wchar_t`.|
|[char_traits<char16_t> – struktura](../standard-library/char-traits-char16-t-struct.md)|Struktura, která je specializace šablony struktura `char_traits` \<CharType > elementu typu `char16_t`.|
|[char_traits<char32_t> – struktura](../standard-library/char-traits-char32-t-struct.md)|Struktura, která je specializace šablony struktura `char_traits` \<CharType > elementu typu `char32_t`.|

## <a name="requirements"></a>Požadavky

- **Záhlaví:** \<řetězec >

- **Namespace:** – std

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
