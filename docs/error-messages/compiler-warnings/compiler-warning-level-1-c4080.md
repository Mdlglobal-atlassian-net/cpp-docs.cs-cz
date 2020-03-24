---
title: Upozornění kompilátoru (úroveň 1) C4080
ms.date: 11/04/2016
f1_keywords:
- C4080
helpviewer_keywords:
- C4080
ms.assetid: 964fb3f4-b9fd-450b-aa23-35cece126172
ms.openlocfilehash: a4e216ff455404514e1cd5f76b820111dba83a6d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200314"
---
# <a name="compiler-warning-level-1-c4080"></a>Upozornění kompilátoru (úroveň 1) C4080

očekával se identifikátor pro název segmentu; našel se symbol.

Název segmentu v [#pragma alloc_text](../../preprocessor/alloc-text.md) musí být řetězec nebo identifikátor. Kompilátor ignoruje direktivu pragma, pokud nebyl nalezen platný identifikátor.

Následující ukázka generuje C4080:

```cpp
// C4080.cpp
// compile with: /W1
extern "C" void func(void);

#pragma alloc_text()   // C4080

// try this line to resolve the warning
// #pragma alloc_text("mysection", func)

int main() {
}

void func(void) {
}
```
