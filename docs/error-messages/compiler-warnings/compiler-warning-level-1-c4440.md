---
title: Kompilátor upozornění (úroveň 1) C4440
ms.date: 11/04/2016
f1_keywords:
- C4440
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
ms.openlocfilehash: ccd7c14cbd078d4740795d25ad772bdc78840a60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408274"
---
# <a name="compiler-warning-level-1-c4440"></a>Kompilátor upozornění (úroveň 1) C4440

Předefinování konvence volání z: 'calling_convention1' chcete ignorovat calling_convention2

Pokus o změnit konvence volání byl ignorován.

Následující ukázka generuje C4440:

```
// C4440.cpp
// compile with: /W1 /LD /clr
typedef void __clrcall F();
typedef F __cdecl *PFV;   // C4440
```