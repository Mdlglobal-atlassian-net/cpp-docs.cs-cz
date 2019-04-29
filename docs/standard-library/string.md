---
title: '&lt;string&gt;'
ms.date: 11/04/2016
f1_keywords:
- string/std::<string>
- <string>
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 3d84f4707af33f44a930f7f67b7f751e2ead627c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412303"
---
# <a name="ltstringgt"></a>&lt;string&gt;

Definuje kontejner šablony třídy `basic_string` a různé podpůrných šablon.

Další informace o `basic_string`, naleznete v tématu [basic_string – třída](../standard-library/basic-string-class.md)

## <a name="syntax"></a>Syntaxe

```cpp
#include <string>
```

## <a name="remarks"></a>Poznámky

Jazyk C++ a standardní knihovny C++ podporuje dva typy řetězce:

- Označovaný také jako C řetězce polí znaků zakončených znakem null.

- Objekty třídy šablony, typu `basic_string`, zpracovávaly všechny **char**– jako argumenty šablony.

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|Typ, který popisuje specializace třídy šablony `basic_string` elementy typu **char** jako `string`.|
|[wstring](../standard-library/string-typedefs.md#wstring)|Typ, který popisuje specializace třídy šablony `basic_string` elementy typu **wchar_t** jako `wstring`.|
|[u16string](../standard-library/string-typedefs.md#u16string)|Typ, který popisuje specializace třídy šablony `basic_string` založené na prvky typu `char16_t`.|
|[u32string](../standard-library/string-typedefs.md#u32string)|Typ, který popisuje specializace třídy šablony `basic_string` založené na prvky typu `char32_t`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[Operator +](../standard-library/string-operators.md#op_add)|Zřetězí dva objekty řetězce.|
|[operator!=](../standard-library/string-operators.md#op_neq)|Testuje, zda je na objekt řetězce na levé straně operátoru není roven objektu string na pravé straně.|
|[operator==](../standard-library/string-operators.md#op_eq_eq)|Testuje, zda na objekt řetězce na levé straně operátoru roven objektu řetězce na pravé straně.|
|[Operator <](../standard-library/string-operators.md#op_lt)|Testuje, zda je na objekt řetězce na levé straně operátoru menší než do objektu string na pravé straně.|
|[operator<=](../standard-library/string-operators.md#op_lt_eq)|Testuje, zda je řetězec, objekt na levé straně operátoru je menší než nebo rovno řetězci objekt na pravé straně.|
|[Operator <\<](../standard-library/string-operators.md#op_lt_lt)|Funkce šablony, která vloží řetězec do výstupního datového proudu.|
|[operator>](../standard-library/string-operators.md#op_gt)|Testuje, zda je řetězec objekt na levé straně operátoru větší než objekt řetězce na pravé straně.|
|[operator>=](../standard-library/string-operators.md#op_gt_eq)|Testuje, zda je na objekt řetězce na levé straně operátoru větší než nebo rovno řetězci objekt na pravé straně.|
|[operator>>](../standard-library/string-operators.md#op_gt_gt)|Funkce šablony, který extrahuje řetězce ze vstupního datového proudu.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|||
|-|-|
|[swap](../standard-library/string-functions.md#swap)|Vymění pole znaků dva řetězce.|
|[stod](../standard-library/string-functions.md#stod)|Převede znakovou sekvenci k **double**.|
|[stof](../standard-library/string-functions.md#stof)|Převede znakovou sekvenci k **float**.|
|[stoi](../standard-library/string-functions.md#stoi)|Převede znakovou sekvenci na celé číslo.|
|[stold](../standard-library/string-functions.md#stold)|Převede znakovou sekvenci k **long double**.|
|[stoll](../standard-library/string-functions.md#stoll)|Převede znakovou sekvenci k **long long**.|
|[stoul](../standard-library/string-functions.md#stoul)|Převede znakovou sekvenci do **unsigned long**.|
|[stoull](../standard-library/string-functions.md#stoull)|Převede znakovou sekvenci do **unsigned long long**.|
|[to_string](../standard-library/string-functions.md#to_string)|Převede hodnotu na `string`.|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Převede hodnotu na široké `string`.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[getline šablony](../standard-library/string-functions.md#getline)|Extrahuje řetězce ze vstupního proudu řádek po řádku.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_string – třída](../standard-library/basic-string-class.md)|Třída šablony popisuje objekty, které můžete ukládat posloupnost libovolný znak jako objekty.|
|[char_traits – struktura](../standard-library/char-traits-struct.md)|Třída šablony popisující atributy přidružené k znaku typu CharType|

### <a name="specializations"></a>Specializace

|||
|-|-|
|[char_traits\<char > – Struktura](../standard-library/char-traits-char-struct.md)|Struktura, která je specializací šablony struktury `char_traits` \<CharType > pro element typu `char`.|
|[char_traits<wchar_t> – struktura](../standard-library/char-traits-wchar-t-struct.md)|Struktura, která je specializací šablony struktury `char_traits` \<CharType > pro element typu `wchar_t`.|
|[char_traits<char16_t> – struktura](../standard-library/char-traits-char16-t-struct.md)|Struktura, která je specializací šablony struktury `char_traits` \<CharType > pro element typu `char16_t`.|
|[char_traits<char32_t> – struktura](../standard-library/char-traits-char32-t-struct.md)|Struktura, která je specializací šablony struktury `char_traits` \<CharType > pro element typu `char32_t`.|

## <a name="requirements"></a>Požadavky

- **Záhlaví:** \<řetězec >

- **Namespace:** std

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
