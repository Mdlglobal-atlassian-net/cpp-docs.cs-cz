---
title: Upozornění kompilátoru (úroveň 1) C4180
ms.date: 11/04/2016
f1_keywords:
- C4180
helpviewer_keywords:
- C4180
ms.assetid: 40c91bd4-37f1-4d59-a4f3-d5ddab68239b
ms.openlocfilehash: 1fd56f3bcc662a326e4a263bb0a266ffc37d6ec6
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626242"
---
# <a name="compiler-warning-level-1-c4180"></a>Upozornění kompilátoru (úroveň 1) C4180

kvalifikátor aplikovaný na typ funkce nemá žádný význam; přeskočen

Kvalifikátor, jako je například **const**, se použije na typ funkce definovaný `typedef`.

## <a name="example"></a>Příklad

```cpp
// C4180.cpp
// compile with: /W1 /c
typedef int FuncType(void);

// the const qualifier cannot be applied to the
// function type FuncType
const FuncType f;   // C4180
```