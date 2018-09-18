---
title: Chyba modulu Runtime R6016 C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6016
dev_langs:
- C++
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65f4b4529e0faf433ff9dc5c4fc2c0594a4d9ff6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076642"
---
# <a name="c-runtime-error-r6016"></a>Chyba modulu Runtime R6016 C

Nedostatek místa pro data vlákna

> [!NOTE]
>  Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má problému s interní pamětí. Existuje mnoho možných příčin této chyby, ale často je způsobeno podmínku velmi málo paměti chybu v aplikaci, nebo chybu v add-in nebo rozšíření, které aplikace používá.
>
>  Zkuste chybu odstranit pomocí tohoto postupu:
>
>  -   Ukončete ostatní spuštěné aplikace nebo restartovat počítač pro uvolnění paměti.
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte aplikaci.
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** odebrat, opravte nebo přeinstalujte doplňky nebo rozšíření používané v aplikaci.
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> -   Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dochází, protože program nedostal od operačního systému pro dokončení dostatek paměti [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) nebo `_beginthreadex` volání nebo místní úložiště nebyla inicializována pomocí vlákna `_beginthread` nebo `_beginthreadex`.

Při spuštění nového vlákna musí knihovna vytvořit pro toto vlákno interní databázi. Pokud databázi nelze rozšířit pomocí paměti poskytované operačním systémem, vlákno se nespustí a volající proces se zastaví. K tomu může dojít, pokud proces vytvořil příliš mnoho vláken, nebo při vyčerpání místního úložiště vláken.

Doporučujeme vám, že by pomocí spustitelného souboru, který volá běhové knihovny jazyka C (CRT) `_beginthreadex` pro vytvoření vlákna spíše než rozhraní Windows API `CreateThread`. `_beginthreadex` Inicializuje interní statické úložiště používané mnoha funkcemi CRT v místním úložišti vláken. Pokud používáte `CreateThread` k vytvoření vlákna, CRT může proces ukončit s chybou R6016 při volání funkce CRT, které vyžaduje inicializované interní statické úložiště.