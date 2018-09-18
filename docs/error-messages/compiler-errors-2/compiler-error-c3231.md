---
title: Chyba kompilátoru C3231 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3231
dev_langs:
- C++
helpviewer_keywords:
- C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57727fbd71314201ec76119d37ab9c73b01d471d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097308"
---
# <a name="compiler-error-c3231"></a>Chyba kompilátoru C3231

'arg': argument typu šablony nelze použít parametr obecného typu

Šablony jsou vytvořeny v době kompilace, ale instance se vytvářejí obecné typy v době běhu. Proto není možné generovat obecný kód, který lze volat šablony, protože šablona se nedá vytvořit instance v době běhu, když se nakonec označuje obecného typu.

Následující ukázka generuje C3231:

```
// C3231.cpp
// compile with: /clr /LD
template <class T> class A;

generic <class T>
ref class C {
   void f() {
      A<T> a;   // C3231
   }
};
```