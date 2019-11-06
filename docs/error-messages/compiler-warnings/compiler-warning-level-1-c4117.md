---
title: Upozornění kompilátoru (úroveň 1) C4117
ms.date: 11/04/2016
f1_keywords:
- C4117
helpviewer_keywords:
- C4117
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
ms.openlocfilehash: 97fd5703a744448db87634e313678cf4e824df7f
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626274"
---
# <a name="compiler-warning-level-1-c4117"></a>Upozornění kompilátoru (úroveň 1) C4117

název makra Name je rezervovaný; Příkaz Command se ignoroval.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Pokus o definování nebo zrušení definice předdefinovaného makra.

1. Probíhá pokus o definování nebo zrušení definice **definovaného**operátoru preprocesoru.

Následující ukázka generuje C4117:

```cpp
// C4117.cpp
// compile with: /W1
#define __FILE__ test         // C4117. __FILE__ is a predefined macro
#define ValidMacroName test   // ok

int main() {
}
```