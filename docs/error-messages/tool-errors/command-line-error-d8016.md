---
title: Chyba příkazového řádku D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: c1e2e3e28f8556416f58d68f8ef1df4b220bc54c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399964"
---
# <a name="command-line-error-d8016"></a>Chyba příkazového řádku D8016

Možnosti příkazového řádku "možnost1" a 'možnost2' jsou nekompatibilní

Možnosti příkazového řádku nelze zadat současně.

Proměnné prostředí, jako je například CL, pro specifikace možností lze zkontrolujte.

**/ CLR** znamená **/EHa**, a nemůžete zadat jakýkoli jiný **/EH** – možnost kompilátoru s **/CLR**. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

Po aktualizaci projektu Visual C++ 6.0 se může zobrazit D8016: proces aktualizace Průvodce projektu může povolit **/RTC** pro každý soubor zdrojového kódu v projektu, který přepíše **/RTC** nastavení projektu.  Chcete-li vyřešit, změňte **/RTC** nastavení pro každý soubor zdrojového kódu v projektu na výchozí nastavení, což znamená, že nastavení projektu pro **/RTC** začnou platit pro každý soubor.

Zobrazit [/RTC (kontroly chyb za běhu)](../../build/reference/rtc-run-time-error-checks.md) informace o změně **/RTC** nastavení vlastnosti.