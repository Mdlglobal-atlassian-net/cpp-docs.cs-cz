---
title: Upozornění (úroveň 1) C4172 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4172
dev_langs:
- C++
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56f606b48fb060472dd67d34800c06946bc41712
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043505"
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