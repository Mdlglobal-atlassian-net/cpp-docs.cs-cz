---
title: Chyba kompilátoru C2998
ms.date: 11/04/2016
f1_keywords:
- C2998
helpviewer_keywords:
- C2998
ms.assetid: 8193d491-b5d9-4477-acb1-cf166889c070
ms.openlocfilehash: 16a3319e71d465082120cbc58e3c7c6b916be80f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499759"
---
# <a name="compiler-error-c2998"></a>Chyba kompilátoru C2998

'identifier': nemůže být definice šablony

Kompilátor nemůže zpracovat syntaxe používané v definici šablony.

Následující ukázka generuje C2998:

```
// C2998.cpp
// compile with: /c
template <class T> int x = 1018; // C2998
```