---
title: Upozornění kompilátoru (úroveň 1) C4003
ms.date: 11/04/2016
f1_keywords:
- C4003
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
ms.openlocfilehash: 4adbffe3220060ee9d43f01cf94628f85d3991cc
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627390"
---
# <a name="compiler-warning-level-1-c4003"></a>Upozornění kompilátoru (úroveň 1) C4003

pro makro Identifier není dostatečný počet skutečných parametrů.

Počet formálních parametrů v definici makra překračuje počet skutečných parametrů v makru. Rozšíření makra nahrazuje prázdný text pro chybějící parametry.

Následující ukázka generuje C4003:

```cpp
// C4003.cpp
// compile with: /WX
#define test(a,b) (a+b)

int main()
{
   int a = 1;
   int b = 2;
   a = test(b);   // C4003
   // try..
   a = test(a,b);
}
```