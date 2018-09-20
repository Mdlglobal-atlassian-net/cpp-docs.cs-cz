---
title: 2.6.1 master konstrukce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d82ae673e428c635172f35f9b0f682aa65dc2b8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445630"
---
# <a name="261-master-construct"></a>2.6.1 master – konstrukce

**Hlavní** – direktiva určuje konstrukce, která určuje strukturovaný blok, který se spouští hlavní vlákno týmu. Syntaxe **hlavní** direktivy je následující:

```
#pragma omp master new-linestructured-block
```

Ostatní vlákna v týmu se neprovedou přidružené strukturovaný blok. Neexistuje žádný implicitní barrier buď na položku a nebo opuštění master – konstrukce.