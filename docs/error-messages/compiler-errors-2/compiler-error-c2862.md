---
title: Chyba kompilátoru C2862
ms.date: 11/04/2016
f1_keywords:
- C2862
helpviewer_keywords:
- C2862
ms.assetid: c04d8499-b799-48a1-9fb4-7902a0b0ac8e
ms.openlocfilehash: a3e2dba20c5283d87b6e98c2f8c9aba83c2d3cb9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227686"
---
# <a name="compiler-error-c2862"></a>Chyba kompilátoru C2862

'rozhraní': rozhraní může mít pouze veřejné členy

Chráněné a soukromým členům se dá přistupovat jenom ze jiné členské funkce. Tyto členy jsou žádné použití v rozhraní, protože neposkytují implementace pro kterýkoli z jejích členů.

Následující ukázka vygeneruje C2862:

```
// C2862.cpp
// compile with: /c
#include <unknwn.h>

[object, uuid="60719E20-EF37-11D1-978D-0000F805D73B"]
__interface IMyInterface {
   HRESULT mf1(void);   // OK
protected:
   HRESULT mf2(int *b);   // C2862
private:
   HRESULT mf3(int *c);   // C2862
};
```