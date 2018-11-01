---
title: Chyba modulu Runtime R6027 C
ms.date: 11/04/2016
f1_keywords:
- R6027
helpviewer_keywords:
- R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
ms.openlocfilehash: 2884f148091d9407d3229f0690a161639b5195e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446512"
---
# <a name="c-runtime-error-r6027"></a>Chyba modulu Runtime R6027 C

není dostatek místa pro inicializaci lowio

> [!NOTE]
> Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má problému s interní pamětí. Existuje několik příčin této chyby, ale obvykle je způsobena podmínku velmi málo paměti. Může být také způsobeno, chybu v aplikaci, poškozením knihoven Visual C++, které používá nebo ovladač.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Ukončete ostatní spuštěné aplikace nebo restartovat počítač pro uvolnění paměti.
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> - Pokud aplikace byla dříve poslední instalace jiné aplikace nebo ovladače funkční, použijte **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** odebrat Nová aplikace nebo ovladače a zkuste aplikaci znovu.
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte všechny kopie systému Microsoft Visual C++ Redistributable.
> - Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> - Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Tato chyba nastane, pokud není dostatek paměti lze inicializovat podporu vstupně-výstupních operací nízké úrovně v modulu C runtime. K této chybě obvykle dochází při spuštění aplikace. Ověřte, že vaše aplikace a ovladače a knihovny DLL, která načte nedošlo k poškození haldy při spuštění.