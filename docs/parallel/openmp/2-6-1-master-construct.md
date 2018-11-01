---
title: 2.6.1 master – konstrukce
ms.date: 11/04/2016
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
ms.openlocfilehash: 0501b1fdfbd36829cee2793fc0f7bb03daeda900
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475527"
---
# <a name="261-master-construct"></a>2.6.1 master – konstrukce

**Hlavní** – direktiva určuje konstrukce, která určuje strukturovaný blok, který se spouští hlavní vlákno týmu. Syntaxe **hlavní** direktivy je následující:

```
#pragma omp master new-linestructured-block
```

Ostatní vlákna v týmu se neprovedou přidružené strukturovaný blok. Neexistuje žádný implicitní barrier buď na položku a nebo opuštění master – konstrukce.