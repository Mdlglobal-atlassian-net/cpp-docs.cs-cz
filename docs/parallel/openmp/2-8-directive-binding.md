---
title: 2.8 vazby direktiv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc5b702b17e01bb8d4625a837abdb71086113e68
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415899"
---
# <a name="28-directive-binding"></a>2.8 Vazby direktiv

Dynamické vazby direktiv musí splňovat následující pravidla:

- **Pro**, **oddíly**, **jeden**, **hlavní**, a **bariéry** direktivy Svázat dynamicky vnější **paralelní**, pokud existuje, bez ohledu na hodnotu kterékoli **Pokud** klauzuli, která může být k dispozici na náhradu této direktivy. Je-li žádné paralelní oblasti se aktuálně zpracovává, direktivy jsou spuštěny týmem, který se skládá z pouze hlavní vlákno.

- **Seřazené** – direktiva vytvoří vazbu dynamicky uzavírající **pro**.

- **Atomické** vynucuje směrnice výhradní přístup k **atomické** direktivy ve všech vláknech, nikoli pouze aktuální týmu.

- **Kritické** vynucuje směrnice výhradní přístup k **kritické** direktivy ve všech vláknech, nikoli pouze aktuální týmu.

- Direktivu nikdy navázat žádné směrnice mimo nejbližšímu dynamicky uzavírající **paralelní**.