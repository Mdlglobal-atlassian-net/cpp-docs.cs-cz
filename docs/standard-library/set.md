---
title: '&lt;set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <set>
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
ms.openlocfilehash: b947d9ba268c9b4028415216e4ad0813f2d71947
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450528"
---
# <a name="ltsetgt"></a>&lt;set&gt;

Definuje třídy šablony kontejneru nastavené a multiset a jejich podpůrné šablony.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<nastavit >

**Obor názvů:** std

> [!NOTE]
> Sada > Knihovna také `#include <initializer_list>` používá příkaz. \<

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|Nastavit verzi|Verze multiset|Popis|
|-|-|-|
|[operator! = (set) – operátor](../standard-library/set-operators.md#op_neq)|[operator! = (multiset) – operátor](../standard-library/set-operators.md#op_neq)|Testuje, zda objekt set nebo multiset na levé straně operátoru není roven sadě nebo objektu multiset na pravé straně.|
|[operátor < (set)](../standard-library/set-operators.md#op_lt)|[operátor < (multiset)](../standard-library/set-operators.md#op_lt_multiset)|Testuje, zda je objekt set nebo multiset na levé straně operátoru menší než sada nebo objekt multiset na pravé straně.|
|[operator < = (set) – operátor](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset) – operátor](../standard-library/set-operators.md#op_lt_eq_multiset)|Testuje, zda je objekt set nebo multiset na levé straně operátoru menší než nebo roven množině nebo objektu multiset na pravé straně.|
|[operator = = (set) – operátor](../standard-library/set-operators.md#op_eq_eq)|[operator== (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|Testuje, zda je objekt set nebo multiset na levé straně operátoru roven sadě nebo objektu multiset na pravé straně.|
|[operátor > (set)](../standard-library/set-operators.md#op_gt)|[operátor > (multiset)](../standard-library/set-operators.md#op_gt_multiset)|Testuje, zda je objekt set nebo multiset na levé straně operátoru větší než sada nebo objekt multiset na pravé straně.|
|[operator > = (set) – operátor](../standard-library/set-operators.md#op_gt_eq)|[operator>= (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|Testuje, zda je objekt set nebo multiset na levé straně operátoru větší než nebo rovno množině nebo objektu multiset na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|Nastavit verzi|Verze multiset|Popis|
|-|-|-|
|[swap](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|Vyměňuje prvky dvou sad nebo množin.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[set – třída](../standard-library/set-class.md)|Slouží k ukládání a načítání dat z kolekce, ve které jsou hodnoty prvků, které jsou obsaženy, jedinečné a slouží jako klíčové hodnoty, podle kterých jsou data automaticky řazena.|
|[multiset – třída](../standard-library/multiset-class.md)|Slouží k ukládání a načítání dat z kolekce, ve které hodnoty elementů, které nemusí být jedinečné a které slouží jako klíčové hodnoty, podle kterých jsou data automaticky řazena.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
