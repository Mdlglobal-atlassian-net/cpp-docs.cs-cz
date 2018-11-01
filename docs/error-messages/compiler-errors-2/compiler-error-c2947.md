---
title: Chyba kompilátoru C2947
ms.date: 11/04/2016
f1_keywords:
- C2947
helpviewer_keywords:
- C2947
ms.assetid: 6c056f62-ec90-4883-8a67-aeeb6ec13546
ms.openlocfilehash: 3738c257192134eedb8554b0d875023862441416
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566752"
---
# <a name="compiler-error-c2947"></a>Chyba kompilátoru C2947

byl očekáván ' >' k ukončení konstrukce, nalezen 'syntaxe:

Rozvrhy generic nebo šablony seznamu argumentů nemusí po ukončení správně.

C2947 mohou být generovány chyby syntaxe.

Následující ukázka generuje C2947:

```
// C2947.cpp
// compile with: /c
template <typename T>=   // C2947
// try the following line instead
// template <typename T>
struct A {};
```