---
title: Závažná chyba C1067 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1067
dev_langs:
- C++
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f267e58617fbc68835fd3a387c4b635de4fd0530
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077669"
---
# <a name="fatal-error-c1067"></a>Závažná chyba C1067

limit kompilátoru: došlo k překročení 64 kB omezení velikosti záznamu typu

K této chybě může dojít, pokud symbol má upravený název delší než 247 znaků.  Pokud chcete vyřešit, zkraťte název symbolu.

Když kompilátor generuje informace o ladění, vysílá záznamů typu k definování typů vyskytne ve zdrojovém kódu.  Například záznamů typu obsahovat jednoduchý struktury a seznamy argumentů funkce.  Některé z těchto záznamů typu mohou být dlouhé seznamy.

Je 64 kB omezení velikosti u všech typů záznamů.  Pokud se překročí tento limit 64K této chybě dojde.

C1067 může také dojít, pokud existuje mnoho symbolů s dlouhými názvy, nebo pokud se třída, struktura nebo sjednocení má příliš mnoho členů.