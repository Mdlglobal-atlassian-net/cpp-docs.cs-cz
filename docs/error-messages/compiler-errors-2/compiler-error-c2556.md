---
title: Chyba kompilátoru C2556
ms.date: 11/04/2016
f1_keywords:
- C2556
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
ms.openlocfilehash: 4a2b4dc9dcd71d518845651dee97c566b778eb0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353063"
---
# <a name="compiler-error-c2556"></a>Chyba kompilátoru C2556

'identifier': Přetížená funkce se liší pouze návratovým typem

Přetížené funkce mají rozdílné návratové typy, ale stejný seznam parametrů. Každé přetížené funkce musí mít seznam jedinečných formálních parametrů.

Následující ukázka generuje C2556:

```
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```