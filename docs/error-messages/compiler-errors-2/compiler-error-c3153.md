---
title: Chyba kompilátoru C3153 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3153
dev_langs:
- C++
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 621af32475008eda4d7502530087673dcb4a0848
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016037"
---
# <a name="compiler-error-c3153"></a>Chyba kompilátoru C3153

'rozhraní': Nelze vytvořit instanci rozhraní

Nelze vytvořit instanci rozhraní. Použít členy rozhraní, odvoďte třídu z rozhraní, implementovat členy rozhraní a pak použít členy.

Následující ukázka generuje C3153:

```
// C3153.cpp
// compile with: /clr
interface class A {
};

int main() {
   A^ a = gcnew A;   // C3153
}
```
