---
title: "-GENPROFILE, - FASTGENPROFILE (Generovat profilace instrumentovaného sestavení) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 028b31044d035def628785969a04c27af4699f65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="genprofile-fastgenprofile-generate-profiling-instrumented-build"></a>/ GENPROFILE, /FASTGENPROFILE (Generovat profilace instrumentovaného sestavení)
Určuje generování souboru .pgd podle linkeru pro podporu optimalizace na základě profilu (PGO).  / GENPROFILE a /FASTGENPROFILE používají různé výchozí parametry. Pomocí /GENPROFILE upřednostnit přesnost přes rychlost a použití paměti při vytváření profilu. Pomocí /FASTGENPROFILE upřednostnit menší využití paměti a rychlost přes přesnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/{GENPROFILE|FASTGENPROFILE}[:{COUNTER32|COUNTER64|EXACT|MEMMAX=#|MEMMIN=#|NOEXACT|NOPATH|NOTRACKEH|PATH|PGD=filename|TRACKEH}]   
```  
  
## <a name="remarks"></a>Poznámky  
 COUNTER32 &#124; COUNTER64  
 COUNTER32 slouží k určení použití 32-bit test čítače a COUNTER64 k určení 64-bit test čítače. Když zadáte /GENPROFILE, výchozí hodnota je COUNTER64. Když zadáte /FASTGENPROFILE, výchozí hodnota je COUNTER32.  
  
 PŘESNÁ &#124; NOEXACT  
 Tuto FUNKCI použijte k určení interlocked přírůstcích vláken pro testy paměti. NOEXACT určuje nechráněné přírůstek operací pro testy paměti. Výchozí hodnota je NOEXACT.  
  
 MEMMAX = hodnota, MEMMIN = hodnota  
 Použijte MEMMAX a MEMMIN k určení rezervace maximální a minimální velikosti pro Cvičná data v paměti. Hodnota je množství paměti tak, aby vyhradil v bajtech.  Ve výchozím nastavení tyto hodnoty jsou určeny interní heuristiky.  
  
 CESTA &#124; NOPATH  
 Použijte CESTU k určení samostatnou sadu čítačů PGO pro každý jedinečný cestu na funkci. Pomocí NOPATH lze zadat jen jednu sadu čítačů pro každou funkci.   Když zadáte /GENPROFILE, výchozí hodnota je cesta. Když zadáte /FASTGENPROFILE, výchozí hodnota je NOPATH.  
  
 TRACKEH &#124; NOTRACKEH  
 Určuje, jestli se má používat další čítače zachovat aktuální přehled, pokud jsou výjimky vyvolány během cvičení. Pomocí TRACKEH můžete zadat další čítače pro přesný počet. NOTRACKEH slouží k zadání jednoho čítače pro kód, který nepoužívá výjimek nebo který nalezen výjimky v vaše scénáře školení.  Když zadáte /GENPROFILE, výchozí hodnota je TRACKEH. Když zadáte /FASTGENPROFILE, výchozí hodnota je NOTRACKEH.  
  
 PGD = název souboru  
 Určuje název základního souboru pro soubor .pgd. Ve výchozím nastavení používá linkeru název základní spustitelné bitové kopie souboru s příponou .pgd.  
  
 Možnosti /GENPROFILE a /FASTGENPROFILE řekněte linkeru pro generování souboru profilování instrumentace potřeba k podpoře aplikace školení pro optimalizace na základě profilu (PGO). Analytické informace generované školení aplikace se používá jako vstup pro provedení cílem optimalizace celého programu během sestavení.   Můžete nastavit další možnosti k ovládání různých funkcí profilování výkonu během cvičení aplikace a sestavení. Výchozí možnosti určeného /GENPROFILE poskytnout nejpřesnější výsledky, zejména pro složitých vícevláknové aplikace. Možnost /FASTGENPROFILE využívá různé výchozí hodnoty pro dosažení vyššího výkonu během cvičení za cenu přesnost a nižší nároky na paměť.  
  
 Profilace informace se zaznamená při spuštění aplikace instrumentovaného po sestavení pomocí /GENPROFILE /FASTGENPROFILE. Tyto informace slouží linkeru při zadání možnosti /USEPROFILE. Další informace o tom, jak cvičení vaší aplikace a podrobnosti o shromažďovaných datech najdete v tématu optimalizace na základě profilu.  
  
 / Ltgc musíte zadat také v případě, že zadáte /GENPROFILE nebo /FASTGENPROFILE.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)   
 [/ LTCG (vytváření kódu v době propojování)](../../build/reference/ltcg-link-time-code-generation.md)