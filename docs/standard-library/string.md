---
title: '&lt;string&gt;'
ms.date: 11/04/2016
f1_keywords:
- string/std::<string>
- <string>
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: fda00cd5a8f8768688c8e10f25a0d1f2370a256f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459193"
---
# <a name="ltstringgt"></a>&lt;string&gt;

Definuje třídu `basic_string` šablony kontejneru a různé podpůrné šablony.

Další informace o `basic_string`naleznete v tématu [Třída basic_string](../standard-library/basic-string-class.md) .

## <a name="syntax"></a>Syntaxe

```cpp
#include <string>
```

## <a name="remarks"></a>Poznámky

C++ Jazyk a C++ standardní knihovna podporují dva typy řetězců:

- Znaková pole zakončená hodnotou null často označují jako řetězce jazyka C.

- Objekty třídy šablony typu `basic_string`, které zpracovávají všechny argumenty šablony jako **znak**.

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|Typ, který popisuje specializaci třídy `basic_string` šablony s elementy typu  `string`char jako.|
|[wstring](../standard-library/string-typedefs.md#wstring)|Typ, který popisuje specializaci třídy `basic_string` šablony s prvky typu  `wstring`wchar_t jako.|
|[u16string](../standard-library/string-typedefs.md#u16string)|Typ, který popisuje specializaci třídy `basic_string` šablony na základě prvků typu. `char16_t`|
|[u32string](../standard-library/string-typedefs.md#u32string)|Typ, který popisuje specializaci třídy `basic_string` šablony na základě prvků typu. `char32_t`|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator + – operátor](../standard-library/string-operators.md#op_add)|Zřetězí dva objekty řetězce.|
|[operator!=](../standard-library/string-operators.md#op_neq)|Testuje, zda objekt String na levé straně operátoru není roven objektu řetězce na pravé straně.|
|[operator==](../standard-library/string-operators.md#op_eq_eq)|Testuje, zda je objekt řetězce na levé straně operátoru roven objektu řetězce na pravé straně.|
|[operátor <](../standard-library/string-operators.md#op_lt)|Testuje, zda je objekt řetězce na levé straně operátoru menší než na objekt řetězce na pravé straně.|
|[operátor < =](../standard-library/string-operators.md#op_lt_eq)|Testuje, zda je objekt řetězce na levé straně operátoru menší než nebo roven objektu řetězce na pravé straně.|
|[operátor <\<](../standard-library/string-operators.md#op_lt_lt)|Funkce šablony, která vloží řetězec do výstupního datového proudu.|
|[operátor >](../standard-library/string-operators.md#op_gt)|Testuje, zda je objekt řetězce na levé straně operátoru větší než na objekt řetězce na pravé straně.|
|[operator>=](../standard-library/string-operators.md#op_gt_eq)|Testuje, zda je objekt řetězce na levé straně operátoru větší než nebo roven objektu řetězce na pravé straně.|
|[operátor > >](../standard-library/string-operators.md#op_gt_gt)|Funkce šablony, která extrahuje řetězec ze vstupního datového proudu.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|||
|-|-|
|[kontrole]()||
|[swap](../standard-library/string-functions.md#swap)|Vyměňuje pole znaků dvou řetězců.|
|[stod](../standard-library/string-functions.md#stod)|Převede posloupnost znaků na dvojitou hodnotu.|
|[stof](../standard-library/string-functions.md#stof)|Převede sekvenci znaků na **float**.|
|[stoi](../standard-library/string-functions.md#stoi)|Převede sekvenci znaků na celé číslo.|
|[stold](../standard-library/string-functions.md#stold)|Převede sekvenci znaků na **Long Double**.|
|[stoll](../standard-library/string-functions.md#stoll)|Převede sekvenci znaků na **dlouhou dobu**.|
|[stoul](../standard-library/string-functions.md#stoul)|Převede sekvenci znaků na **Long bez znaménka**.|
|[stoull](../standard-library/string-functions.md#stoull)|Převede znakovou sekvenci do **unsigned long long**.|
|[to_string](../standard-library/string-functions.md#to_string)|Převede hodnotu na `string`.|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Převede hodnotu na šířku `string`.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[Šablona getline](../standard-library/string-functions.md#getline)|Extrahuje řetězce ze vstupního streamu řádek po řádku.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_string – třída](../standard-library/basic-string-class.md)|Třída šablony, která popisuje objekty, které mohou ukládat sekvenci libovolných objektů podobných znakům.|
|[char_traits – struktura](../standard-library/char-traits-struct.md)|Třída šablony, která popisuje atributy přidružené ke znaku typu CharType|

### <a name="specializations"></a>Specializace

|||
|-|-|
|[char_traits\<char > – Struktura](../standard-library/char-traits-char-struct.md)|Struktura, která je specializací struktury `char_traits` \<šablony CharType > k elementu typu `char`.|
|[char_traits<wchar_t> – struktura](../standard-library/char-traits-wchar-t-struct.md)|Struktura, která je specializací struktury `char_traits` \<šablony CharType > k elementu typu `wchar_t`.|
|[char_traits<char16_t> – struktura](../standard-library/char-traits-char16-t-struct.md)|Struktura, která je specializací struktury `char_traits` \<šablony CharType > k elementu typu `char16_t`.|
|[char_traits<char32_t> – struktura](../standard-library/char-traits-char32-t-struct.md)|Struktura, která je specializací struktury `char_traits` \<šablony CharType > k elementu typu `char32_t`.|

## <a name="requirements"></a>Požadavky

- **Hlavička:** \<> řetězců

- **Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
