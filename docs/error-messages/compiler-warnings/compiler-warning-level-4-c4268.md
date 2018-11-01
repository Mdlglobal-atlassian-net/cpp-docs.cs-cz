---
title: Kompilátor upozornění (úroveň 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: e3cda7ed70963508d7663c6c12b2b98ac64db204
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676496"
---
# <a name="compiler-warning-level-4-c4268"></a>Kompilátor upozornění (úroveň 4) C4268

'identifier': 'const' statická/globální data inicializovaná s konstruktorem default generovaným kompilátorem vyplní objekt nulami

A **const** globální nebo statická instance nejsou v netriviálních třídy je inicializován pomocí konstruktoru vygenerovaný kompilátorem výchozí.

## <a name="example"></a>Příklad

```
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

Protože je tato instance třídy **const**, hodnota `m_data` nelze změnit.