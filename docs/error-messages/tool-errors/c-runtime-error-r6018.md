---
title: Chyba modulu Runtime R6018 C
ms.date: 11/04/2016
f1_keywords:
- R6018
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
ms.openlocfilehash: e0d229b4fd8c1a4f8e067c0e59a278344fd4e113
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531912"
---
# <a name="c-runtime-error-r6018"></a>Chyba modulu Runtime R6018 C

Chyba neočekávané haldy

> [!NOTE]
> Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má vnitřní problém. Existuje několik příčin této chyby, ale často je způsobena závadou v kódu aplikace.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> - Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> - Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Program došlo k neočekávané chybě při provádění operace správy paměti.

K této chybě obvykle dochází, pokud program neúmyslně mění data za běhu haldy. Ale ho může taky způsobovat vnitřní chybě v modulu runtime nebo operačního systému kódu.

Chcete-li vyřešit tento problém, zkontrolujte chyby poškození haldy ve vašem kódu. Další informace a příklady najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Dále zkontrolujte, že používáte nejnovější distribuovatelné součásti pro nasazení aplikace. Informace najdete v tématu [nasazení v jazyce Visual C++](../../ide/deployment-in-visual-cpp.md).