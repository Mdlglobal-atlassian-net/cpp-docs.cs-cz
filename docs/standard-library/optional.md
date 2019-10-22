---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: bce31811c98d351f3c561b3136d41f7ed23d13e0
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687261"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Definuje šablonu třídy kontejneru `optional` a několik podpůrných šablon.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<optional >

**Obor názvů:** std

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator = = – operátor](../standard-library/optional-operators.md#op_eq_eq)|Testuje, zda je objekt roven jinému objektu.|
|[operator!=](../standard-library/optional-operators.md#op_neq)|Testuje, zda objekt není roven jinému objektu.|
|[operátor <](../standard-library/optional-operators.md#op_lt)|Testuje, zda je objekt na levé straně menší než objekt na pravé straně.|
|[operátor < =](../standard-library/optional-operators.md#op_lt_eq)|Testuje, zda je objekt na levé straně menší nebo roven objektu na pravé straně.|
|[operátor >](../standard-library/optional-operators.md#op_gt)|Testuje, zda je objekt na levé straně větší než objekt na pravé straně.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Testuje, zda je objekt na levé straně větší nebo roven objektu na pravé straně.|

> [!NOTE]
> Kromě relačních porovnávacích operátorů \<optional > také podporuje porovnání s **nullopt** a `T`.

### <a name="functions"></a>Funkce

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Vytvoří objekt jako volitelný.|
|[adresu](../standard-library/optional-functions.md#swap)|Zamění obsažené hodnoty dvou objektů `optional`.|

### <a name="classes-and-structs"></a>Třídy a struktury

|||
|-|-|
|hash|Vrátí hodnotu hash obsaženého objektu.|
|[Volitelná třída](../standard-library/optional-class.md)|Popisuje objekt, který může nebo nemusí obsahovat hodnotu.|
|[nullopt_t – struktura](../standard-library/nullopt-t-structure.md)|Popisuje objekt, který nedrží hodnotu.|
|[bad_optional_access – třída](../standard-library/bad-optional-access-class.md)|Popisuje objekt vyvolaný jako výjimka pro hlášení pokusu o přístup k hodnotě, která není k dispozici.|

### <a name="objects"></a>Objekty

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|Instance `nullopt_t` pro porovnání.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
