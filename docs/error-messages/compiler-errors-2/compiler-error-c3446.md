---
title: Chyba kompilátoru C3446 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3446
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a88bb77489d2596c271842e7becb0214d1af2821
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018860"
---
# <a name="compiler-error-c3446"></a>Chyba kompilátoru C3446

>"*třídy*': výchozí inicializátor členu není povolený pro člena hodnotové třídy.

V sadě Visual Studio 2015 a starší kompilátor povoleno (ale ignorovat) výchozí inicializátor členu pro člena třídy value class. Výchozí inicializace hodnotová třída vždy nula inicializuje členy. výchozí konstruktor není povolená. V sadě Visual Studio 2017 výchozí inicializátory členů vyvolat chybu kompilátoru, jak je znázorněno v tomto příkladu:

## <a name="example"></a>Příklad

Následující ukázka generuje C3446 v sadě Visual Studio 2017 a novější:

```cpp
// C3446.cpp
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer
                  // is not allowed for a member of a value class
       int j {0}; // C3446
};
```

Chcete-li chybu opravit, odeberte inicializátoru:

```cpp
// C3446b.cpp
value struct V
{
       int i;
       int j;
};
```

