---
title: Závažná chyba C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 2217b865109cc48151e4e96b2d38b88764c0c64f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203625"
---
# <a name="fatal-error-c1189"></a>Závažná chyba C1189

> **chyba\#:** *uživatel zadal chybovou zprávu* .

## <a name="remarks"></a>Poznámky

C1189 se generuje pomocí direktivy `#error`. Text chybové zprávy určuje vývojář, který obsahuje kód direktivy. Další informace najdete v tématu [direktiva #error (CC++/)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C1189. V ukázce vývojář vydá vlastní chybovou zprávu, protože `_WIN32` identifikátor není definován:

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Viz také

[#define – direktiva (C++)](../../preprocessor/hash-define-directive-c-cpp.md)
