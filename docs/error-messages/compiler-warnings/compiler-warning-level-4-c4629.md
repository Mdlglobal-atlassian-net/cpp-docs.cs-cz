---
title: Upozornění kompilátoru (úroveň 4) C4629
ms.date: 11/04/2016
f1_keywords:
- C4629
helpviewer_keywords:
- C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
ms.openlocfilehash: 4aaaf3d592398981c1266a0ffbc1625da7d906af
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990616"
---
# <a name="compiler-warning-level-4-c4629"></a>Upozornění kompilátoru (úroveň 4) C4629

používá se graf, znaková sekvence ' degraf ' interpretována jako token ' char ' (pokud to není to, co jste zamýšleli, vložte mezeru mezi tyto dva znaky)

V části [/za](../../build/reference/za-ze-disable-language-extensions.md)se kompilátor upozorní, když detekuje graf.

Následující ukázka generuje C4629:

```cpp
// C4629.cpp
// compile with: /Za /W4
int main()
<%   // C4629 <% digraph for {
}
```
