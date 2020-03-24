---
title: Upozornění kompilátoru (úroveň 2) C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: c75d2d776537307fd34fa3a55807d303630dbeb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161969"
---
# <a name="compiler-warning-level-2-c4285"></a>Upozornění kompilátoru (úroveň 2) C4285

návratový typ pro ' identifikátor:: operator-> ' je při použití s použitím notace vpony rekurzivní.

Zadaná funkce **operator-> ()** nemůže vracet typ, pro který je definován, nebo odkaz na typ, pro který je definován.

Následující ukázka generuje C4285:

```cpp
// C4285.cpp
// compile with: /W2
class C
{
public:
    C operator->();   // C4285
   // C& operator->();  C4285, also
};

int main()
{
}
```
