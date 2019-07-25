---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 47924c3d6bd1a2f45cdbac648f4f563c57ce8939
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459120"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

Definuje šablonu `basic_string_view` třídy a související typy a operátory. (Vyžaduje možnost kompilátoru [std: c++ 17](../build/reference/std-specify-language-standard-version.md) nebo novější.)

## <a name="syntax"></a>Syntaxe

```cpp
#include <string_view>
```

## <a name="remarks"></a>Poznámky

String_view rodina specializace šablony poskytuje efektivní způsob, jak předat nevlastnící popisovač, který je k dispozici, pro data znaků libovolných objektů podobných řetězci s prvním prvkem sekvence na pozici nula. Parametr funkce typu `string_view` (který je definicí typedef pro `basic_string_view<char>`) `std::string`může přijímat argumenty jako, **char\*** nebo jiné třídy typu String, pro které implicitní převod na `string_view`je definován. Podobně parametr `wstring_view`nebo `u16string_view` můžepřijmout`u32string_view` libovolný typ řetězce, pro který je definován implicitní převod. Další informace naleznete v tématu [Třída basic_string_view](../standard-library/basic-string-view-class.md).

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Specializace šablony `basic_string_view` třídy s elementy typu **char**.|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Specializace šablony `basic_string_view` třídy s elementy typu **wchar_t**.|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|Specializace šablony `basic_string_view` třídy s prvky typu `char16_t`.|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|Specializace šablony `basic_string_view` třídy s prvky typu `char32_t`.|

### <a name="operators"></a>Operátory

`string_view` Operátory > \<string_view mohou porovnat objekty s objekty libovolných typů převoditelné řetězce.

|Operátor|Popis|
|-|-|
|[operator!=](../standard-library/string-view-operators.md#op_neq)|Testuje, zda objekt na levé straně operátoru není roven objektu na pravé straně.|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|Testuje, zda je objekt na levé straně operátoru roven objektu na pravé straně.|
|[operátor <](../standard-library/string-view-operators.md#op_lt)|Testuje, zda je objekt na levé straně operátoru menší než objekt na pravé straně.|
|[operátor < =](../standard-library/string-view-operators.md#op_lt_eq)|Testuje, zda je objekt na levé straně operátoru menší než nebo roven objektu na pravé straně.|
|[operátor <\<](../standard-library/string-view-operators.md#op_lt_lt)|Funkce šablony, která vloží `string_view` do výstupního datového proudu.|
|[operátor >](../standard-library/string-view-operators.md#op_gt)|Testuje, zda je objekt na levé straně operátoru větší než objekt na pravé straně.|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|Testuje, zda je objekt na levé straně operátoru větší než nebo roven objektu na pravé straně.|

### <a name="literals"></a>Literály

|Operátor|Popis|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|`string_view`Vytvoří ,`wstring_view`, ,nebo`u32string_view` v závislosti na typu řetězcového literálu, ke kterému je připojen. `u16string_view`|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_string_view – třída](../standard-library/basic-string-view-class.md)|Šablona třídy, která poskytuje zobrazení jen pro čtení do sekvence libovolných objektů podobných znakům.|
|[kontrole](string-view-hash.md)|Objekt funkce, který vytváří hodnotu hash pro string_view.|

## <a name="requirements"></a>Požadavky

- **Hlavička:** \<string_view >

- **Obor názvů:** std

- **Možnost kompilátoru:** std: c++ 17 (nebo novější)

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
