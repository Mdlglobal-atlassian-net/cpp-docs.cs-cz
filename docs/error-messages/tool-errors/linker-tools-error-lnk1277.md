---
title: Chyba Linkerů LNK1277 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 542c48bd23b3f84ab301404987c77d964f51823e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082513"
---
# <a name="linker-tools-error-lnk1277"></a>Chyba linkerů LNK1277

v pgd (název souboru) se nenašel záznam objektu

Při použití [/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), se liší od cesty, na které se vyskytují během /LTCG:PGINSTRUMENT cestu vstupní soubory .obj, .lib či def. To může vysvětlit změnou v proměnné prostředí LIB po /LTCG:PGINSTRUMENT. Úplná cesta k vstupní soubor je uložen v souboru .pgd.

/LTCG:PGOPTIMIZE vyžaduje shodné s fáze /LTCG:PGINSTRUMENT vstupy.

Pokud chcete vyřešit toto upozornění, proveďte jednu z následujících akcí:

- Spusťte /LTCG:PGINSTRUMENT, znovu všechny testovací běhy a spusťte /LTCG:PGOPTIMIZE.

- Na co se při spuštění /LTCG:PGINSTRUMENT změňte proměnné prostředí LIB.

Není doporučeno pomocí /LTCG:PGUPDATE LNK1277 obejít.