---
title: Chyba modulu Runtime R6028 C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6028
dev_langs:
- C++
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a23fcd6ff7c5fb49e31efab831f1102bc079d91
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093380"
---
# <a name="c-runtime-error-r6028"></a>Chyba modulu Runtime R6028 C

Nelze inicializovat haldu

> [!NOTE]
>  Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má problému s interní pamětí. Existuje mnoho možných příčin této chyby, ale často je způsobeno podmínku velmi málo paměti chyb v programu, nebo hardwarové vadné ovladače.
>
>  Zkuste chybu odstranit pomocí tohoto postupu:
>
>  -   Ukončete ostatní spuštěné aplikace nebo restartovat počítač pro uvolnění paměti.
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> -   Pokud aplikace byla dříve poslední instalace jiné aplikace nebo ovladače funkční, použijte **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** odebrat Nová aplikace nebo ovladače a zkuste aplikaci znovu.
> -   Zkontrolujte web dodavatele hardwaru nebo **Windows Update** v **ovládací panely** pro aktualizace softwaru a ovladače.
> -   Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dojde, když se operačnímu systému nepodaří vytvořit fond paměti pro aplikace. Konkrétně prostředí Runtime jazyka C (CRT) volalo funkci Win32 `HeapCreate`, která vrátila hodnotu NULL označující selhání.

Pokud k této chybě dojde během spouštění aplikace, nemusí být systém schopen splnit požadavky haldy, protože jsou načteny vadné ovladače. Pomocí služby Windows Update nebo na webu dodavatele hardwaru vyhledejte aktualizované ovladače.