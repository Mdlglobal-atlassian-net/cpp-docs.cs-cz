---
title: Chyba kompilátoru C3034
ms.date: 11/04/2016
f1_keywords:
- C3034
helpviewer_keywords:
- C3034
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
ms.openlocfilehash: 56ae2ddf35148fe263e406f48526cd68c4f91352
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748291"
---
# <a name="compiler-error-c3034"></a>Chyba kompilátoru C3034

Direktiva OpenMP ' directive1 ' nemůže být přímo vnořená v rámci direktivy ' directive2 '.

Některé direktivy nemůžou být vnořené. Chcete-li tuto chybu opravit, můžete sloučit příkazy obou direktiv do bloku jedné direktivy nebo můžete vytvořit po sobě jdoucí direktivy.

Následující ukázka generuje C3034:

```cpp
// C3034.cpp
// compile with: /openmp /link vcomps.lib
int main() {

   #pragma omp single
   {
      #pragma omp single   // C3034
      {
      ;
      }
   }

   // Two consecutive single clauses are OK.
   #pragma omp single
   {
   }

   #pragma omp single
   {
   }
}
```
