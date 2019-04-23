---
title: Chyba kompilátoru C2674
ms.date: 11/04/2016
f1_keywords:
- C2674
helpviewer_keywords:
- C2674
ms.assetid: 7cbd70d8-d992-44d7-a5cb-dd8cf9c759d2
ms.openlocfilehash: f29371f2987eaae1aa7a56c9f4eb56c332fdf31c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779138"
---
# <a name="compiler-error-c2674"></a>Chyba kompilátoru C2674

Obecná deklarace není v tomto kontextu povolená.

Obecný byl deklarován nesprávně. Další informace najdete v tématu [obecných typů](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2674.

```
// C2674.cpp
// compile with: /clr /c
void F(generic <class T> ref class R1);   // C2674
generic <class T> ref class R2 {};   // OK
```