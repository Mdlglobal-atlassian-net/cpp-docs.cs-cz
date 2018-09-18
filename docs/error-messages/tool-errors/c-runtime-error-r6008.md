---
title: Chyba modulu Runtime R6008 C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6008
dev_langs:
- C++
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39b06566f84003b08f5fe3869a021c4bf86dcf5f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105121"
---
# <a name="c-runtime-error-r6008"></a>Chyba modulu Runtime R6008 C

není dostatek místa pro argumenty

> [!NOTE]
>  Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má problému s interní pamětí. Existuje několik příčin této chyby, ale často je způsobena podmínku velmi málo paměti příliš mnoho paměti provedenou proměnné prostředí nebo chyby v programu.
>
>  Zkuste chybu odstranit pomocí tohoto postupu:
>
>  -   Ukončete ostatní spuštěné aplikace nebo restartovat počítač pro uvolnění paměti.
> -   Snížení počtu a velikosti argumenty příkazového řádku do aplikace.
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> -   Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Byl dostatek paměti pro načtení programu, ale není dostatek paměti k vytvoření **argv** pole. Důvodem může být velmi nedostatek paměti nebo neobvykle vysoký příkazových řádků nebo použití proměnných prostředí. Zvažte jednu z následujících řešení:

- Zvýšit množství paměti k dispozici pro program.

- Snížení počtu a velikosti argumenty příkazového řádku.

- Zmenšete velikost prostředí odebráním nepotřebných proměnné.