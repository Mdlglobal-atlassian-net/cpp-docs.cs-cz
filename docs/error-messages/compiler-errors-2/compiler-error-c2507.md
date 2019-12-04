---
title: Chyba kompilátoru C2507
ms.date: 11/04/2016
f1_keywords:
- C2507
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
ms.openlocfilehash: 23433dccd7fc4f86c2e848359ac50c796fcccab0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746796"
---
# <a name="compiler-error-c2507"></a>Chyba kompilátoru C2507

identifikátor: pro základní (Base) třídu je moc velký počet virtuálních modifikátorů.

Třída nebo struktura je deklarována jako `virtual` více než jednou. Pro každou třídu v seznamu základních tříd může být použit pouze jeden modifikátor `virtual`.

Následující ukázka generuje C2507:

```cpp
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```
