---
title: '&lt;optional&gt;'
ms.date: 11/04/2016
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: 83a0ad52735f92d731dafb32ad1be5a8278776b4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447187"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Definuje třídu šablony kontejneru volitelnou a několik podpůrných šablon.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<volitelné >

**Obor názvů:** std

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|Testuje, zda `optional` je objekt na levé straně operátoru roven `optional` objektu na pravé straně.|
|[operator!=](../standard-library/optional-operators.md#op_neq)|Testuje, zda `optional` objekt na levé straně operátoru není roven `optional` objektu na pravé straně.|
|[operátor <](../standard-library/optional-operators.md#op_lt)|Testuje, `optional` zda je objekt na levé straně operátoru menší `optional` než objekt na pravé straně.|
|[operátor < =](../standard-library/optional-operators.md#op_lt_eq)|Testuje, zda `optional` je objekt na levé straně operátoru menší než nebo roven `optional` objektu na pravé straně.|
|[operátor >](../standard-library/optional-operators.md#op_gt)|Testuje, `optional` zda je objekt na levé straně operátoru větší `optional` než objekt na pravé straně.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Testuje, zda `optional` je objekt na levé straně operátoru větší než nebo roven `optional` objektu na pravé straně.|

> [!NOTE]
> Kromě relačních porovnání, \<volitelné operátory > také podporují porovnání s **nullopt** a. `T`

### <a name="functions"></a>Funkce

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Vytvoří objekt jako volitelný.|
|[swap](../standard-library/optional-functions.md#swap)||

### <a name="classes-and-structs"></a>Třídy a struktury

|||
|-|-|
|[kontrole]()||
|[Volitelná třída](../standard-library/optional-class.md)|Popisuje objekt, který může nebo nemusí obsahovat hodnotu.|
|[nullopt_t – struktura](../standard-library/nullopt-t-structure.md)|Popisuje objekt, který nedrží hodnotu.|
|[bad_optional_access – třída](../standard-library/bad-optional-access-class.md)|Popisuje objekt vyvolaný jako výjimka pro hlášení pokusu o přístup k hodnotě, která není k dispozici.|

### <a name="objects"></a>Objekty

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)||

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
