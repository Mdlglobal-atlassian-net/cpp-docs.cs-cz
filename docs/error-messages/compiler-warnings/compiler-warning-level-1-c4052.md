---
title: Kompilátor upozornění (úroveň 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4052
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: c7d2a603b7ec97889b075c7a67e5b8439ad487af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599625"
---
# <a name="compiler-warning-level-1-c4052"></a>Kompilátor upozornění (úroveň 1) C4052

deklarace funkcí odlišná jedna obsahuje argumenty proměnných

Jedna deklarace funkce obsahuje argumenty proměnných. Ignorováno.

Následující ukázka generuje C4052:

```
// C4052.c
// compile with: /W4 /c
int f();
int f(int i, ...);   // C4052
```