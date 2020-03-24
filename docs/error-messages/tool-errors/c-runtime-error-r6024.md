---
title: Chyba modulu C runtime R6024
ms.date: 11/04/2016
f1_keywords:
- R6024
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
ms.openlocfilehash: de89d2e9e2b34f40b906a5dacca4179eade23f7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197194"
---
# <a name="c-runtime-error-r6024"></a>Chyba modulu C runtime R6024

nedostatek místa pro _onexit tabulku/atexit

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace se vypnula, protože má problém interní paměti. K této chybě obvykle dochází v důsledku extrémně nízkého stavu paměti nebo v případě chyby v programu nebo poškození vizuálních C++ knihoven, které používá.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Ukončete ostatní spuštěné aplikace nebo restartujte počítač pro uvolnění paměti.
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** k opravě nebo přeinstalaci všech kopií Microsoft Visual C++ Redistributable.
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dochází, protože pro funkci `_onexit` nebo `atexit` nebyla k dispozici žádná paměť. Tato chyba je způsobena stavem nedostatku paměti. Po spuštění aplikace můžete zvážit předpřidělování vyrovnávacích pamětí, které vám pomůžou při ukládání uživatelských dat a provádění čistého ukončení aplikace v podmínkách s nedostatkem paměti.
