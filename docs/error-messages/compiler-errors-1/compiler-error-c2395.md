---
title: Compiler Error C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: dd3bd922e2bfa61da2da87d368bb4b28237161f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303652"
---
# <a name="compiler-error-c2395"></a>Compiler Error C2395

"your_type::operator'op": CLR WinRT operátor nebo není platný. Nejméně jeden parametr musí být z následujících typů: Nejde ", nejde %', 'T &", nejde ^ ", nejde ^ %", nejde ^ & ", kde T ="your_type"

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