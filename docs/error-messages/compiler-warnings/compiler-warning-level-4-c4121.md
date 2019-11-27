---
title: Upozornění kompilátoru (úroveň 4) C4121
ms.date: 11/04/2016
f1_keywords:
- C4121
helpviewer_keywords:
- C4121
ms.assetid: 8c5b85c9-2543-426b-88bc-319c50158c7e
ms.openlocfilehash: bafa16cbad2cb0a2475cae5a98c608096e296442
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541623"
---
# <a name="compiler-warning-level-4-c4121"></a>Upozornění kompilátoru (úroveň 4) C4121

Symbol: zarovnání člena záleželo na balení

Kompilátor přidal odsazení, aby zarovnal člena struktury na hranici balení, ale hodnota balení je menší než velikost člena. Například následující fragment kódu vygeneruje upozornění C4121:

```cpp
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

- Změňte velikosti balení tak, aby byla stejná nebo větší než velikost člena, který způsobil toto upozornění. Například v tomto fragmentu kódu změňte `pack(2)` na `pack(4)` nebo `pack(8)`.

- Změňte pořadí deklarací členů podle velikosti od největšího po nejmenší. Ve fragmentu kódu obrátí pořadí členů struktury tak, aby `long long` člen předchází `int`a `int` předchází `char`.

Toto upozornění se zobrazí pouze v případě, že kompilátor přidává před datové členy odsazení. Nezobrazí se, pokud jsou při balení data umístěna do místa v paměti, které není zarovnáno pro tento datový typ, ale před datový člen nebylo vloženo žádné odsazení. Pokud data nejsou zarovnána na hranicích, které jsou násobkem velikosti dat, může dojít ke snížení výkonu. Čtení a zápisy nezarovnaných dat způsobují u některých architektur chyby procesoru a vyřešení těchto chyb může trvat řádově dva až třikrát déle. Přístupy k nezarovnaným datům nelze portovat na některé architektury RISC.

K určení zarovnání struktury lze použít [sadu #pragma pack](../../preprocessor/pack.md) nebo [/zp](../../build/reference/zp-struct-member-alignment.md) . (Kompilátor negeneruje toto upozornění, je-li zadán parametr **/Zp1** .)