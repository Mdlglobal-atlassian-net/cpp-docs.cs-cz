---
title: "Národní prostředí a kódové stránky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54ab2f67a382da831ff4c1038f0269d0044f751f
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="locales-and-code-pages"></a>Národní prostředí a kódové stránky
ID národního prostředí odráží místní konvence a jazyk pro určitou zeměpisnou oblast. Daný jazyk může být používán ve více než jedné zemi nebo oblasti. Například portugalsky se hovoří v Brazílii stejně jako v Portugalsku. Naopak země nebo oblast může používat více než jeden úřední jazyk. Například Kanada používá dva jazyky: angličtinu a francouzštinu. Kanada má tedy dvě odlišná národní prostředí: kanadské s angličtinou a kanadské s francouzštinou. Ke kategoriím závislým na národním prostředí patří formátování dat nebo zobrazovací formát pro peněžní hodnoty.  
  
 Jazyk určuje konvence formátování textu a data, zatímco země nebo oblast určuje místní konvence. Každý jazyk má jedinečný mapování reprezentována znakové stránky, který obsahuje jiné znaky než ty v abecedě (například číslic a interpunkčních znamének). Znaková stránka je znaková sada a souvisí s jazyk. Jako takový [národního prostředí](../c-runtime-library/locale.md) jedinečnou kombinaci jazyka, země nebo oblast a znaková stránka. Stránka nastavení národního prostředí a kód lze změnit v době běhu voláním [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) funkce.  
  
 Různé jazyky mohou používat různé znakové stránky. Například ANSI znaková stránka 1252 se používá pro angličtinu a většina evropských jazyků a ANSI znaková stránka 932 se používá pro japonské Kanji. Prakticky všechny znakové stránky sdílet sadu pro nejnižší 128 znaků (0x00 do 0x7F) znaků ASCII.  
  
 Jakákoli jednobajtová znaková stránka může být reprezentován v tabulce (s 256 položky) jako mapování bajt hodnot znaků (včetně číslic a interpunkčních znamének), nebo glyfů. Všechny vícebajtové znakové stránky může také reprezentována jako velmi velké tabulky (s položkami 64 tisíc) hodnot dvoubajtových znaků. V praxi ale jsou obvykle reprezentovány jako tabulku pro první 256 znaků (jednobajtové) a jako rozsahy pro dvoubajtové hodnoty.  
  
 Další informace o znakové stránky najdete v tématu [znakové stránky](../c-runtime-library/code-pages.md).  
  
 Knihovny runtime jazyka C obsahují dva typy vnitřních znakových stránek: národní prostředí a vícebajtové. Při spuštění programu můžete změnit aktuální znaková stránka (naleznete v dokumentaci k [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) a [_setmbcp](../c-runtime-library/reference/setmbcp.md) funkce). Běhové knihovny může také získat a použít hodnotu znaková stránka operačního systému, což je konstantní po dobu trvání provádění tohoto programu.  
  
 Když znaková stránka národního prostředí změní, chování závislých na národním prostředí sadu funkcí se změní podle zvolené znakové stránky. Ve výchozím nastavení začínají všech funkcí závislých na národním prostředí se znaková stránka národního prostředí jedinečné pro národní prostředí "C". Znaková stránka interní národního prostředí (stejně jako ostatní vlastnosti specifické pro národní prostředí) můžete změnit pomocí volání `setlocale` funkce. Volání `setlocale`(LC_ALL, "") nastaví národní prostředí podle národního prostředí uživatele operačního systému.  
  
 Podobně když vícebajtové znakové stránky změní, chování vícebajtových funkcí se změní podle zvolené znakové stránky. Ve výchozím nastavení všechny vícebajtové funkce zahájit provádění vícebajtové znakové stránky, odpovídající operační systém výchozí znaková stránka. Interní vícebajtové znakové stránky lze změnit pomocí volání `_setmbcp` funkce.  
  
 Běhové funkce C `setlocale` nastaví, změní nebo dotazuje některých nebo všech informací o národním prostředí aktuálním programem. [_Wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) rutiny je verze široká charakterová `setlocale`; argumenty a návratové hodnoty `_wsetlocale` jsou široká charakterová řetězce.  
  
## <a name="see-also"></a>Viz také  
 [Kódování Unicode a MBCS](../text/unicode-and-mbcs.md)   
 [Výhody přenositelnosti znakové sady](../text/benefits-of-character-set-portability.md)