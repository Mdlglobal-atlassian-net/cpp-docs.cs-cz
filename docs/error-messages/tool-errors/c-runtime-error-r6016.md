---
title: Chyba modulu C runtime R6016
ms.date: 11/04/2016
f1_keywords:
- R6016
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
ms.openlocfilehash: 22bf4b7e8951215d1a013edb29af1ebff7517ffc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197337"
---
# <a name="c-runtime-error-r6016"></a>Chyba modulu C runtime R6016

Nedostatek místa pro data vlákna

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace se vypnula, protože má problém interní paměti. Tato chyba má mnoho možných důvodů, ale často je způsobena extrémně nízkou podmínkou paměti, chybou v aplikaci nebo chybou v doplňku nebo rozšíření používaném aplikací.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Ukončete ostatní spuštěné aplikace nebo restartujte počítač pro uvolnění paměti.
> - K opravě nebo opětovné instalaci aplikace použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Pomocí stránky **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** můžete odebrat, opravit nebo znovu nainstalovat doplňky nebo rozšíření používané aplikací.
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dochází, protože program nedostal dostatek paměti z operačního systému k dokončení [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) nebo volání `_beginthreadex` nebo Thread Local úložiště nebylo inicializováno `_beginthread` nebo `_beginthreadex`.

Při spuštění nového vlákna musí knihovna vytvořit pro toto vlákno interní databázi. Pokud databázi nelze rozšířit pomocí paměti poskytované operačním systémem, vlákno se nespustí a volající proces se zastaví. K tomu může dojít, pokud proces vytvořil příliš mnoho vláken, nebo při vyčerpání místního úložiště vláken.

Doporučujeme, aby spustitelný soubor, který volá běhovou knihovnu jazyka C (CRT), měl místo `CreateThread`rozhraní API pro Windows použít `_beginthreadex` pro vytvoření vlákna. `_beginthreadex` inicializuje interní statické úložiště, které používá mnoho funkcí CRT v thread localm úložišti. Použijete-li `CreateThread` k vytvoření vlákna, může CRT ukončit proces s R6016, když je provedeno volání funkce CRT, která vyžaduje inicializované interní statické úložiště.
