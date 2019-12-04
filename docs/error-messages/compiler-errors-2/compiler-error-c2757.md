---
title: Chyba kompilátoru C2757
ms.date: 11/04/2016
f1_keywords:
- C2757
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
ms.openlocfilehash: a9f4661495e0fa5219a517b6f6ca410323a77269
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759526"
---
# <a name="compiler-error-c2757"></a>Chyba kompilátoru C2757

symbol: symbol s tímto názvem už existuje, takže tento název nejde použít jako název oboru názvů.

Symbol použitý v aktuální kompilaci jako identifikátor oboru názvů je již používán v odkazovaném sestavení.

Následující ukázka generuje C2757:

```cpp
// C2757a.cpp
// compile with: /clr /LD
public ref class Nes {};
```

A potom

```cpp
// C2757b.cpp
// compile with: /clr /c
#using <C2757a.dll>

namespace Nes {    // C2757
// try the following line instead
// namespace Nes2 {
   public ref class X {};
}
```
