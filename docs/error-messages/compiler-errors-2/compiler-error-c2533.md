---
title: Chyba kompilátoru C2533 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2533
dev_langs:
- C++
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 528b78e71713725907a9f0e2bd06cec1a8c62e67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045403"
---
# <a name="compiler-error-c2533"></a>Chyba kompilátoru C2533

'identifier': konstruktory není povolený návratový typ.

Konstruktor nemůže mít návratový typ (včetně `void` návratový typ).

Běžné příčiny této chyby je chybí středník mezi koncem definice třídy a první implementaci konstruktoru. Kompilátor považuje definici návratový typ funkce konstruktoru třídy a generuje C2533.

Následující ukázka generuje C2533 a ukazuje, jak ho opravit:

```
// C2533.cpp
// compile with: /c
class X {
public:
   X();
};

int X::X() {}   // C2533 - constructor return type not allowed
X::X() {}   // OK - fix by using no return type
```