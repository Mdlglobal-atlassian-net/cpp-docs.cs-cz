---
title: Kompilátor upozornění (úroveň 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 9a7f42b2dd65644d3f2abec58236a0b93cc6f635
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207230"
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