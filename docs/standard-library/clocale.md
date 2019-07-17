---
title: '&lt;clocale –&gt;'
ms.date: 11/04/2016
f1_keywords:
- <clocale>
helpviewer_keywords:
- clocale header
ms.assetid: 5bde3e01-cf67-4f1f-a383-447ec814d00e
ms.openlocfilehash: 624a1afdbe0e73c81a324273836eff6b89705236
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244762"
---
# <a name="ltclocalegt"></a>&lt;clocale –&gt;

Obsahuje hlavičku knihovny Standard C \<locale.h > a přidá názvy přidružené k `std` oboru názvů.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<clocale – >

**Namespace:** std

## <a name="remarks"></a>Poznámky

Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším spojením v záhlaví knihovny Standard C jsou deklarovány v `std` oboru názvů.

## <a name="constants"></a>Konstanty

```cpp
#define NULL see below
#define LC_ALL see below
#define LC_COLLATE see below
#define LC_CTYPE see below
#define LC_MONETARY see below
#define LC_NUMERIC see below
#define LC_TIME see below
```

## <a name="structures"></a>Struktury

```cpp
struct lconv;
```

## <a name="functions"></a>Funkce

```cpp
char* setlocale(int category, const char* locale);
lconv* localeconv();
```

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
