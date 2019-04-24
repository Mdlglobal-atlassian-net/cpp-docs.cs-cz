---
title: Chyba modulu C runtime R6008
ms.date: 11/04/2016
f1_keywords:
- R6008
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
ms.openlocfilehash: 60e6475a84d2662ad3718e04dba879dc06afeee7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214074"
---
# <a name="c-runtime-error-r6008"></a>Chyba modulu C runtime R6008

není dostatek místa pro argumenty

> [!NOTE]
> Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má problému s interní pamětí. Existuje několik příčin této chyby, ale často je způsobena podmínku velmi málo paměti příliš mnoho paměti provedenou proměnné prostředí nebo chyby v programu.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Ukončete ostatní spuštěné aplikace nebo restartovat počítač pro uvolnění paměti.
> - Snížení počtu a velikosti argumenty příkazového řádku do aplikace.
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> - Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> - Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Byl dostatek paměti pro načtení programu, ale není dostatek paměti k vytvoření **argv** pole. Důvodem může být velmi nedostatek paměti nebo neobvykle vysoký příkazových řádků nebo použití proměnných prostředí. Zvažte jednu z následujících řešení:

- Zvýšit množství paměti k dispozici pro program.

- Snížení počtu a velikosti argumenty příkazového řádku.

- Zmenšete velikost prostředí odebráním nepotřebných proměnné.