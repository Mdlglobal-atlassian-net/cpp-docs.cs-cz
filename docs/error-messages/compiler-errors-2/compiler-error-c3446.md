---
title: Chyba kompilátoru C3446
ms.date: 07/21/2017
f1_keywords:
- C3446
helpviewer_keywords:
- C3446
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
ms.openlocfilehash: 0f9ebd274a90dffe00b0e8375cc374acf46e7a08
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447117"
---
# <a name="compiler-error-c3446"></a>Chyba kompilátoru C3446

>*Class*: výchozí inicializátor členů není povolený pro člena hodnotové třídy.

V aplikaci Visual Studio 2015 a starší kompilátor povolil (ale ignoruje) výchozí inicializátor členu pro člena hodnotové třídy. Výchozí inicializace třídy hodnot vždy nula – inicializuje členy; výchozí konstruktor není povolený. V aplikaci Visual Studio 2017 vyvolají výchozí Inicializátory členů chybu kompilátoru, jak je znázorněno v následujícím příkladu:

## <a name="example"></a>Příklad

Následující ukázka generuje C3446 v aplikaci Visual Studio 2017 a novější:

```cpp
// C3446.cpp
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer
                  // is not allowed for a member of a value class
       int j {0}; // C3446
};
```

Chcete-li chybu opravit, odeberte inicializátor:

```cpp
// C3446b.cpp
value struct V
{
       int i;
       int j;
};
```

