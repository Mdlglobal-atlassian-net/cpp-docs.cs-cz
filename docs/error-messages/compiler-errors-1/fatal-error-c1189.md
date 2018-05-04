---
title: Závažná chyba C1189 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C1189
dev_langs:
- C++
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b49f227b5fda20ab0ba202d3d7eca99492509b35
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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