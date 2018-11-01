---
title: Chyba kompilátoru C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: 2bccd15b8c2b6d1c5cd6c4b536bbdaf350eb0181
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512902"
---
# <a name="compiler-error-c2081"></a>Chyba kompilátoru C2081

'identifier': název v seznamu formálních parametrů je neplatný

Identifikátor způsobila chybu syntaxe.

Tuto chybu může způsobovat pomocí starý styl seznamu formálních parametrů. Musíte zadat typ formální parametry v seznamu formálních parametrů.

Následující ukázka generuje C2081:

```
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

Možná řešení:

```
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```