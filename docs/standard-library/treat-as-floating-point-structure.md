---
title: treat_as_floating_point – struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: 4cf3ac5be972d8636f1d3dbda3b195f4012517be
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459884"
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point – struktura

Určuje, `Rep` zda lze považovat za typ s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Poznámky

`Rep`může být považována za typ s plovoucí desetinnou čárkou pouze `treat_as_floating_point<Rep>` v případě, že je specializace odvozena od [true_type](../standard-library/type-traits-typedefs.md#true_type). Třída šablony může být specializovaná pro uživatelsky definovaný typ.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<Chrono >

**Obor názvů:** std:: chrono

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
