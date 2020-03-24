---
title: Upozornění kompilátoru (úroveň 2) C4756
ms.date: 11/04/2016
f1_keywords:
- C4756
helpviewer_keywords:
- C4756
ms.assetid: 5a16df83-6b82-4619-83bd-319af4ef1d1d
ms.openlocfilehash: 5a48620a2cbc80379ea7a6787783e98dac1ffa9b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161721"
---
# <a name="compiler-warning-level-2-c4756"></a>Upozornění kompilátoru (úroveň 2) C4756

přetečení v konstantní aritmetické konstantě

Kompilátor vygeneroval výjimku při provádění konstantní aritmetické operace během kompilace.

Následující ukázka generuje C4756:

```cpp
// C4756.cpp
// compile with: /W2 /Od
int main()
{
   float f = 1e100+1e100;   // C4756
}
```
