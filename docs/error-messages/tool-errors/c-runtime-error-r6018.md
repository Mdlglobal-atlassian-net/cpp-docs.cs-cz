---
title: Chyba modulu C runtime R6018
ms.date: 11/04/2016
f1_keywords:
- R6018
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
ms.openlocfilehash: 83ad191fe1518e5e6bab0798840415ef392db71e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197285"
---
# <a name="c-runtime-error-r6018"></a>Chyba modulu C runtime R6018

Neočekávaná chyba haldy

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace byla vypnuta, protože došlo k vnitřnímu problému. Tato chyba může mít několik možných důvodů, ale často je způsobena nedostatkem kódu aplikace.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

V programu došlo k neočekávané chybě při provádění operace správy paměti.

K této chybě obvykle dochází v případě, že program nechtěně změní data haldy běhu. Může to ale být způsobeno také vnitřní chybou v kódu modulu runtime nebo operačního systému.

Pokud chcete tento problém vyřešit, vyhledejte v kódu chyby poškození haldy. Další informace a příklady najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Dále ověřte, že používáte nejnovější distribuovatelné součásti pro nasazení aplikace. Informace najdete v tématu [nasazení v vizuálu C++ ](../../windows/deployment-in-visual-cpp.md).
