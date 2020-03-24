---
title: Chyba modulu C runtime R6009
ms.date: 11/04/2016
f1_keywords:
- R6009
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
ms.openlocfilehash: 64391f8ec05a99bb85a9d6cd00d6488a945fdb62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197350"
---
# <a name="c-runtime-error-r6009"></a>Chyba modulu C runtime R6009

nedostatek místa pro prostředí

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace se vypnula, protože má problém interní paměti. K této chybě může dojít z několika možných důvodů, ale často je způsobena extrémně nízkou pamětí, příliš mnoho paměti zavedených proměnnými prostředí nebo chyba v programu.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Ukončete ostatní spuštěné aplikace nebo restartujte počítač pro uvolnění paměti.
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K načtení programu bylo dostatek paměti, ale nedostatek paměti pro vytvoření pole **envp** .  To může být způsobeno extrémně nedostatkem paměti nebo neobvyklým využitím proměnné prostředí. Vezměte v úvahu jedno z následujících řešení:

- Zvyšte množství paměti dostupné pro program.

- Snižte počet a velikost argumentů příkazového řádku.

- Zmenšení velikosti prostředí odebráním nepotřebných proměnných.
