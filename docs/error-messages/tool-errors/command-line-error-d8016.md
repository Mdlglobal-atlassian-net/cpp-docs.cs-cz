---
title: Chyba příkazového řádku D8016 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8016
dev_langs:
- C++
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c6ba57b7036aae652b9eb6d885f9105d8bf0826
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607600"
---
# <a name="command-line-error-d8016"></a>Chyba příkazového řádku D8016
Možnosti příkazového řádku "možnost1" a 'možnost2' jsou nekompatibilní  
  
 Možnosti příkazového řádku nelze zadat současně.  
  
 Proměnné prostředí, jako je například CL, pro specifikace možností lze zkontrolujte.  
  
 **/ CLR** znamená **/EHa**, a nemůžete zadat jakýkoli jiný **/EH** – možnost kompilátoru s **/CLR**. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Po aktualizaci projektu Visual C++ 6.0 se může zobrazit D8016: proces aktualizace Průvodce projektu může povolit **/RTC** pro každý soubor zdrojového kódu v projektu, který přepíše **/RTC** nastavení projektu.  Chcete-li vyřešit, změňte **/RTC** nastavení pro každý soubor zdrojového kódu v projektu na výchozí nastavení, což znamená, že nastavení projektu pro **/RTC** začnou platit pro každý soubor.  
  
 Zobrazit [/RTC (kontroly chyb za běhu)](../../build/reference/rtc-run-time-error-checks.md) informace o změně **/RTC** nastavení vlastnosti.