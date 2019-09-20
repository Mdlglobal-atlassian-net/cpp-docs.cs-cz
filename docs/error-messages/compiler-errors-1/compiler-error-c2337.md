---
title: Chyba kompilátoru C2337
ms.date: 09/19/2019
f1_keywords:
- C2337
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
ms.openlocfilehash: bf9b3e782804add13aeaef0e6672d2dd66d193be
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158778"
---
# <a name="compiler-error-c2337"></a>Chyba kompilátoru C2337

> *atribut-Name*: atribut se nenašel.

Váš kód používá atribut, který není v tomto kontextu podporován. Nebo, atribut není v této verzi kompilátoru k dispozici. Tento problém vyřešíte odebráním nepodporovaného atributu.

Následující ukázka generuje C2337:

```cpp
// C2337.cpp
// compile with: /c
[emitidl];
[module(name="x")];
[grasshopper]   // C2337, not a supported attribute
class a{};
```
