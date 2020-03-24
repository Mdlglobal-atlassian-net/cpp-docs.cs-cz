---
title: Upozornění kompilátoru (úroveň 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: e2e1781bf4c1b9ac0ee29d0b5900daa6cfe94b45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199768"
---
# <a name="compiler-warning-level-1-c4269"></a>Upozornění kompilátoru (úroveň 1) C4269

' identifier ': Automatická data const inicializovaná s výchozím konstruktorem generovaným kompilátorem vytváří nespolehlivé výsledky

**Konstantní** Automatická instance netriviální třídy je inicializována s výchozím konstruktorem generovaným kompilátorem.

## <a name="example"></a>Příklad

```cpp
// C4269.cpp
// compile with: /c /LD /W1
class X {
public:
   int m_data;
};

void g() {
   const X x1;   // C4269
};
```

Vzhledem k tomu, že se tato instance třídy generuje v zásobníku, může být počáteční hodnota `m_data` cokoli. Kromě toho, vzhledem k tomu, že se jedná o **konstantní** instanci, nesmí být hodnota `m_data` změněna.
