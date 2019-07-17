---
title: '&lt;cctype –&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cctype>
helpviewer_keywords:
- cctype header
ms.assetid: 3fd18bfd-c414-4def-bac1-c362e1fe8b71
ms.openlocfilehash: 19431d02e0742d63df058ca743fc0560131805bd
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244953"
---
# <a name="ltcctypegt"></a>&lt;cctype –&gt;

Obsahuje hlavičku knihovny Standard C \<ctype.h > a přidá názvy přidružené k `std` oboru názvů.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<cctype – >

**Namespace:** std

## <a name="remarks"></a>Poznámky

Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším spojením v záhlaví knihovny Standard C jsou deklarovány v `std` oboru názvů.

## <a name="functions"></a>Funkce

```cpp
int isalnum(int c);
int isalpha(int c);
int isblank(int c);
int iscntrl(int c);
int isdigit(int c);
int isgraph(int c);
int islower(int c);
int isprint(int c);
int ispunct(int c);
int isspace(int c);
int isupper(int c);
int isxdigit(int c);
int tolower(int c);
int toupper(int c);
```

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
