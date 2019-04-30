---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 8952416cf37fc4d8d281d6ced9b8264495ec3799
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346647"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

Definuje šablonu třídy `basic_string_view` a souvisejících typů a operátory. (Vyžaduje – možnost kompilátoru [std: c ++ 17](../build/reference/std-specify-language-standard-version.md) nebo novější.)

## <a name="syntax"></a>Syntaxe

```cpp
#include <string_view>
```

## <a name="remarks"></a>Poznámky

Řady string_view specializace šablony poskytuje efektivní způsob, jak předat jen pro čtení, bezpečnost výjimek, vlastnící popisovač znaková data ze všech objektů jako řetězec s první prvek pořadí na pozici nula. Parametr – funkce typu `string_view` (což je definice typu `basic_string_view<char>`) může přijímat argumenty, jako `std::string`, **char\***, nebo v jiné třídě jako řetězec z úzkých znaků, pro které implicitní převod na `string_view` je definována. Obdobně parametr `wstring_view`, `u16string_view` nebo `u32string_view` může přijmout libovolný typ řetězce, pro který je definován implicitní převod. Další informace najdete v tématu [basic_string_view třídy](../standard-library/basic-string-view-class.md).

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Specializace šablony třídy `basic_string_view` elementy typu **char**.|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Specializace šablony třídy `basic_string_view` elementy typu **wchar_t**.|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|Specializace šablony třídy `basic_string_view` elementy typu `char16_t`.|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|Specializace šablony třídy `basic_string_view` elementy typu `char32_t`.|

### <a name="operators"></a>Operátory

\<String_view > můžete porovnat operátory `string_view` objekty k objektům jakékoli převoditelné typy řetězců.

|Operátor|Popis|
|-|-|
|[operator!=](../standard-library/string-view-operators.md#op_neq)|Testuje, zda je objekt na levé straně operátoru není roven objektu na pravé straně.|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|Testuje, zda je objekt na levé straně operátoru roven objektu na pravé straně.|
|[Operator <](../standard-library/string-view-operators.md#op_lt)|Testuje, zda je objekt na levé straně operátoru menší než na objekt na pravé straně.|
|[operator<=](../standard-library/string-view-operators.md#op_lt_eq)|Testuje, zda je objekt na levé straně operátoru menší než nebo roven objektu na pravé straně.|
|[Operator <\<](../standard-library/string-view-operators.md#op_lt_lt)|Funkce šablony, který se vkládá `string_view` do výstupní datový proud.|
|[operator>](../standard-library/string-view-operators.md#op_gt)|Testuje, zda je objekt na levé straně operátoru větší než objekt na pravé straně.|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|Testuje, zda je objekt na levé straně operátoru větší než nebo stejný jako objekt na pravé straně.|

### <a name="literals"></a>Literály

|Operátor|Popis|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|Vytvoří `string_view`, `wstring_view`, `u16string_view`, nebo `u32string_view` v závislosti na typu řetězcový literál, na který se připojí.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_string_view – třída](../standard-library/basic-string-view-class.md)|Šablony třídy, která poskytuje zobrazení jen pro čtení na sekvenci libovolný znak jako objekty.|
|[Hodnota hash](string-view-hash.md)|Objekt funkce, která vytvoří hodnotu hash pro string_view.|

## <a name="requirements"></a>Požadavky

- **Záhlaví:** \<string_view >

- **Namespace:** std

- **– Možnost kompilátoru:** std: c ++ 17 (nebo novější)

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
