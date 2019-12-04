---
title: Chyba kompilátoru C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: d4234626bc246d6da87be68b03d44562dd5990ff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744508"
---
# <a name="compiler-error-c2432"></a>Chyba kompilátoru C2432

Neplatný odkaz na 16bitová data v ' identifier '

16bitový registr se používá jako index nebo základní registr. Kompilátor nepodporuje odkazování na 16bitová data. 16bitové Registry nelze použít jako index nebo základní Registry při kompilaci pro 32 bitový kód.

Následující ukázka generuje C2432:

```cpp
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```
