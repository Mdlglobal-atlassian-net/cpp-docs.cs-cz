---
title: Kompilátor upozornění (úroveň 3) C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 5f895a231c8b32d76e4ccd3c15ffae5717d8017f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476060"
---
# <a name="compiler-warning-level-3-c4316"></a>Kompilátor upozornění (úroveň 3) C4316

Objekt přidělený do haldy nemusí být zarovnáním pro tento typ.

Neoprávněně zarovnaný objektu přidělený pomocí `operator new` nemusí mít zadané zarovnání. Přepsat [operátor new](../../c-runtime-library/operator-new-crt.md) a [operátor delete](../../c-runtime-library/operator-delete-crt.md) pro nadbytečně zarovnané typy tak, že používají rutiny pro zarovnané přidělení – například [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) a [_aligned_free –](../../c-runtime-library/reference/aligned-free.md). Následující ukázka generuje C4316:

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```