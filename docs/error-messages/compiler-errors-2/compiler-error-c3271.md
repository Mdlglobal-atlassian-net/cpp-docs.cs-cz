---
title: Chyba kompilátoru C3271
ms.date: 11/04/2016
f1_keywords:
- C3271
helpviewer_keywords:
- C3271
ms.assetid: 16d8bd1d-2e30-4c6a-a07f-0c4f3342fab5
ms.openlocfilehash: f94ef54408584e40dc406935e36053352ecf38e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651855"
---
# <a name="compiler-error-c3271"></a>Chyba kompilátoru C3271

'member': Neplatná hodnota 'value' pro atribut FieldOffset

Byl předán záporného čísla **FieldOffset** atribut.

Následující ukázka generuje C3271:

```
// C3271.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Explicit)]
value class MyStruct1 {
   public: [FieldOffset(0)] int a;
   public: [FieldOffset(-1)] long b;   // C3271
};
```
