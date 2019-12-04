---
title: Chyba kompilátoru C2600
ms.date: 11/04/2016
f1_keywords:
- C2600
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
ms.openlocfilehash: b2d95460cadf03f9152599ef47ae703030326dd1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740738"
---
# <a name="compiler-error-c2600"></a>Chyba kompilátoru C2600

' function ': nejde definovat speciální členskou funkci generovanou kompilátorem (musí být nejdřív deklarovaná ve třídě).

Než členské funkce, jako jsou konstruktory nebo destruktory, mohou být definovány pro třídu, musí být deklarovány ve třídě. Kompilátor může generovat výchozí konstruktory a destruktory (označované jako speciální členské funkce), pokud žádné nejsou deklarovány ve třídě. Pokud však definujete jednu z těchto funkcí bez párové deklarace ve třídě, kompilátor zjistí konflikt.

Chcete-li tuto chybu opravit, deklarujte v deklaraci třídy každou členskou funkci, kterou definujete vně deklarace třídy.

Následující ukázka generuje C2600:

```cpp
// C2600.cpp
// compile with: /c
class C {};
C::~C() {}   // C2600

class D {
   D::~D();
};

D::~D() {}
```
