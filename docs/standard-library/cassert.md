---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 14dda03e835ec411013b2d827bd1ccaa77f8982e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245022"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

Obsahuje hlavičku knihovny C Standard \<assert.h > a přidá názvy přidružené k `std` oboru názvů. Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším spojením v záhlaví knihovny C Standard jsou deklarovány v `std` oboru názvů.

> [!NOTE]
> \<Assert.h > nedefinuje `static_assert` – makro.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cassert>
```

## <a name="macros"></a>Makra

```cpp
#define assert(E)
```

### <a name="remarks"></a>Poznámky

`assert(E)` je jenom konstantní, pokud je definován NDEBUG kde `assert` je poslední definované nebo předefinovat, nebo *E* převést na bool vyhodnocen **true**.

## <a name="see-also"></a>Viz také:

[assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
