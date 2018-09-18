---
title: Upozornění (úroveň 1) C4269 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4269
dev_langs:
- C++
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6dc986c98028530b8a5d4d25047305fd1a8effef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027273"
---
# <a name="compiler-warning-level-1-c4269"></a>Kompilátor upozornění (úroveň 1) C4269

'identifier': 'const' automatické data inicializovaná s konstruktorem default generovaným kompilátorem vytvoří nespolehlivé výsledky

A **const** automatické instance nejsou v netriviálních třídy je inicializována s kompilátorem generované výchozí konstruktor.

## <a name="example"></a>Příklad

```
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

Protože tato instance třídy, je vygenerována v zásobníku, počáteční hodnota `m_data` může být cokoli. Kromě toho od té doby je **const** instance, hodnota `m_data` nikdy lze změnit.