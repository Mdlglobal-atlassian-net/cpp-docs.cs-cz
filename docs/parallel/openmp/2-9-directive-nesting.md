---
title: 2.9 vnořování direktiv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9558180a2f063171be563219f89ec3858e37a5d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396984"
---
# <a name="29-directive-nesting"></a>2.9 Vnořování direktiv

Dynamického vnoření direktiv musí splňovat následující pravidla:

- A **paralelní** direktiv dynamicky uvnitř jiného **paralelní** logicky zavádí nový tým, který se skládá z aktuálního vlákna, není-li vnořené paralelismu je povolená.

- **pro**, **oddíly**, a **jeden** direktivy, kteří jsou navázáni na stejný **paralelní** nemohou být vnořená v sobě navzájem.

- **kritické** direktivy se stejným názvem nemůžou být vnořena v sobě navzájem. Všimněte si, že toto omezení není dostatečné k zabránění vzájemnému zablokování.

- **pro**, **oddíly**, a **jeden** direktivy nejsou povolené v dynamický rozsah **kritické**, **seřazené**, a **hlavní** oblastech, pokud direktivy vytvořit vazbu na stejný **paralelní** jako oblastí.

- **bariéra** direktivy nejsou povolené v dynamický rozsah **pro**, **seřazené**, **oddíly**, **jeden**, **hlavní**, a **kritické** oblastech, pokud direktivy vytvořit vazbu na stejný **paralelní** jako oblastí.

- **hlavní** direktivy nejsou povolené v dynamický rozsah **pro**, **oddíly**, a **jeden** direktivy Pokud **hlavní** direktivy vytvořit vazbu na stejný **paralelní** jako direktiv pro sdílení práce.

- **seřazené** direktivy nejsou povoleny dynamické rozsahu **kritické** oblastech, pokud direktivy vytvořit vazbu na stejný **paralelní** jako oblastí.

- Směrnice, které je povoleno při provedení dynamicky v rámci paralelní oblasti je povolen také při spuštění mimo paralelní oblasti. Při spuštění dynamicky mimo paralelní oblasti zadaného uživatelem, direktiva provádí týmem, který se skládá z pouze hlavní vlákno.