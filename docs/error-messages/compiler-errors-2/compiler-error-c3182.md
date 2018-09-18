---
title: Chyba kompilátoru C3182 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3182
dev_langs:
- C++
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 722f95b41f9f5ec467af25ccf927631590f90e45
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110212"
---
# <a name="compiler-error-c3182"></a>Chyba kompilátoru C3182

'class': deklaraci using-declaration nebo přístup člena je neplatný v rámci spravované nebo WinRTtype

A [pomocí](../../cpp/using-declaration.md) deklarace není platný v rámci všech formy spravované třídy.

Následující ukázka generuje C3182 a ukazuje, jak ho opravit.

```
// C3182a.cpp
// compile with: /clr /c
ref struct B {
   void mf(int) {
   }
};

ref struct D : B {
   using B::mf;   // C3182, delete to resolve
   void mf(char) {
   }
};
```
