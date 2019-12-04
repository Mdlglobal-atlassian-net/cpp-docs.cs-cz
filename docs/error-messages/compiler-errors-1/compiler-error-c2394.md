---
title: Chyba kompilátoru C2394
ms.date: 11/04/2016
f1_keywords:
- C2394
helpviewer_keywords:
- C2394
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
ms.openlocfilehash: 2c8c23939298f5603b59636ede08b65acaa0f22b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744989"
---
# <a name="compiler-error-c2394"></a>Chyba kompilátoru C2394

' your_type:: operator'op ' ': CLR nebo WinRToperator není platný. Minimálně jeden parametr musí být z následujících typů: t ^ ', t ^% ', t ^ & ', kde T = ' your_type '.

Operátor v prostředí Windows Runtime nebo spravovaném typu neměl aspoň jeden parametr, jehož typ je stejný jako typ návratové hodnoty operátoru.

Následující ukázka generuje C2394:

```cpp
// C2394.cpp
// compile with: /clr /c
ref struct Y {
   static Y^ operator -(int i, char c);   // C2394

   // OK
   static Y^ operator -(Y^ hY, char c);
   // or
   static Y^ operator -(int i, Y^& rhY);
};
```
