---
title: Chyba kompilátoru C3272
ms.date: 11/04/2016
f1_keywords:
- C3272
helpviewer_keywords:
- C3272
ms.assetid: 7cdf254d-f207-4116-a1bf-7386f3b82a6f
ms.openlocfilehash: 3e4348dcce0cfd04234b515877d788e5330f8e4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598572"
---
# <a name="compiler-error-c3272"></a>Chyba kompilátoru C3272

'symbol': symbol vyžaduje FieldOffset, protože je členem typu typename definované pomocí StructLayout(LayoutKind::Explicit)

Když `StructLayout(LayoutKind::Explicit)` je v platnosti, musí být pole označená `FieldOffset`.

Následující ukázka generuje C3272:

```
// C3272_2.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Explicit)]
ref struct X
{
   int data_;   // C3272
   // try the following line instead
   // [FieldOffset(0)] int data_;
};
```
