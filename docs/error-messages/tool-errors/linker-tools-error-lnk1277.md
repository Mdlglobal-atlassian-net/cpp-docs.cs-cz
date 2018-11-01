---
title: Chyba linkerů LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 137aa15dd9dad4b08d52af55da60a9cdf8b58055
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662069"
---
# <a name="linker-tools-error-lnk1277"></a>Chyba linkerů LNK1277

v pgd (název souboru) se nenašel záznam objektu

Při použití [/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), se liší od cesty, na které se vyskytují během /LTCG:PGINSTRUMENT cestu vstupní soubory .obj, .lib či def. To může vysvětlit změnou v proměnné prostředí LIB po /LTCG:PGINSTRUMENT. Úplná cesta k vstupní soubor je uložen v souboru .pgd.

/LTCG:PGOPTIMIZE vyžaduje shodné s fáze /LTCG:PGINSTRUMENT vstupy.

Pokud chcete vyřešit toto upozornění, proveďte jednu z následujících akcí:

- Spusťte /LTCG:PGINSTRUMENT, znovu všechny testovací běhy a spusťte /LTCG:PGOPTIMIZE.

- Na co se při spuštění /LTCG:PGINSTRUMENT změňte proměnné prostředí LIB.

Není doporučeno pomocí /LTCG:PGUPDATE LNK1277 obejít.