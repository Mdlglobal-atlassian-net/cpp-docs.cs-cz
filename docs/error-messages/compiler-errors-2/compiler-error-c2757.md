---
title: Compiler Error C2757
ms.date: 11/04/2016
f1_keywords:
- C2757
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
ms.openlocfilehash: 98b43a2f3c0888fc385226cd80889b9911c84690
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227909"
---
# <a name="compiler-error-c2757"></a>Compiler Error C2757

'symbol': symbol s tímto názvem už existuje, a proto nelze použít tento název jako název oboru názvů

Symbol použitý v aktuální kompilaci jako identifikátor oboru názvů je již používán v odkazovaném sestavení.

Následující ukázka generuje C2757:

```
// C2757a.cpp
// compile with: /clr /LD
public ref class Nes {};
```

a pak,

```
// C2757b.cpp
// compile with: /clr /c
#using <C2757a.dll>

namespace Nes {    // C2757
// try the following line instead
// namespace Nes2 {
   public ref class X {};
}
```
