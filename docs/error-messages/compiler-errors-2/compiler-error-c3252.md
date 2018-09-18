---
title: Chyba kompilátoru C3252 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3252
dev_langs:
- C++
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70a38090bcbe1a984e643d6d995abe2c79339163
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080620"
---
# <a name="compiler-error-c3252"></a>Chyba kompilátoru C3252

"metoda": nejde snížit přístupnost virtuální metody ve spravované nebo typ WinRT

Třídu, která implementuje virtuální metodou ze základní třídy nebo jakoukoli metodu z rozhraní nemůže omezovat přístup této metody.

Všimněte si, že všechny metody v rozhraní veřejná.

Následující ukázka generuje C3252 a ukazuje, jak ho opravit:

```
// C3252.cpp
// compile with: /clr /c
ref class A {
public:
   virtual void f1() {}
};

ref class B : public A {
// To fix, uncomment the following line:
// public:
   virtual void f1() override sealed {}   // C3252, make this method public
};
```