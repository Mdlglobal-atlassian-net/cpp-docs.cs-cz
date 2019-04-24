---
title: Chyba kompilátoru C3446
ms.date: 07/21/2017
f1_keywords:
- C3446
helpviewer_keywords:
- C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
ms.openlocfilehash: 8145e0cdd97022ebdcc1a7ce38c8860a005945b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182441"
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

