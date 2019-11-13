---
title: Upozornění kompilátoru (úroveň 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: b5566bca22c328328a49e82268b96e8ec0fedc95
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052056"
---
# <a name="compiler-warning-level-2-c4307"></a>Upozornění kompilátoru (úroveň 2) C4307

' operator ': přetečení celočíselné konstanty

Operátor se používá ve výrazu, jehož výsledkem je celočíselná konstanta, která má přetečení místa, které je pro něj přiděleno. Pro konstantu možná budete muset použít větší typ. **Podepsaný int** má menší hodnotu, než je `unsigned int`, protože **signed int** používá jeden bit k reprezentaci.

Následující ukázka generuje C4307:

```cpp
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```