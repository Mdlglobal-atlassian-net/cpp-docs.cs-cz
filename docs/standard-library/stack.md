---
title: '&lt;vrstvě&gt;'
ms.date: 11/04/2016
f1_keywords:
- <stack>
helpviewer_keywords:
- stack, stack header
- stack header
ms.assetid: 89d8999e-c773-46f2-86c1-4b3b5aedb1c1
ms.openlocfilehash: 8a31ccd553638b9b548db89a191da40bc513a05f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453777"
---
# <a name="ltstackgt"></a>&lt;vrstvě&gt;

Definuje zásobník tříd šablon a dvě podpůrné šablony.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> zásobníku

**Obor názvů:** std

> [!NOTE]
> Knihovna > `#include <initializer_list>` Stack také používá příkaz. \<

## <a name="members"></a>Členové

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/stack-operators.md#op_neq)|Testuje, zda objekt stack na levé straně operátoru není roven objektu zásobníku na pravé straně.|
|[operátor <](../standard-library/stack-operators.md#op_lt)|Testuje, zda je objekt zásobníku na levé straně operátoru menší než objekt zásobníku na pravé straně.|
|[podnikatel\<=](../standard-library/stack-operators.md#op_lt_eq)|Testuje, zda je objekt zásobníku na levé straně operátoru menší než nebo roven objektu zásobníku na pravé straně.|
|[operator==](../standard-library/stack-operators.md#op_eq_eq)|Testuje, zda je objekt zásobníku na levé straně operátoru roven objektu zásobníku na pravé straně.|
|[operátor >](../standard-library/stack-operators.md#op_gt)|Testuje, zda je objekt zásobníku na levé straně operátoru větší než objekt zásobníku na pravé straně.|
|[operator>=](../standard-library/stack-operators.md#op_gt_eq)|Testuje, zda je objekt zásobníku na levé straně operátoru větší než nebo roven objektu zásobníku na pravé straně.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[swap]()||

### <a name="classes"></a>Třídy

|||
|-|-|
|[stack – třída](../standard-library/stack-class.md)|Třída adaptéru pro kontejner šablon, která poskytuje omezení funkcí omezující přístup k prvku, který byl naposledy přidán k některému základnímu typu kontejneru.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
