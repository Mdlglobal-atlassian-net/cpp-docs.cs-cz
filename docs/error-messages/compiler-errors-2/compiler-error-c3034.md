---
title: Chyba kompilátoru C3034
ms.date: 11/04/2016
f1_keywords:
- C3034
helpviewer_keywords:
- C3034
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
ms.openlocfilehash: d0a5da87feeabc5d3d5b558ce0dd6bdfe3869d53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595101"
---
# <a name="compiler-error-c3034"></a>Chyba kompilátoru C3034

Direktivy OpenMP 'directive1' nemůže být přímo vnořená v rámci "directive2" – direktiva

Některé direktivy nemůže být vnořený. Chcete-li vyřešit tuto chybu, příkazy direktivy můžete sloučit do bloku jedna direktiva nebo můžete vytvořit po sobě jdoucích direktivy.

Následující ukázka generuje C3034:

```
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