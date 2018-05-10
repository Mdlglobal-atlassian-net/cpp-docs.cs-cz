---
title: treat_as_floating_point – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
dev_langs:
- C++
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96687959ce4fdd7b5431611a64b878cf05f855ab
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point – struktura

Určuje, zda `Rep` lze zacházet jako s plovoucí desetinnou čárkou typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Poznámky

`Rep` lze zacházet jako s plovoucí desetinnou čárkou typ pouze tehdy, když specializace `treat_as_floating_point<Rep>` je odvozený od [true_type –](../standard-library/type-traits-typedefs.md#true_type). Šablony třídy můžete specializované pro uživatelem definovaný typ.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<typu chrono >

**Namespace:** std::chrono

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
