---
title: Chyba modulu Runtime R6002 C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6002
dev_langs:
- C++
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc23cf3c692eef37a86b5385d2e9e3a68340374e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080919"
---
# <a name="c-runtime-error-r6002"></a>C R6002 Chyba za běhu

podpora plovoucí desetinné čárky není načtená.

Nepropojil potřebné knihovny s plovoucí desetinnou čárkou.

> [!NOTE]
>  Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má vnitřní problém. Existuje několik příčin této chyby, ale často je způsobena závadou v kódu aplikace nebo pokusem o spuštění aplikace, který nebyl vytvořen pro procesor konkrétní počítače.
>
>  Zkuste chybu odstranit pomocí tohoto postupu:
>
>  -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> -   Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Této chybě může dojít ve vaší aplikaci, když nebyl propojený s plovoucí desetinnou čárkou knihovny. Zkontrolujte, že pro jednu z těchto příčin:

- Řetězec formátu pro `printf_s` nebo `scanf_s` funkce obsažené specifikace formátu s plovoucí desetinnou čárkou a program neobsahuje žádné hodnoty s plovoucí desetinnou čárkou nebo proměnné. Chcete tento problém vyřešit, použijte argument typu s plovoucí desetinnou čárkou tak, aby odpovídaly specifikace formátu s plovoucí desetinnou čárkou nebo provést s plovoucí desetinnou čárkou přiřazení jinde v programu. To způsobí, že podpora plovoucí desetinné čárky, který se má načíst.

- Kompilátor minimalizuje velikost programu načtením podpora plovoucí desetinné čárky pouze v případě potřeby. Kompilátor nemůže zjistit, operace s plovoucí desetinnou čárkou nebo specifikace formátu s plovoucí desetinnou čárkou v řetězcích formátu, takže nenačte nezbytné rutiny s plovoucí desetinnou čárkou. Chcete-li vyřešit tento problém, použijte specifikace formátu s plovoucí desetinnou čárkou a zadat jako argument s plovoucí desetinnou čárkou nebo provést s plovoucí desetinnou čárkou přiřazení jinde v programu. To způsobí, že podpora plovoucí desetinné čárky, který se má načíst.

- V programu jazyků knihovny jazyka C byla zadána před knihovny až po FORTRAN při propojený program. Znovu připojit a určete knihovny jazyka C poslední.