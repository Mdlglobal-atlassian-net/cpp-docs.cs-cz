---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: 58ebd91fb4fa32cf31d2c49429d0445b92fe0c82
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449912"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

Obsahuje hlavičku \<standardní knihovny jazyka C vyhodnocení. h > a přidává přidružené názvy `std` do oboru názvů. Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším propojením v záhlaví standardní knihovny jazyka C jsou deklarovány v `std` oboru názvů.

> [!NOTE]
> \<Assert. h > nedefinuje `static_assert` makro.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cassert>
```

## <a name="macros"></a>Makra

```cpp
#define assert(E)
```

### <a name="remarks"></a>Poznámky

`assert(E)`je pouze konstantní, pokud je definována hodnota NDEBUG `assert` , kde je naposledy definováno nebo předefinováno, nebo *E* převedena na bool je vyhodnocena jako **true**.

## <a name="see-also"></a>Viz také:

[assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[C++Přehled standardní knihovny](../standard-library/cpp-standard-library-overview.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
