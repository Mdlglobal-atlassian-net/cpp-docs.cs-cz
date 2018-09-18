---
title: Závažná chyba C1307 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65f398dd9885c571ea0d66171889f20d3321a3b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085859"
---
# <a name="fatal-error-c1307"></a>Závažná chyba C1307

Program byl upraven od shromáždění dat profilu

Při použití [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), linker zjištěn vstupní modul, který byl znovu zkompilovat po /LTCG:PGINSTRUMENT a že modul byl změněn na místo, kde stávající data profilu už nejsou relevantní. Například pokud grafu volání v modulu překompilovanou nezměnilo, bude kompilátor generovat C1307.

Pokud chcete tuto chybu vyřešit, spusťte /LTCG:PGINSTRUMENT, znovu všechny testovací běhy a spusťte /LTCG:PGOPTIMIZE. Pokud nelze spustit /LTCG:PGINSTRUMENT a znovu, které všechny testovací běhy, použijte k vytvoření optimalizované bitové kopie /LTCG:PGUPDATE místo /LTCG:PGOPTIMIZE.