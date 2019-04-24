---
title: Závažná chyba C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 06d42316a0109ac063bba43cefebd9aab71c2e72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62229056"
---
# <a name="fatal-error-c1189"></a>Závažná chyba C1189

> **\#Chyba:** *uživatelem zadaná chybová zpráva*

## <a name="remarks"></a>Poznámky

Je generován C1189 `#error` směrnice. Vývojář, který kódů direktiva Určuje text chybové zprávy. Další informace najdete v tématu [#error – direktiva (C++)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C1189. V ukázce vývojář vydá vlastní chybovou zprávu vzhledem k tomu, `_WIN32` identifikátor není definován:

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Viz také:

[#define – direktiva (C++)](../../preprocessor/hash-define-directive-c-cpp.md)