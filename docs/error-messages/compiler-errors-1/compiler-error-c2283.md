---
title: Chyba kompilátoru C2283
ms.date: 11/04/2016
f1_keywords:
- C2283
helpviewer_keywords:
- C2283
ms.assetid: 8a5b3175-b480-4598-a1f7-0b50504c5caa
ms.openlocfilehash: 1113236680241a80c462e382c8c9c7de342b5463
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388745"
---
# <a name="compiler-error-c2283"></a>Chyba kompilátoru C2283

'identifier': specifikátor pure nebo abstract override není povolený pro nepojmenované struktury

Členská funkce Nepojmenovaná třída nebo struktura je deklarována s specifikátor pure, což není povoleno.

Následující ukázka generuje C2283:

```
// C2283.cpp
// compile with: /c
struct {
   virtual void func() = 0;   // C2283
};
struct T {
   virtual void func() = 0;   // OK
};
```