---
title: '&lt;typeindex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <typeindex>
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
ms.openlocfilehash: 237356a0862ec3fc591264b482b23e62ef2c51cb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455065"
---
# <a name="lttypeindexgt"></a>&lt;typeindex&gt;

Zahrňte standardní hlavičku \<typeindex > k definování třídy a funkce, která podporuje indexování objektů třídy [type_info](../cpp/type-info-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
#include <typeindex>
```

## <a name="remarks"></a>Poznámky

[Struktura hash](../standard-library/hash-structure.md) definuje `hash function` , který je vhodný pro mapování hodnot typu [type_index](../standard-library/type-index-class.md) na distribuci hodnot indexu.

Třída zalomí ukazatel `type_info` na objekt, který vám pomůže při indexování. `type_index`

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
