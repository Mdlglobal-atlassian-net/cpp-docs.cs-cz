---
title: '&lt;csetjmp&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csetjmp>
helpviewer_keywords:
- csetjmp header
ms.assetid: 8f21fddd-5e9b-4219-a848-581cdd3569d9
ms.openlocfilehash: 8f3a1a622776d5dd2ef3d22aaa3436933c5a7137
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452399"
---
# <a name="ltcsetjmpgt"></a>&lt;csetjmp&gt;

Obsahuje hlavičku \<standardní knihovny jazyka C setjmp. h > a přidává přidružené názvy `std` do oboru názvů.

## <a name="syntax"></a>Syntaxe

```cpp
#include <csetjmp>

using jmp_buf = see below;
```

## <a name="functions"></a>Funkce

```cpp
[[noreturn]] void longjmp(jmp_buf env, int val);
```

## <a name="macros"></a>Makra

```cpp
#define setjmp(env)
```

## <a name="remarks"></a>Poznámky

Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším propojením v hlavičce standardní knihovny jazyka C jsou deklarovány v `std` oboru názvů.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[C++Přehled standardní knihovny](../standard-library/cpp-standard-library-overview.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
