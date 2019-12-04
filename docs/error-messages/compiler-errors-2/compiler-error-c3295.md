---
title: Chyba kompilátoru C3295
ms.date: 11/04/2016
f1_keywords:
- C3295
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
ms.openlocfilehash: 4ee79e87085b0b939a762fec4c576c393846c2ae
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756861"
---
# <a name="compiler-error-c3295"></a>Chyba kompilátoru C3295

klíčové slovo #pragma pragma se dá použít jenom v oboru názvů Global nebo Namespace.

Některé direktivy pragma nelze použít ve funkci.  Další informace naleznete v tématu [direktivy pragma a klíčové slovo __pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C3295.

```cpp
// C3295.cpp
int main() {
   #pragma managed   // C3295
}
```
