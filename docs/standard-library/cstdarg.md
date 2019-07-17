---
title: '&lt;cstdarg&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdarg>
helpviewer_keywords:
- cstdarg header
ms.assetid: 639b4ef7-8408-4640-9343-41631f0ab663
ms.openlocfilehash: f8d2d3b886cfa46905e8f17f1e13b51881b80191
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244488"
---
# <a name="ltcstdarggt"></a>&lt;cstdarg&gt;

Obsahuje hlavičku knihovny C Standard \<stdarg.h > a přidá názvy přidružené k `std` oboru názvů. Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším spojením v záhlaví knihovny C Standard jsou deklarovány v `std` oboru názvů.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cstdarg>
```

## <a name="namespace-and-macros"></a>Namespace a makra

```cpp
namespace std {
    using va_list = see below;
}

#define va_arg(V, P)
#define va_copy(VDST, VSRC)
#define va_end(V)
#define va_start(V, P)
```

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
