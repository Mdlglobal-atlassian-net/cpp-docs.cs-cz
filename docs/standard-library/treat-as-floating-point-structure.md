---
title: treat_as_floating_point – struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: add69179b23a953a937458cbfa55254b21c5ea37
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685115"
---
# <a name="treat_as_floating_point-structure"></a>treat_as_floating_point – struktura

Určuje, zda `Rep` lze považovat za typ s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Poznámky

`Rep` lze považovat za typ s plovoucí desetinnou čárkou pouze v případě, že je `treat_as_floating_point<Rep>` specializace odvozena z [true_type](../standard-library/type-traits-typedefs.md#true_type). Šablona třídy může být specializovaná pro uživatelsky definovaný typ.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono >

**Obor názvů:** std:: chrono

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[\<chrono >](../standard-library/chrono.md)
