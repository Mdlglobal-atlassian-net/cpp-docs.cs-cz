---
title: "Chyba příkazového řádku D8016 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D8016
dev_langs:
- C++
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 463de86acf0446f125b66ec1cdc3768c6238b630
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-error-d8016"></a>Chyba příkazového řádku D8016
nejsou kompatibilní, 'možnost 1' a 'option2' Možnosti příkazového řádku  
  
 Možnosti příkazového řádku nelze zadat současně.  
  
 Zkontrolujte proměnné prostředí, například CL, pro možnost specifikace.  
  
 **/ CLR** znamená **/EHa**, a nelze zadat libovolný jiný **/EH** – možnost kompilátoru s **/CLR**. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Můžete obdržet D8016 po aktualizaci [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 6.0 projektu: proces projektu aktualizace Průvodce může povolit **/RTC** pro každého souboru zdrojového kódu v projektu, který přepíše **/RTC** nastavení pro projekt.  Chcete-li vyřešit, změňte **/RTC** nastavení pro každou souboru zdrojového kódu v projektu na výchozí nastavení, což znamená, že nastavení projektu pro **/RTC** bude platit pro každý soubor.  
  
 V tématu [/RTC (kontroluje chyby Run-Time)](../../build/reference/rtc-run-time-error-checks.md) informace o změně **/RTC** nastavení vlastnosti.