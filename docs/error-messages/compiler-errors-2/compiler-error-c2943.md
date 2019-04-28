---
title: Chyba kompilátoru C2943
ms.date: 11/04/2016
f1_keywords:
- C2943
helpviewer_keywords:
- C2943
ms.assetid: ede6565e-d892-44c0-8eee-c69545f3be2e
ms.openlocfilehash: 53340611ef92aac7c9bed30f364fed424fdfe140
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366274"
---
# <a name="compiler-error-c2943"></a>Chyba kompilátoru C2943

'class': typ třídy id předefinovalo jako argument typu šablony

Rozvrhy generic nebo šablony třídy, namísto symbol, nelze použít jako argument typu obecné nebo šablony.

Následující ukázka generuje C2943:

```
// C2943.cpp
// compile with: /c
template<class T>
class List {};

template<class List<int> > class MyList;   // C2943
template<class T >  class MyList;
```