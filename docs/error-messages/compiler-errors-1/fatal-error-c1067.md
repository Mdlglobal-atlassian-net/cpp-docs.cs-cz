---
title: Závažná chyba C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: 3b016790220d409435ff7ea53c6f48899a9e8f1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204344"
---
# <a name="fatal-error-c1067"></a>Závažná chyba C1067

limit kompilátoru: překročil se limit 64 KB pro velikost záznamu typu.

K této chybě může dojít, pokud symbol obsahuje dekorované jméno delší než 247 znaků.  Chcete-li vyřešit, Zkraťte název symbolu.

Když kompilátor generuje ladicí informace, vygeneruje záznamy typu k definování typů zjištěných ve zdrojovém kódu.  Například typ záznamy obsahuje jednoduché struktury a seznamy argumentů funkcí.  Některé z těchto typů záznamů můžou být velké seznamy.

Velikost libovolného záznamu typu je omezena na 64 KB.  Pokud dojde k překročení tohoto limitu 64 KB, dojde k této chybě.

K C1067 může dojít také v případě, že existuje mnoho symbolů s dlouhými názvy nebo pokud třída, struktura nebo sjednocení má příliš mnoho členů.
