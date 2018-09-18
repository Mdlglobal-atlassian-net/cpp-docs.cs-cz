---
title: Chyba modulu Runtime R6032 C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6032
dev_langs:
- C++
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43155f24411fb5206a03d607f0551c2d34294aeb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024200"
---
# <a name="c-runtime-error-r6032"></a>Chyba modulu Runtime R6032 C

Není dostatek místa pro informace o národním prostředí

> [!NOTE]
>  Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má problému s interní pamětí. Existuje několik příčin této chyby, ale často je způsobeno podmínku velmi málo paměti, nebo chybu v programu.
>
>  Zkuste chybu odstranit pomocí tohoto postupu:
>
>  -   Ukončete ostatní spuštěné aplikace nebo restartovat počítač pro uvolnění paměti.
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> -   Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Modul runtime uchovává informace o národním prostředí v každém vláknu tak, že dokáže zpracovat volání funkcí citlivé na národní prostředí. Selhání přidělení paměti pro tyto informace je modul runtime nemůže pokračovat, protože na ní závisí příliš mnoho jeho základní funkce.