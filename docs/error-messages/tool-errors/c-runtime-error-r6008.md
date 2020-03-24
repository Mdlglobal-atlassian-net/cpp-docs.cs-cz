---
title: Chyba modulu C runtime R6008
ms.date: 11/04/2016
f1_keywords:
- R6008
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
ms.openlocfilehash: 214b6548cc7a3b880223503c2f3e9222d64212ca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197390"
---
# <a name="c-runtime-error-r6008"></a>Chyba modulu C runtime R6008

nedostatek místa pro argumenty

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace se vypnula, protože má problém interní paměti. K této chybě může dojít z několika možných důvodů, ale často je způsobena extrémně nízkou pamětí, příliš mnoho paměti zavedených proměnnými prostředí nebo chyba v programu.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Ukončete ostatní spuštěné aplikace nebo restartujte počítač pro uvolnění paměti.
> - Snižte počet a velikost argumentů příkazového řádku pro aplikaci.
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K načtení programu je dostatek paměti, ale nedostatek paměti pro vytvoření pole **argv** . To může být způsobeno extrémně nedostatkem paměti nebo neobvyklými možnostmi použití příkazů nebo proměnných prostředí. Vezměte v úvahu jedno z následujících řešení:

- Zvyšte množství paměti dostupné pro program.

- Snižte počet a velikost argumentů příkazového řádku.

- Zmenšení velikosti prostředí odebráním nepotřebných proměnných.
