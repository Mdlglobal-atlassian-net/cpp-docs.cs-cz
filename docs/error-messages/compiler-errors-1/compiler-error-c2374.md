---
title: Chyba kompilátoru C2374
ms.date: 11/04/2016
f1_keywords:
- C2374
helpviewer_keywords:
- C2374
ms.assetid: 73b51965-e91c-4e21-9732-f71c1449d22e
ms.openlocfilehash: 44f2d9d8c80af2111e7c63d976ef39cfa4809e48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338802"
---
# <a name="compiler-error-c2374"></a>Chyba kompilátoru C2374

'identifier': předefinování; Vícenásobná inicializace

Identifikátor je inicializovat více než jednou.

Následující ukázka generuje C2374:

```
// C2374.cpp
// compile with: /c
int i = 0;
int i = 1;   // C2374
int j = 1;   // OK
```