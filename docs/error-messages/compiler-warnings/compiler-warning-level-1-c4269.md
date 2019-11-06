---
title: Upozornění kompilátoru (úroveň 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 84a0d4c541f67742d68c7f08e0dda52ccd350d04
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626712"
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