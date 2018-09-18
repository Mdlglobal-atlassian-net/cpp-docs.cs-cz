---
title: Chyba kompilátoru C2719 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2719
dev_langs:
- C++
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4423352bad520d66920a01542f592ed8022482d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054180"
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