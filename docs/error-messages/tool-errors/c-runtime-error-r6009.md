---
title: Chyba modulu Runtime R6009 C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6009
dev_langs:
- C++
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0deafa72a427543c0d885401a1d4192d61a6db65
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069037"
---
# <a name="c-runtime-error-r6009"></a>Chyba modulu Runtime R6009 C

není dostatek místa pro prostředí

> [!NOTE]
>  Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má problému s interní pamětí. Existuje několik příčin této chyby, ale často je způsobena podmínku velmi málo paměti příliš mnoho paměti provedenou proměnné prostředí nebo chyby v programu.
>
>  Zkuste chybu odstranit pomocí tohoto postupu:
>
>  -   Ukončete ostatní spuštěné aplikace nebo restartovat počítač pro uvolnění paměti.
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> -   Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Došlo k načtení programu dostatek paměti, ale není dostatek paměti k vytvoření **envp** pole.  Příčinou může být velmi nedostatek paměti nebo použití proměnných prostředí neobvykle velký. Zvažte jednu z následujících řešení:

- Zvýšit množství paměti k dispozici pro program.

- Snížení počtu a velikosti argumenty příkazového řádku.

- Zmenšete velikost prostředí odebráním nepotřebných proměnné.