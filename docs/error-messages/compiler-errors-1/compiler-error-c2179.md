---
title: Chyba kompilátoru C2179 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2179
dev_langs:
- C++
helpviewer_keywords:
- C2179
ms.assetid: f929bfc6-3964-4e54-87d6-7529b9b6c0b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b56437dfe5b9be75ae93dea46890d408ea2dc66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111626"
---
# <a name="compiler-error-c2179"></a>Chyba kompilátoru C2179

'type': argument atributu nemůže používat parametry typu

Parametr obecného typu se vyřeší v době běhu. Parametr atributu však musí být vyřešené v době kompilace. Parametr obecného typu, proto nelze použít jako argument pro atribut.

## <a name="example"></a>Příklad

Následující ukázka generuje C2179.

```
// C2179.cpp
// compile with: /clr
using namespace System;

public ref struct Attr : Attribute {
   Attr(Type ^ a) {
      x = a;
   }

   Type ^ x;
};

ref struct G {};

generic<typename T>
public ref class Z {
public:
   Type ^ d;
   [Attr(T::typeid)]   // C2179
   // try the following line instead
   // [Attr(G::typeid)]
   T t;
};
```