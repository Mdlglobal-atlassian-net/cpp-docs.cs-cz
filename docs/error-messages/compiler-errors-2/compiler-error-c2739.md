---
title: Compiler Error C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: f7e7b20f64c8975e747fe84138cbcb18c3fd14fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258020"
---
# <a name="compiler-error-c2739"></a>Compiler Error C2739

'number': explicitní spravované nebo rozměry pole WinRT musí být mezi 1 a 32

Rozměr pole nebyl od 1 do 32.

Následující ukázka generuje C2739 a ukazuje, jak ho opravit:

```
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```