---
title: Upozornění kompilátoru (úroveň 4) C4937
ms.date: 11/04/2016
f1_keywords:
- C4937
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
ms.openlocfilehash: dd7a7f9ac3d0ce0798a88f753cb0ccb4addbd5bc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988754"
---
# <a name="compiler-warning-level-4-c4937"></a>Upozornění kompilátoru (úroveň 4) C4937

Text1 a Text2 nejde odlišit jako argumenty direktivy.

Vzhledem k tomu, jak kompilátor zpracovává argumenty na direktivy, názvy, které mají význam pro kompilátor, jako například klíčová slova s více reprezentacemi textu (jednoduché a dvojité podtržítko), nelze odlišit.

Příklady takových řetězců jsou __cdecl a \__forceinline.  Všimněte si, že v části/za jsou povoleny pouze formuláře dvojitých podtržítek.

Následující ukázka generuje C4937:

```cpp
// C4937.cpp
// compile with: /openmp /W4
#include "omp.h"
int main() {
   #pragma omp critical ( __leave )   // C4937
   ;

   // OK
   #pragma omp critical ( leave )
   ;
}
```
