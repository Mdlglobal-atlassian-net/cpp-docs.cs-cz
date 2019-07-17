---
title: '&lt;optional&gt;'
ms.date: 11/04/2016
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: c73ad2ad94a5de29bc2c457fdf6ca8b9c783615c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267898"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

Definuje kontejner šablony třídy, který je volitelné a několik podpůrných šablon.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<volitelné >

**Namespace:** std

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|Testuje, zda `optional` objekt na levé straně operátoru rovná `optional` objekt na pravé straně.|
|[operator!=](../standard-library/optional-operators.md#op_neq)|Testuje, zda `optional` objekt na levé straně operátoru není roven `optional` objekt na pravé straně.|
|[Operator <](../standard-library/optional-operators.md#op_lt)|Testuje, zda `optional` objekt na levé straně operátoru menší než `optional` objekt na pravé straně.|
|[Operator < =](../standard-library/optional-operators.md#op_lt_eq)|Testuje, zda `optional` je objekt na levé straně operátoru menší než nebo rovna hodnotě `optional` objekt na pravé straně.|
|[Operator >](../standard-library/optional-operators.md#op_gt)|Testuje, zda `optional` je objekt na levé straně operátoru větší než `optional` objekt na pravé straně.|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|Testuje, zda `optional` je objekt na levé straně operátoru větší než nebo rovna hodnotě `optional` objekt na pravé straně.|

> [!NOTE]
> Kromě relační porovná \<volitelné > operátory také podporuje porovnání s **nullopt** a `T`.

### <a name="functions"></a>Funkce

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|Vytvoří objekt volitelné.|
|[swap](../standard-library/optional-functions.md#swap)||

### <a name="classes-and-structs"></a>Třídy a struktury

|||
|-|-|
|[Hodnota hash]()||
|[volitelné třídy](../standard-library/optional-class.md)|Popisuje objekt, který může nebo nemusí obsahovat hodnotu.|
|[nullopt_t – struktura](../standard-library/nullopt-t-structure.md)|Popisuje objekt, který není drží hodnotu.|
|[bad_optional_access třídy](../standard-library/bad-optional-access-class.md)|Popisuje objekt vyvolána jako výjimku do sestavy pokus o přístup k hodnotě není existuje.|

### <a name="objects"></a>Objekty

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)||

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
