---
title: '&lt;system_error&gt;'
ms.date: 03/15/2019
f1_keywords:
- <system_error>
- system_error
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
ms.openlocfilehash: b9ddb3117afe37060b8013be235bdb11a2a031ac
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898854"
---
# <a name="ltsystem_errorgt"></a>&lt;system_error&gt;

Zahrňte system_error > hlaviček \<k definování třídy výjimek `system_error` a souvisejících šablon pro zpracování chyb systému nízké úrovně.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<system_error >

**Obor názvů:** std

## <a name="members"></a>Členové

### <a name="objects"></a>Objekty

|||
|-|-|
|[generic_category](../standard-library/system-error-functions.md#generic_category)|Představuje kategorii pro obecné chyby.|
|[is_error_code_enum_v](../standard-library/system-error-functions.md#is_error_code_enum_v)||
|[is_error_condition_enum_v](../standard-library/system-error-functions.md#is_error_condition_enum_v)||
|[system_category](../standard-library/system-error-functions.md#system_category)|Představuje kategorii pro chyby způsobené přetečeními systému nižší úrovně.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|Vytvoří `error_code` objektu.|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|Vytvoří `error_condition` objektu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator==](../standard-library/system-error-operators.md#op_eq_eq)|Testuje, zda je objekt na levé straně operátoru roven objektu na pravé straně.|
|[operator!=](../standard-library/system-error-operators.md#op_neq)|Testuje, zda objekt na levé straně operátoru není roven objektu na pravé straně.|
|[operátor <](../standard-library/system-error-operators.md#op_lt)|Zkouší, zda je objekt menší než objekt předaný k porovnání.|
|[operátor < <](../standard-library/system-error-operators.md#op_ostream)||

### <a name="enums"></a>Výčty

|||
|-|-|
|[errc](../standard-library/system-error-enums.md#errc)|Poskytuje symbolické názvy pro všechna makra kódu chyby definovaná v subsystému POSIX v `<errno.h>`.|

### <a name="classes-and-structs"></a>Třídy a struktury

|||
|-|-|
|[error_category](../standard-library/error-category-class.md)|Představuje abstraktní, společný základ pro objekty, které popisují kategorii chybových kódů.|
|[error_code](../standard-library/error-code-class.md)|Představuje systémové chyby nízké úrovně, které jsou specifické pro konkrétní implementaci.|
|[error_condition](../standard-library/error-condition-class.md)|Představuje uživatelsky definované kódy chyb.|
|[kontrole](../standard-library/hash-structure.md#system_error)||
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|Představuje predikát typu, který testuje pro [error_code výčet třídy](../standard-library/error-code-class.md) .|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|Představuje predikát typu, který testuje pro [error_condition výčet třídy](../standard-library/error-condition-class.md) .|
|[system_error](../standard-library/system-error-class.md)|Představuje základní třídu pro všechny výjimky vyvolané k hlášení přetečení systému nízké úrovně.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
