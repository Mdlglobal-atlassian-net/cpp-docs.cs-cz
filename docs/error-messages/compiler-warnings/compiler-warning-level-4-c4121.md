---
title: Upozornění kompilátoru (úroveň 4) upozornění C4121 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4121
dev_langs:
- C++
helpviewer_keywords:
- C4121
ms.assetid: 8c5b85c9-2543-426b-88bc-319c50158c7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bfd0c3c2ad4f0382867a4728a4e1f8748c02cad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098989"
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