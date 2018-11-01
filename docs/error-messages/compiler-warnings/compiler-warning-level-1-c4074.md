---
title: Kompilátor upozornění (úroveň 1) C4074
ms.date: 11/04/2016
f1_keywords:
- C4074
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
ms.openlocfilehash: d9b0259e95198396d8c34ca43781045248e22ad9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665562"
---
# <a name="compiler-warning-level-1-c4074"></a>Kompilátor upozornění (úroveň 1) C4074

Inicializátory jsou vložené do vyhrazené oblasti inicializace

Inicializační oblasti kompilátoru, který je určený [init_seg – #pragma](../../preprocessor/init-seg.md), si vyhradil Microsoft. Kód v této oblasti mohou být provedeny před inicializace knihovny run-time C.

Následující ukázka generuje C4074:

```
// C4074.cpp
// compile with: /W1
#pragma init_seg( compiler )   // C4074

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```