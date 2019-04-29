---
title: Chyba kompilátoru C2612
ms.date: 11/04/2016
f1_keywords:
- C2612
helpviewer_keywords:
- C2612
ms.assetid: 6faacfd6-4455-41a2-808e-0f6799f84d6d
ms.openlocfilehash: b2d4888c1be39c4f48f0ca674426c7af612b9bb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379022"
---
# <a name="compiler-error-c2612"></a>Chyba kompilátoru C2612

na konci 'char' neplatné v seznamu inicializátorů base/member

Znak se objeví po poslední základní nebo členský v seznamu inicializátorů.

Následující ukázka generuje C2612:

```
// C2612.cpp
class A {
public:
   int i;
   A( int ia ) : i( ia ) + {};   // C2612
};
```