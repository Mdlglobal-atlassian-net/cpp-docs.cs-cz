---
title: 2.8 Vazby direktiv
ms.date: 11/04/2016
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
ms.openlocfilehash: fb22d1b503303842ff73550c1c6544cae7e5f2f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528615"
---
# <a name="28-directive-binding"></a>2.8 Vazby direktiv

Dynamické vazby direktiv musí splňovat následující pravidla:

- **Pro**, **oddíly**, **jeden**, **hlavní**, a **bariéry** direktivy Svázat dynamicky vnější **paralelní**, pokud existuje, bez ohledu na hodnotu kterékoli **Pokud** klauzuli, která může být k dispozici na náhradu této direktivy. Je-li žádné paralelní oblasti se aktuálně zpracovává, direktivy jsou spuštěny týmem, který se skládá z pouze hlavní vlákno.

- **Seřazené** – direktiva vytvoří vazbu dynamicky uzavírající **pro**.

- **Atomické** vynucuje směrnice výhradní přístup k **atomické** direktivy ve všech vláknech, nikoli pouze aktuální týmu.

- **Kritické** vynucuje směrnice výhradní přístup k **kritické** direktivy ve všech vláknech, nikoli pouze aktuální týmu.

- Direktivu nikdy navázat žádné směrnice mimo nejbližšímu dynamicky uzavírající **paralelní**.