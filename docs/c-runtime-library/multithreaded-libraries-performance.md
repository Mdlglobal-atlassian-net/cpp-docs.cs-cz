---
title: Výkon vícevláknových knihoven | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], performance
- libraries, multithreaded
- performance, multithreading
- multithreaded libraries
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d738cbfe462543437ed4c620f671bb325263e3e3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390410"
---
# <a name="multithreaded-libraries-performance"></a>Výkon vícevláknových knihoven
Jednovláknové CRT již není k dispozici. Toto téma popisuje, jak získat maximální výkon z vícevláknových knihoven.  
  
## <a name="maximizing-performance"></a>Tím se maximalizuje výkon  
 Výkon vícevláknových knihoven vylepšeno a blíží výkon eliminovat nyní jednovláknové knihovny. Pro tyto situace při i vyšší výkon, je vyžadována, existuje několik nových funkcí.  
  
-   Zamykání nezávislé datového proudu umožňuje zamknout datového proudu a pak použít [funkce jazyka _nolock](../c-runtime-library/nolock-functions.md) , přímý přístup do datového proudu. To umožňuje použití zámek k být zdvihnut mimo kritické smyčky.  
  
-   Národní prostředí podle vláken snižuje náklady na přístup národního prostředí pro scénáře s více vlákny (viz [_configthreadlocale –](../c-runtime-library/reference/configthreadlocale.md)).  
  
-   Funkce závislých na národním prostředí (s názvy končící na _l) trvat národní prostředí jako parametr, odebrání významné náklady (například [printf _printf_l –, wprintf, _wprintf_l –](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)).  
  
-   Optimalizace pro běžné kódové stránky snížit náklady na krátké operací.  
  
-   Definování [_crt_disable_perfcrit_locks –](../c-runtime-library/crt-disable-perfcrit-locks.md) vynutí všechny vstupně-výstupních operací předpokládá model jednovláknové vstupně-výstupních operací a používání formulářů _nolock – funkce. To umožňuje vysoce I/E-jednovláknové aplikacím získat lepší výkon.  
  
-   Ohrožení zpracování haldy CRT umožňuje povolit systému Windows nízká fragmentace haldy (LFH) pro haldě CRT, která může výrazně zlepšit výkon v vysoce škálovat scénáře.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)