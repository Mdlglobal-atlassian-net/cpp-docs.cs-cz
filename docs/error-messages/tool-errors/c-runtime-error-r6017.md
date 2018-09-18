---
title: Chyba modulu Runtime R6017 C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6017
dev_langs:
- C++
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2437e33610222183aa03a22cf6638156aaaa5e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077032"
---
# <a name="c-runtime-error-r6017"></a>Chyba modulu Runtime R6017 C

Chyba uzamčení neočekávané s více vlákny

> [!NOTE]
>  Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má vnitřní problém. Existuje několik příčin této chyby, ale často je způsobena závadou v kódu aplikace.
>
>  Zkuste chybu odstranit pomocí tohoto postupu:
>
>  -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> -   Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Procesu došlo k neočekávané chybě při pokusu o přístup k modulu runtime jazyka C s více vlákny zámek na systémový prostředek. K této chybě obvykle dochází, pokud proces neúmyslně mění haldy dat získaných za běhu. Však to může taky způsobovat vnitřní chybu v knihovně modulu runtime nebo operačního systému kódu.

Chcete-li vyřešit tento problém, zkontrolujte chyby poškození haldy ve vašem kódu. Další informace a příklady najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Dále zkontrolujte, že používáte nejnovější distribuovatelné součásti pro nasazení aplikace. Informace najdete v tématu [nasazení v jazyce Visual C++](../../ide/deployment-in-visual-cpp.md).