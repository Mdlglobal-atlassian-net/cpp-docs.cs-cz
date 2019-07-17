---
title: '&lt;system_error&gt;'
ms.date: 03/15/2019
f1_keywords:
- <system_error>
- system_error
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
ms.openlocfilehash: 4365f0aaf8fdd4d43159b78acf6dcffa4fcbe428
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246552"
---
# <a name="ltsystemerrorgt"></a>&lt;system_error&gt;

Zahrnout hlavičku \<system_error > Chcete-li definovat třídu výjimky `system_error` a související šablony pro zpracování chyb nízké úrovně systému.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<system_error >

**Namespace:** std

## <a name="members"></a>Členové

### <a name="objects"></a>Objekty

|||
|-|-|
|[generic_category –](../standard-library/system-error-functions.md#generic_category)|Představuje konkrétní kategorii obecné chyby.|
|[is_error_code_enum_v](../standard-library/system-error-functions.md#is_error_code_enum_v)||
|[is_error_condition_enum_v](../standard-library/system-error-functions.md#is_error_condition_enum_v)||
|[system_category](../standard-library/system-error-functions.md#system_category)|Představuje konkrétní kategorii chyby způsobené nižší úrovně systému přetečení.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|Vytvoří `error_code` objektu.|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|Vytvoří `error_condition` objektu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator==](../standard-library/system-error-operators.md#op_eq_eq)|Testuje, zda je objekt na levé straně operátoru roven objektu na pravé straně.|
|[operator!=](../standard-library/system-error-operators.md#op_neq)|Testuje, zda je objekt na levé straně operátoru není roven objektu na pravé straně.|
|[Operator <](../standard-library/system-error-operators.md#op_lt)|Zkouší, zda je objekt menší než objekt předaný k porovnání.|
|[operátor <<](../standard-library/system-error-operators.md#op_ostream)||

### <a name="enums"></a>Výčty

|||
|-|-|
|[errc](../standard-library/system-error-enums.md#errc)|Poskytuje symbolické názvy pro všechna makra kód chyby definované v rámci specifikace Posix v `<errno.h>`.|

### <a name="classes-and-structs"></a>Třídy a struktury

|||
|-|-|
|[error_category –](../standard-library/error-category-class.md)|Představuje abstraktní, běžné základ pro objekty, které popisují kategorie kódů chyb.|
|[error_code](../standard-library/error-code-class.md)|Reprezentuje chyby nízké úrovně systému, které jsou specifické pro implementaci.|
|[error_condition](../standard-library/error-condition-class.md)|Představuje uživatelem definované chybové kódy.|
|[Hodnota hash](../standard-library/hash-structure.md#system_error)||
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|Představuje typ predikát, který testuje [error_code – třída](../standard-library/error-code-class.md) výčtu.|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|Představuje typ predikát, který testuje [error_condition – třída](../standard-library/error-condition-class.md) výčtu.|
|[system_error](../standard-library/system-error-class.md)|Představuje základní třídu pro všechny výjimky vyvolané hlášení nižší úrovně systému přetečení.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
