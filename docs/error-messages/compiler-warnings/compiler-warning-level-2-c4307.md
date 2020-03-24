---
title: Upozornění kompilátoru (úroveň 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: f6e06acaf43708d6c0da6d67531b6c4b9f202971
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161877"
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
