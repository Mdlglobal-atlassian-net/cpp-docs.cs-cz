---
title: Chyba kompilátoru C3052
ms.date: 11/04/2016
f1_keywords:
- C3052
helpviewer_keywords:
- C3052
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
ms.openlocfilehash: ed9c27e1602f9372cb9137615ef66932a8df960c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265773"
---
# <a name="compiler-error-c3052"></a>Chyba kompilátoru C3052

'příkaz var': proměnná se neobjevuje v klauzuli data-sharing pod klauzulí default(none)

Pokud [default(none)](../../parallel/openmp/reference/default-openmp.md) se používá, všechny proměnné použité v strukturovaný blok musí být explicitně určena jako [sdílené](../../parallel/openmp/reference/shared-openmp.md) nebo [privátní](../../parallel/openmp/reference/private-openmp.md).

Následující ukázka generuje C3052:

```
// C3052.cpp
// compile with: /openmp /c
int main() {
   int n1 = 1;

   #pragma omp parallel default(none) // shared(n1) private(n1)
   {
      n1 = 0;   // C3052 use either a shared or private clause
   }
}
```