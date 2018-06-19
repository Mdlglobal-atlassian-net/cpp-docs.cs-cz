---
title: Závažná chyba C1189 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1189
dev_langs:
- C++
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 051b7eb965526d12311dfacaeae7a00e4fbe4e75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199791"
---
# <a name="fatal-error-c1189"></a>Závažná chyba C1189

> **\#Chyba:** *uživatelem dodaný chybová zpráva*

## <a name="remarks"></a>Poznámky

Je generován C1189 `#error` – direktiva. Vývojáři, který kódy direktiva Určuje text chybové zprávy. Další informace najdete v tématu [#error – direktiva (C/C++)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C1189. V ukázce vývojář problémy vlastní chybové zprávy, protože `_WIN32` identifikátor není definován:

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Viz také

[#define – direktiva (C++)](../../preprocessor/hash-define-directive-c-cpp.md)