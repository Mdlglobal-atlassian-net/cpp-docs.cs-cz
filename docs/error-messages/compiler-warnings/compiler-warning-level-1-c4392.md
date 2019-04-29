---
title: Kompilátor upozornění (úroveň 1) C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: 1dc0c546509b17132358f432f6a781035a314a72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386418"
---
# <a name="compiler-warning-level-1-c4392"></a>Kompilátor upozornění (úroveň 1) C4392

'podpis': nesprávný počet argumentů pro vnitřní funkci, byl očekáván ' argumentů.

Deklarace funkce pro vnitřní kompilátor má nesprávný počet argumentů. Výsledná bitová kopie se možná správně nespustí.

Pokud chcete vyřešit toto varování, opravte deklaraci nebo odstraňte deklaraci a jednoduše #include na příslušný soubor hlaviček.

Následující ukázka generuje C4392:

```
// C4392.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_stream_pd(double *dp);   // C4392

#ifdef  __cplusplus
}
#endif

int main()
{
}
```