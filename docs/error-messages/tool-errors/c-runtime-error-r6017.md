---
title: Chyba modulu Runtime R6017 C
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 75e2512196937b483d6bc1a9817f6957bb468418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653918"
---
# <a name="c-runtime-error-r6017"></a>Chyba modulu Runtime R6017 C

Chyba uzamčení neočekávané s více vlákny

> [!NOTE]
> Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má vnitřní problém. Existuje několik příčin této chyby, ale často je způsobena závadou v kódu aplikace.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> - Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> - Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Procesu došlo k neočekávané chybě při pokusu o přístup k modulu runtime jazyka C s více vlákny zámek na systémový prostředek. K této chybě obvykle dochází, pokud proces neúmyslně mění haldy dat získaných za běhu. Však to může taky způsobovat vnitřní chybu v knihovně modulu runtime nebo operačního systému kódu.

Chcete-li vyřešit tento problém, zkontrolujte chyby poškození haldy ve vašem kódu. Další informace a příklady najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Dále zkontrolujte, že používáte nejnovější distribuovatelné součásti pro nasazení aplikace. Informace najdete v tématu [nasazení v jazyce Visual C++](../../ide/deployment-in-visual-cpp.md).