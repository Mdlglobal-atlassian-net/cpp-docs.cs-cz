---
title: Chyba kompilátoru C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: d635601fbf8b36218fb47c09444f3f5d023c823e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383084"
---
# <a name="compiler-error-c2719"></a>Chyba kompilátoru C2719

'parametru': formální parametr s __declspec(align('#')) se nezarovnají

[Zarovnat](../../cpp/align-cpp.md) `__declspec` modifikátoru není povolena u parametry funkce. Zarovnání parametr funkce je řízena používá konvence volání. Další informace najdete v tématu [konvence volání](../../cpp/calling-conventions.md).

Následující ukázka generuje C2719 a ukazuje, jak ho opravit:

```
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```