---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: f3b4896a3cb4774e46b36480dd9769fa131fc287
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957181"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Definuje třídu `optional` šablony kontejneru a několik podpůrných šablon.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<volitelné >

**Obor názvů:** std

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|Testuje, zda je objekt roven jinému objektu.|
|[operator!=](../standard-library/optional-operators.md#op_neq)|Testuje, zda objekt není roven jinému objektu.|
|[operátor <](../standard-library/optional-operators.md#op_lt)|Testuje, zda je objekt na levé straně menší než objekt na pravé straně.|
|[operátor < =](../standard-library/optional-operators.md#op_lt_eq)|Testuje, zda je objekt na levé straně menší nebo roven objektu na pravé straně.|
|[operátor >](../standard-library/optional-operators.md#op_gt)|Testuje, zda je objekt na levé straně větší než objekt na pravé straně.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Testuje, zda je objekt na levé straně větší nebo roven objektu na pravé straně.|

> [!NOTE]
> Kromě relačních porovnání, \<volitelné operátory > také podporují porovnání s **nullopt** a. `T`

### <a name="functions"></a>Funkce

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Vytvoří objekt jako volitelný.|
|[swap](../standard-library/optional-functions.md#swap)|Zamění obsažené hodnoty dvou `optional` objektů.|

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
