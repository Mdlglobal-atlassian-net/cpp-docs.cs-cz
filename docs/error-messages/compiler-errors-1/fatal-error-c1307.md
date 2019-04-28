---
title: Závažná chyba C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: 1acdda77ac9cbf8d99752de3b78ab9c32bbb4cbc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338529"
---
# <a name="fatal-error-c1307"></a>Závažná chyba C1307

Program byl upraven od shromáždění dat profilu

Při použití [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), linker zjištěn vstupní modul, který byl znovu zkompilovat po /LTCG:PGINSTRUMENT a že modul byl změněn na místo, kde stávající data profilu už nejsou relevantní. Například pokud grafu volání v modulu překompilovanou nezměnilo, bude kompilátor generovat C1307.

Pokud chcete tuto chybu vyřešit, spusťte /LTCG:PGINSTRUMENT, znovu všechny testovací běhy a spusťte /LTCG:PGOPTIMIZE. Pokud nelze spustit /LTCG:PGINSTRUMENT a znovu, které všechny testovací běhy, použijte k vytvoření optimalizované bitové kopie /LTCG:PGUPDATE místo /LTCG:PGOPTIMIZE.