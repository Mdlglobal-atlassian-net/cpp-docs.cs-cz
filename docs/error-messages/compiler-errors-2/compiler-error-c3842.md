---
title: Chyba kompilátoru C3842 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3842
dev_langs:
- C++
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8db69ce3af28ed5878c43775b2c33542e5c817d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055519"
---
# <a name="compiler-error-c3842"></a>Chyba kompilátoru C3842

'function': 'const' a 'volatile: kvalifikátory pro členské funkce WinRT nebo spravované typy nejsou podporovány.

[Const](../../cpp/const-cpp.md) a [volatile](../../cpp/volatile-cpp.md) členských funkcí třídy Windows Runtime nebo spravované typy se nepodporují.

Následující ukázka generuje C3842:

```
// C3842a.cpp
// compile with: /clr /c
public ref struct A {
   void f() const {}   // C3842
   void f() volatile {}   // C3842

   void f() {}
};
```