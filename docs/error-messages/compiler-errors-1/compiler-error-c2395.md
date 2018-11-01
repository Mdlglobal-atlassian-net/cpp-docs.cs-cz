---
title: Chyba kompilátoru C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: dd3bd922e2bfa61da2da87d368bb4b28237161f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599834"
---
# <a name="compiler-error-c2395"></a>Chyba kompilátoru C2395

"your_type::operator'op'': CLR nebo WinRT operátor není platný. Nejméně jeden parametr musí být z následujících typů: nejde ", nejde %', 'T &", nejde ^ ", nejde ^ %", nejde ^ & ", kde T ="your_type"

Operátor v prostředí Windows Runtime nebo spravovaný typ neměl nejmíň jeden parametr, jehož typ je stejný jako typ vrácené hodnoty operátor.

Následující ukázka generuje C2395 a ukazuje, jak ho opravit:

```
// C2395.cpp
// compile with: /clr /c
value struct V {
   static V operator *(int i, char c);   // C2395

   // OK
   static V operator *(V v, char c);
   // or
   static V operator *(int i, V& rv);
};
```