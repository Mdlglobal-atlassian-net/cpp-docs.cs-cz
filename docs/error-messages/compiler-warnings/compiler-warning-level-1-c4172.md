---
title: Kompilátor upozornění (úroveň 1) C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: caa71da9182c1da1d17d87d901084d0ee9badf73
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391787"
---
# <a name="compiler-warning-level-1-c4172"></a>Kompilátor upozornění (úroveň 1) C4172

Vrací adresu lokální proměnné nebo dočasné

Funkce vrátí adresu místní proměnné nebo dočasný objekt. Lokálních proměnných a dočasné objekty jsou zničeny při návratu funkce, takže adresu vrácenou není platný.

Změnit návrh funkce tak, aby nevrací adresu místního objektu.

Následující ukázka generuje C4172:

```
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```