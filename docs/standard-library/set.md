---
title: '&lt;set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <set>
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
ms.openlocfilehash: 633571f00cfe761b687e9b76624029f57ab6043e
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523907"
---
# <a name="ltsetgt"></a>&lt;set&gt;

Definuje kontejner šablony třídy sady a multiset a jejich podpůrných šablon.

## <a name="syntax"></a>Syntaxe

```cpp
#include <set>
```

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|Nastavit verzi|Multiset – verze|Popis|
|-----------------|----------------------|-----------------|
|[Operator! = (set)](../standard-library/set-operators.md#op_neq)|[Operator! = (multiset)](../standard-library/set-operators.md#op_neq)|Testuje, zda sada nebo multiset – objekt na levé straně operátoru není roven set nebo multiset – objekt na pravé straně.|
|[Operator < (set)](../standard-library/set-operators.md#op_lt)|[Operator < (multiset)](../standard-library/set-operators.md#op_lt_multiset)|Testuje, zda sada nebo multiset – objekt na levé straně operátoru menší než sada nebo multiset – objekt na pravé straně.|
|[Operator < = (set)](../standard-library/set-operators.md#op_lt_eq)|[operátor\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|Testuje, zda sada nebo multiset – objekt na levé straně operátoru menší než nebo rovna hodnotě set nebo multiset – objekt na pravé straně.|
|[Operator == (set)](../standard-library/set-operators.md#op_eq_eq)|[operator== (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|Testuje, zda sada nebo multiset – objekt na levé straně operátoru roven set nebo multiset – objekt na pravé straně.|
|[Operator > (set)](../standard-library/set-operators.md#op_gt)|[Operator > (multiset)](../standard-library/set-operators.md#op_gt_multiset)|Testuje, zda sada nebo multiset – objekt na levé straně operátoru větší než sada nebo multiset – objekt na pravé straně.|
|[Operator > = (set)](../standard-library/set-operators.md#op_gt_eq)|[operator>= (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|Testuje, zda sada nebo multiset – objekt na levé straně operátoru větší než nebo rovna hodnotě set nebo multiset – objekt na pravé straně.|

### <a name="specialized-template-functions"></a>Specializované funkce šablon

|Nastavit verzi|Multiset – verze|Popis|
|-----------------|----------------------|-----------------|
|[Prohození](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|Vymění prvky dvou sad nebo multisets.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[set – třída](../standard-library/set-class.md)|Používá pro ukládání a načítání dat z kolekce, ve kterém hodnoty elementů obsažených jsou jedinečné a slouží jako klíčové hodnoty, podle kterých jsou data automaticky uspořádávána.|
|[multiset – třída](../standard-library/multiset-class.md)|Používá pro ukládání a načítání dat z kolekce, ve kterém hodnoty elementů obsažených nemusí být jedinečný a ve které slouží jako klíčové hodnoty, podle kterých jsou data automaticky uspořádávána.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
