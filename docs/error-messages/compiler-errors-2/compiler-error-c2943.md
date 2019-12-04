---
title: Chyba kompilátoru C2943
ms.date: 11/04/2016
f1_keywords:
- C2943
helpviewer_keywords:
- C2943
ms.assetid: ede6565e-d892-44c0-8eee-c69545f3be2e
ms.openlocfilehash: ac704c06ac0e455cccdb2b035d0947ae9ec04bd5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755392"
---
# <a name="compiler-error-c2943"></a>Chyba kompilátoru C2943

' class ': typ-class-ID předefinován jako argument typu šablony

Nemůžete použít obecnou třídu nebo třídu šablony namísto symbolu jako obecný argument nebo argument typu Template.

Následující ukázka generuje C2943:

```cpp
// C2943.cpp
// compile with: /c
template<class T>
class List {};

template<class List<int> > class MyList;   // C2943
template<class T >  class MyList;
```
