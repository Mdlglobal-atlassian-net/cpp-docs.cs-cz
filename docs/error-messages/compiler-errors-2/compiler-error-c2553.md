---
title: Chyba kompilátoru C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: aa3e97d576e994878ab5b080363c4c09b79f42ed
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756783"
---
# <a name="compiler-error-c2553"></a>Chyba kompilátoru C2553

' base_function ': návratový typ přepisující virtuální funkce se liší od ' override_function '

Funkce v odvozené třídě se pokusila přepsat virtuální funkci v základní třídě, ale funkce odvozené třídy neobsahovala stejný návratový typ jako funkce základní třídy.  Signatura funkce přepsání se musí shodovat s signaturou funkce, která je přepsána.

Následující ukázka generuje C2553:

```cpp
// C2553.cpp
// compile with: /clr /c
ref struct C {
   virtual void f();
};

ref struct D : C {
   virtual int f() override ;   // C2553

   // try the following line instead
   // virtual void f() override;
};
```
