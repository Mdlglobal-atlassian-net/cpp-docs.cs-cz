---
title: Chyba modulu Runtime R6024 C
ms.date: 11/04/2016
f1_keywords:
- R6024
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
ms.openlocfilehash: 89b99a93512603eaf2273a6ff3f434f1ad3b3bb8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497052"
---
# <a name="c-runtime-error-r6024"></a>Chyba modulu Runtime R6024 C

není dostatek místa pro tabulku _onexit/atexit

> [!NOTE]
> Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má problému s interní pamětí. Tato chyba je obvykle způsobeno podmínku velmi málo paměti nebo jen zřídka, chyb v programu nebo poškozením knihoven Visual C++, které používá.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Ukončete ostatní spuštěné aplikace nebo restartovat počítač pro uvolnění paměti.
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte všechny kopie systému Microsoft Visual C++ Redistributable.
> - Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> - Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dochází, protože nebylo k dispozici pro žádné paměti `_onexit` nebo `atexit` funkce. Tato chyba je způsobena podmínku nedostatku paměti. Můžete zvážit, předběžně přiděluje vyrovnávací paměti při spuštění aplikace, které pomáhají při ukládání uživatelských dat a provedení čisté aplikace ukončit v nedostatku paměti.