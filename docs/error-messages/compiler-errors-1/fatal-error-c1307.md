---
title: Závažná chyba C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: c7eb90c8e17408f6898ef7ff1a9d9e5efcafb4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203343"
---
# <a name="fatal-error-c1307"></a>Závažná chyba C1307

program se od shromáždění dat profilu upravoval.

Při použití [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)linker zjistil vstupní modul, který byl znovu zkompilován po/LTCG: PGINSTRUMENT a že byl modul změněn do bodu, ve kterém již existující data profilu nejsou relevantní. Například pokud se graf volání změnil v rekompilovaném modulu, kompilátor vygeneruje C1307.

Chcete-li tuto chybu vyřešit, spusťte/LTCG: PGINSTRUMENT, znovu spusťte všechny testovací běhy a spusťte/LTCG: PGOPTIMIZE. Pokud nemůžete spustit/LTCG: PGINSTRUMENT a opakovat všechny testovací běhy, použijte/LTCG: PGUPDATE namísto/LTCG: PGOPTIMIZE k vytvoření optimalizované bitové kopie.
