---
title: '&lt;system_error –&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <system_error>
- system_error
dev_langs:
- C++
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f182df5bda73f9b31c86407cc1475ee6c5ec9b9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856941"
---
# <a name="ltsystemerrorgt"></a>&lt;system_error&gt;

Zahrnout záhlaví \<system_error – > Definovat třídy výjimek `system_error` a související šablon pro zpracování chyby nízké úrovně systému.

## <a name="syntax"></a>Syntaxe

```cpp
#include <system_error>
```

### <a name="objects"></a>Objekty

|||
|-|-|
|[generic_category](../standard-library/system-error-functions.md#generic_category)|Představuje kategorii pro obecné chyby.|
|[system_category](../standard-library/system-error-functions.md#system_category)|Představuje kategorii pro chyby způsobené některé nízké úrovně systému.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[generic_errno](../standard-library/system-error-typedefs.md#generic_errno)|Typ, který reprezentuje výčet, který poskytuje symbolický názvy pro všechny makra kód chyby definované Posix v `<errno.h>`.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|Vytvoří `error_code` objektu.|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|Vytvoří `error_condition` objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator==](../standard-library/system-error-operators.md#op_eq_eq)|Testy, pokud je objekt na levé straně operátoru stejný objekt na pravé straně.|
|[operator!=](../standard-library/system-error-operators.md#op_neq)|Testy, pokud objekt na levé straně operátoru není stejný jako objekt na pravé straně.|
|[operátor <](../standard-library/system-error-operators.md#op_lt)|Zkouší, zda je objekt menší než objekt předaný k porovnání.|

### <a name="enumerations"></a>Výčty

|||
|-|-|
|[errc](../standard-library/system-error-enums.md#errc)|Poskytuje symbolický názvy pro všechny makra kód chyby definované Posix v `<errno.h>`.|

### <a name="classes-and-structs"></a>Třídy a struktury

|||
|-|-|
|[error_category](../standard-library/error-category-class.md)|Představuje abstraktní, běžné základ pro objekty, která popisuje kategorie kódy chyb.|
|[error_code](../standard-library/error-code-class.md)|Reprezentuje chyby nízké úrovně systému, které jsou specifické pro implementaci.|
|[error_condition](../standard-library/error-condition-class.md)|Představuje uživatelem definované chybové kódy.|
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|Představuje predikátem typu, který vyhledá [error_code – třída](../standard-library/error-code-class.md) výčtu.|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|Představuje predikátem typu, který vyhledá [error_condition – třída](../standard-library/error-condition-class.md) výčtu.|
|[system_error](../standard-library/system-error-class.md)|Představuje základní třídu pro všechny výjimky vydané nahlásit nízké úrovně systému přetečení.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<system_error – >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
