---
title: Upozornění kompilátoru (úroveň 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: cdc25155aced50331851e9581c346155c6f8e45c
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966345"
---
# <a name="compiler-warning-level-1-c4407"></a>Upozornění kompilátoru (úroveň 1) C4407

přetypování mezi různými ukazateli na reprezentace členů, kompilátor může generovat nesprávný kód.

Bylo zjištěno nesprávné přetypování.

C4407 je možné vygenerovat z důvodu práce v souladu s kompilátorem, která byla provedena v aplikaci Visual Studio 2005. Ukazatel na člena nyní vyžaduje úplný název a operátor address-of (&).

K C4407 může dojít, pokud přetypování mezi vícenásobnou dědičností mezi jednotlivými členy a jedním členem ukazatele dědičnosti na člena. V některých případech to může fungovat, ale někdy to nemůže být způsobeno tím, že reprezentace typu pointer-to-Member s jediným děděním neobsahuje dostatečné informace. Kompilace s **/VMM** může pomáhat (Další informace najdete v tématu [/VMM,/VMS,/VMV (pro obecné účely reprezentaci)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). Můžete také zkusit změnit uspořádání základních tříd; Kompilátor detekuje ztrátu informací v převodu, protože základní třída je nenulového posunu od odvozeného.

Následující ukázka generuje C4407:

```cpp
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