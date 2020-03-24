---
title: Chyba modulu C runtime R6002
ms.date: 11/04/2016
f1_keywords:
- R6002
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
ms.openlocfilehash: b2e617b6f7841f1aa7e6fd2f6962c0e117fab6c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197415"
---
# <a name="c-runtime-error-r6002"></a>Chyba modulu C runtime R6002

Podpora plovoucí desetinné čárky není načtena

Nutná knihovna plovoucí desetinné čárky nebyla propojena.

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace byla vypnuta, protože došlo k vnitřnímu problému. Tato chyba může mít několik příčin, ale často je způsobena nedostatkem kódu aplikace nebo pokusem o spuštění aplikace, která nebyla sestavena pro konkrétní procesor počítače.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě může dojít v aplikaci, když nebyla propojena knihovna plovoucí desetinné čárky. Vyhledejte jeden z těchto příčin:

- Formátovací řetězec pro funkci `printf_s` nebo `scanf_s` obsahoval specifikaci formátu s plovoucí desetinnou čárkou a program neobsahoval žádné hodnoty nebo proměnné s plovoucí desetinnou čárkou. Chcete-li tento problém vyřešit, použijte argument s plovoucí desetinnou čárkou, který bude odpovídat specifikaci formátu s plovoucí desetinnou čárkou, nebo můžete provést přiřazení plovoucí desetinné čárky jinde v programu. To způsobuje, že se načte podpora plovoucí desetinné čárky.

- Kompilátor minimalizuje velikost programu načtením podpory plovoucí desetinné čárky, pouze pokud je to nutné. Kompilátor nemůže detekovat operace s plovoucí desetinnou čárkou nebo specifikace formátu s plovoucí desetinnou čárkou ve formátovacích řetězcích, takže nenačte potřebné rutiny s plovoucí desetinnou čárkou. Chcete-li tento problém vyřešit, použijte specifikaci formátu s plovoucí desetinnou čárkou a zadejte argument s plovoucí desetinnou čárkou, nebo v programu proveďte jiné přiřazení s plovoucí desetinnou čárkou. To způsobuje, že se načte podpora plovoucí desetinné čárky.

- V programu se smíšeným jazykem byla před knihovnou FORTRAN při propojení programu zadána knihovna jazyka C. Znovu propojte a zadejte poslední knihovnu jazyka C.
