---
title: Závažná chyba C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: f8fe301e25d9ecb5cc67397f9537e0bbd86c0627
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165850"
---
# <a name="fatal-error-c1067"></a>Závažná chyba C1067

limit kompilátoru: Došlo k překročení 64 kB omezení velikosti záznamu typu

K této chybě může dojít, pokud symbol má upravený název delší než 247 znaků.  Pokud chcete vyřešit, zkraťte název symbolu.

Když kompilátor generuje informace o ladění, vysílá záznamů typu k definování typů vyskytne ve zdrojovém kódu.  Například záznamů typu obsahovat jednoduchý struktury a seznamy argumentů funkce.  Některé z těchto záznamů typu mohou být dlouhé seznamy.

Je 64 kB omezení velikosti u všech typů záznamů.  Pokud se překročí tento limit 64K této chybě dojde.

C1067 může také dojít, pokud existuje mnoho symbolů s dlouhými názvy, nebo pokud se třída, struktura nebo sjednocení má příliš mnoho členů.