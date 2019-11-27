---
title: Upozornění kompilátoru (úroveň 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: 1d0531b79ef29d2aa9528cc29046fa9e9514c379
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541986"
---
# <a name="compiler-warning-level-4-c4268"></a>Upozornění kompilátoru (úroveň 4) C4268

identifikátor: statická/globální data const inicializovaná pomocí výchozího konstruktoru generovaného kompilátorem vyplní objekt nulami.

**Konstantní** globální nebo statická instance netriviální třídy je inicializována pomocí výchozího konstruktoru generovaného kompilátorem.

## <a name="example"></a>Příklad

```cpp
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

Jelikož je tato instance třídy **const**, hodnota `m_data` nemůže být změněna.