---
title: Chyba kompilátoru C2600
ms.date: 11/04/2016
f1_keywords:
- C2600
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
ms.openlocfilehash: 4d9e94790c3f4b2fa0aaf36894f0b12c7134a9ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500396"
---
# <a name="compiler-error-c2600"></a>Chyba kompilátoru C2600

'function': nelze definovat kompilátorem generované zvláštní členské funkce (nejprve musí být deklarován ve třídě)

Před členské funkce jako konstruktory a destruktory lze definovat pro třídu musí být deklarovány ve třídě. Kompilátor může generovat výchozí konstruktory a destruktory (označované jako zvláštní členské funkce), pokud žádné není deklarovaný ve třídě. Ale pokud definujete jednu z těchto funkcí bez odpovídající deklarace ve třídě, kompilátor zjistí ke konfliktu.

Chcete-li opravit tuto chybu v deklaraci třídy, deklarujte Každá členská funkce, které definujete mimo deklaraci třídy.

Následující ukázka generuje C2600:

```
// C2600.cpp
// compile with: /c
class C {};
C::~C() {}   // C2600

class D {
   D::~D();
};

D::~D() {}
```