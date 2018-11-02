---
title: treat_as_floating_point – struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: 1b7b58983032ee74ed3d88feb7325cd537e1cc2f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493857"
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point – struktura

Určuje, zda `Rep` lze považovat za typ s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Poznámky

`Rep` lze považovat za typ s plovoucí desetinnou čárkou pouze tehdy, když specializace `treat_as_floating_point<Rep>` je odvozen z [true_type](../standard-library/type-traits-typedefs.md#true_type). Třída šablony mohou být specializované pro typ definovaný uživatelem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono >

**Namespace:** std::chrono

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
