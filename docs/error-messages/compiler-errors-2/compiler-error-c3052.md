---
title: Chyba kompilátoru C3052 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3052
dev_langs:
- C++
helpviewer_keywords:
- C3052
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d292087aefcc7bb99e505aefd0534dd018b2725
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049214"
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