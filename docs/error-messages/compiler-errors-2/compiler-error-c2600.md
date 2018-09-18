---
title: Chyba kompilátoru C2600 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2600
dev_langs:
- C++
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1846cefa78c8df13e8ca3c1a7fbc142ba2bf6ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022081"
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