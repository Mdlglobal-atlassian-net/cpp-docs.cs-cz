---
title: Upozornění kompilátoru (úroveň 1) C4618
ms.date: 11/04/2016
f1_keywords:
- C4618
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
ms.openlocfilehash: 5e6c945932699119f97bca2d3d118a03665f6f9f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185877"
---
# <a name="compiler-warning-level-1-c4618"></a>Upozornění kompilátoru (úroveň 1) C4618

parametry pragma zahrnovaly prázdný řetězec; Direktiva pragma se ignoruje.

Jako argument pro **#pragma**byl zadán řetězec s hodnotou null.

Direktiva pragma byla zpracována bez argumentu.

Následující ukázka generuje C4618:

```cpp
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```
