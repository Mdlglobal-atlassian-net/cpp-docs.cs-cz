---
title: Chyba modulu C runtime R6026
ms.date: 11/04/2016
f1_keywords:
- R6026
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
ms.openlocfilehash: 28e541b61b6381cd283578a0ce1909e5b39a4a53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151913"
---
# <a name="c-runtime-error-r6026"></a>Chyba modulu C runtime R6026

není dostatek místa pro inicializaci stdio

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

K této chybě dochází, když není dost paměti k dispozici inicializovat standardní podporu vstupně-výstupní operace v modulu C runtime. K této chybě obvykle dochází při spuštění aplikace. Ověřte, že vaše aplikace a ovladače a knihovny DLL, která načte nedošlo k poškození haldy při spuštění.