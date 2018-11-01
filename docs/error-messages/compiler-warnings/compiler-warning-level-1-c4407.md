---
title: Kompilátor upozornění (úroveň 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: 5142e3800f3ad716166a27e3b0407a40999b5746
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436826"
---
# <a name="compiler-warning-level-1-c4407"></a>Kompilátor upozornění (úroveň 1) C4407

přetypování mezi různé reprezentacemi ukazatele na člen, kompilátor může vygenerovat nesprávný kód

Byl zjištěn nesprávný přetypování.

C4407 mohou být generovány z důvodu kompilátoru prací, které bylo provedeno v aplikaci Visual C++ 2005. Pointer-to-member nyní vyžaduje úplný název a address-of – operátor (&).

C4407 může dojít, pokud přetypování mezi více dědičnosti pointer-to-member na jednoduchá dědičnost pointer-to-member. Někdy to můžou fungovat, ale někdy není toho schopen, protože reprezentace pointer-to-member jednoduchá dědičnost nebude obsahovat dostatek informací. Kompilace s **/VMM** může pomoci (Další informace najdete v tématu [/VMM, / VMS, / vmv (obecná reprezentace)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). Můžete také zkusit uspořádání základní třídy; kompilátor je zjišťování ztráty informací v převod, protože základní třída je posunem nenulové od odvozený.

Následující ukázka generuje C4407:

```
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```