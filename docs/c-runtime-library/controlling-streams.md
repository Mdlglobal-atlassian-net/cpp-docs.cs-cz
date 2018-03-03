---
title: "Řídicí proudy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Controlling Streams
dev_langs:
- C++
helpviewer_keywords:
- streams, controlling
- controlling streams
- streams
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d6b2678add561eda41a7426a840b9c4ad074301
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="controlling-streams"></a>Řídicí proudy
[fopen –](../c-runtime-library/reference/fopen-wfopen.md) vrátí adresu objekt typu `FILE`. Použijte tuto adresu jako `stream` argument několik – funkce knihovny provádět různé operace v otevření souboru. Pro datový proud s bajtů všechny vstupní probíhá jako v případě, že každý znak je pro čtení voláním [fgetc –](../c-runtime-library/reference/fgetc-fgetwc.md), a všechny výstup probíhá jako v případě, že každý znak je zapsán voláním [fputc –](../c-runtime-library/reference/fputc-fputwc.md). Pro datový proud s široké, všechny vstupní probíhá jako v případě, že každý znak je pro čtení voláním [fgetwc –](../c-runtime-library/reference/fgetc-fgetwc.md), a všechny výstup probíhá jako v případě, že každý znak je zapsán voláním [fputwc –](../c-runtime-library/reference/fputc-fputwc.md).  
  
 Soubor můžete zavřít voláním [fclose –](../c-runtime-library/reference/fclose-fcloseall.md), po jejímž uplynutí adresu `FILE` objekt je neplatný.  
  
 A `FILE` objekt ukládá stav datového proudu, včetně:  
  
-   Indikátor chyby nastavit nenulové hodnoty funkcí, která zaznamená pro čtení nebo zápisu došlo k chybě.  
  
-   Indikátor end souboru ve funkci, která zaznamená konec souboru při čtení nastavení nenulové hodnoty.  
  
-   Indikátor pozice souboru Určuje další bajtů v datovém proudu pro čtení nebo zápis, pokud soubor může podporovat umísťovací požadavky.  
  
-   A [stream stavu](../c-runtime-library/stream-states.md) Určuje, zda datový proud bude přijímat čtení a zápisy a jestli nevázaný datového proudu, zaměřené na konkrétní bajtů, nebo celý zaměřené na konkrétní.  
  
-   Převod stavu pamatuje, že stav všech částečně sestaví nebo vygenerovat zobecněn vícebajtových znaků, jakož i žádný stav posunutí pro pořadí bajtů v souboru).  
  
-   Vyrovnávací paměť souboru Určuje adresu a velikost pole objekt, který funkce knihovny můžete použít ke zlepšení výkonu pro čtení a operace zápisu do datového proudu.  
  
 Nijak nemění žádné hodnotou uloženou v `FILE` objektu nebo do vyrovnávací paměti souboru, který zadáte pro použití s objektem. Nelze zkopírovat `FILE` objektu a přenositelnosti použijte adresu kopie jako `stream` argument funkce knihovny.  
  
## <a name="see-also"></a>Viz také  
 [Soubory a proudy](../c-runtime-library/files-and-streams.md)