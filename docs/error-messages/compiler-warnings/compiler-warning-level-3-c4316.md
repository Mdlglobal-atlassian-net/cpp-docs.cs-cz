---
title: Upozornění kompilátoru (úroveň 3) C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 0d920cb3dc967854d1a507d06ce31fde6a670434
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198845"
---
# <a name="compiler-warning-level-3-c4316"></a>Upozornění kompilátoru (úroveň 3) C4316

Objekt přidělený k haldě nelze pro tento typ zarovnat.

Přerovnaný objekt přidělený pomocí `operator new` nesmí mít zadané zarovnání. Přepište [operátor New](../../c-runtime-library/operator-new-crt.md) a [operátoru delete](../../c-runtime-library/operator-delete-crt.md) pro přerovnanáelné typy tak, aby používaly rutiny zarovnané alokace, například [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) a [_aligned_free](../../c-runtime-library/reference/aligned-free.md). Následující ukázka generuje C4316:

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```
