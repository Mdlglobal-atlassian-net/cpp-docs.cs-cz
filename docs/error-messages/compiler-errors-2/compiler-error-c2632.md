---
title: Chyba kompilátoru C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: f69d43bf50f5f13957e49d1e9ffa798a3db5a7b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754690"
---
# <a name="compiler-error-c2632"></a>Chyba kompilátoru C2632

typ typ1 následovaný ' typ2 ' je neplatný

Tato chyba může být způsobena tím, že chybí kód mezi dvěma specifikátory typu.

Následující ukázka generuje C2632:

```cpp
// C2632.cpp
int float i;   // C2632
```

Tato chyba se může vygenerovat taky v důsledku práce s shodami s kompilátorem, která se dokončila pro Visual Studio .NET 2003. `bool` je teď řádný typ. V předchozích verzích byl `bool` definice typedef a můžete vytvořit identifikátory s tímto názvem.

Následující ukázka generuje C2632:

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

Chcete-li tuto chybu vyřešit, aby byl kód platný jak ve Visual C++studio .NET 2003, tak ve Visual Studio .NET verze vizuálu, přejmenujte identifikátor.
