---
title: Upozornění kompilátoru (úroveň 1) C4074
ms.date: 11/04/2016
f1_keywords:
- C4074
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
ms.openlocfilehash: 7a11112962872788df855bfc63b869193188fab9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164076"
---
# <a name="compiler-warning-level-1-c4074"></a>Upozornění kompilátoru (úroveň 1) C4074

Inicializátory jsou vložené v oblasti inicializace rezervované kompilátorem.

Inicializační oblast kompilátoru, která je určena [#pragma init_seg](../../preprocessor/init-seg.md), je vyhrazena společností Microsoft. Kód v této oblasti může být proveden před inicializací knihovny run-time jazyka C.

Následující ukázka generuje C4074:

```cpp
// C4074.cpp
// compile with: /W1
#pragma init_seg( compiler )   // C4074

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```
