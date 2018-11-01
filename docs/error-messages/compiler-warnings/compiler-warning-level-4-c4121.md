---
title: Upozornění kompilátoru (úroveň 4) upozornění C4121
ms.date: 11/04/2016
f1_keywords:
- C4121
helpviewer_keywords:
- C4121
ms.assetid: 8c5b85c9-2543-426b-88bc-319c50158c7e
ms.openlocfilehash: 0d02c5aff188a82062ae537f053157795d8925d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540488"
---
# <a name="compiler-warning-level-4-c4121"></a>Upozornění kompilátoru (úroveň 4) upozornění C4121

Symbol: zarovnání člena záleželo na balení

Kompilátor přidal odsazení, aby zarovnal člena struktury na hranici balení, ale hodnota balení je menší než velikost člena. Například následující fragment kódu vygeneruje upozornění C4121:

```
// C4121.cpp
// compile with: /W4 /c
#pragma pack(2)
struct s
{
   char a;
   int b; // C4121
   long long c;
};
```

Chcete-li tento problém vyřešit, proveďte jednu z následujících změn:

- Změňte velikosti balení tak, aby byla stejná nebo větší než velikost člena, který způsobil toto upozornění. Například v tomto fragmentu kódu změňte `pack(2)` k `pack(4)` nebo `pack(8)`.

- Změňte pořadí deklarací členů podle velikosti od největšího po nejmenší. V tomto fragmentu kódu převraťte pořadí členů struktury tak, aby `long long` předchází člena `int`a `int` předchází `char`.

Toto upozornění se zobrazí pouze v případě, že kompilátor přidává před datové členy odsazení. Nezobrazí se, pokud jsou při balení data umístěna do místa v paměti, které není zarovnáno pro tento datový typ, ale před datový člen nebylo vloženo žádné odsazení. Pokud data nejsou zarovnána na hranicích, které jsou násobkem velikosti dat, může dojít ke snížení výkonu. Čtení a zápisy nezarovnaných dat způsobují u některých architektur chyby procesoru a vyřešení těchto chyb může trvat řádově dva až třikrát déle. Přístupy k nezarovnaným datům nelze portovat na některé architektury RISC.

Můžete použít [#pragma pack](../../preprocessor/pack.md) nebo [/zp](../../build/reference/zp-struct-member-alignment.md) k určení zarovnání struktury. (Kompilátor negeneruje toto upozornění, když **/Zp1** určena.)