---
title: Chyba modulu C runtime R6017
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 2d868939425c11f13dffd84e28c1afee45e3b11a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197299"
---
# <a name="c-runtime-error-r6017"></a>Chyba modulu C runtime R6017

Neočekávaná chyba zámku s více vlákny

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace byla vypnuta, protože došlo k vnitřnímu problému. Tato chyba může mít několik možných důvodů, ale často je způsobena nedostatkem kódu aplikace.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

Proces obdržel neočekávanou chybu při pokusu o přístup k zámku s více vlákny v modulu C runtime na prostředku systému. K této chybě obvykle dochází, pokud proces neúmyslně změní data haldy modulu runtime. Může to ale být způsobeno také vnitřní chybou v běhové knihovně nebo kódu operačního systému.

Pokud chcete tento problém vyřešit, vyhledejte v kódu chyby poškození haldy. Další informace a příklady najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Dále ověřte, že používáte nejnovější distribuovatelné součásti pro nasazení aplikace. Informace najdete v tématu [nasazení v vizuálu C++ ](../../windows/deployment-in-visual-cpp.md).
