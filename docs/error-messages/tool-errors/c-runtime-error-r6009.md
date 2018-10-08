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
ms.openlocfilehash: 42a5aed9f823b5d2c5425c4d7baae129c08e76e7
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860924"
---
# <a name="c-runtime-error-r6009"></a>Chyba modulu Runtime R6009 C

není dostatek místa pro prostředí

> [!NOTE]
> Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má problému s interní pamětí. Existuje několik příčin této chyby, ale často je způsobena podmínku velmi málo paměti příliš mnoho paměti provedenou proměnné prostředí nebo chyby v programu.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Ukončete ostatní spuštěné aplikace nebo restartovat počítač pro uvolnění paměti.
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> - Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> - Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Došlo k načtení programu dostatek paměti, ale není dostatek paměti k vytvoření **envp** pole.  Příčinou může být velmi nedostatek paměti nebo použití proměnných prostředí neobvykle velký. Zvažte jednu z následujících řešení:

- Zvýšit množství paměti k dispozici pro program.

- Snížení počtu a velikosti argumenty příkazového řádku.

- Zmenšete velikost prostředí odebráním nepotřebných proměnné.