---
title: Chyba příkazového řádku D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: 1bdef16b14488be86aff880db7c049f4bcddcdb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196960"
---
# <a name="command-line-error-d8016"></a>Chyba příkazového řádku D8016

Možnosti příkazového řádku možnost1 a možnost2 jsou nekompatibilní.

Možnosti příkazového řádku nelze zadat společně.

Pro specifikace možností ověřte proměnné prostředí, jako je CL.

**/CLR** implikuje **/EHa**a nelze zadat žádnou jinou možnost kompilátoru **/eh** s možností **/CLR**. Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

Po aktualizaci projektu Visual C++ 6,0 se může zobrazit D8016: proces Průvodce aktualizací projektu může povolit **/RTC** pro každý soubor zdrojového kódu v projektu, který přepíše nastavení **/RTC** projektu.  Chcete-li tento problém vyřešit, změňte nastavení **/RTC** pro každý soubor zdrojového kódu v projektu na výchozí nastavení, což znamená, že nastavení projektu pro **/RTC** bude platit pro každý soubor.

Informace o změně nastavení vlastnosti **/RTC** naleznete v tématu [/RTC (kontrola chyb za běhu)](../../build/reference/rtc-run-time-error-checks.md) .
