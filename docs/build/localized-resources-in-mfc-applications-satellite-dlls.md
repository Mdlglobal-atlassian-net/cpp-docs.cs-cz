---
title: "Místní zdroje v aplikacích MFC: satelitní knihovny DLL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8f601c32a1fe2accec2663246a56830fda5ed930
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Místní zdroje v aplikacích MFC: Satelitní knihovny DLL
MFC verze 7.0 nebo novější poskytuje rozšířenou podporu pro satelitní knihovny DLL, funkce, která pomáhají při vytváření aplikací lokalizovaný pro víc jazyků. Satelitní knihovny DLL je [DLL obsahuje pouze](../build/creating-a-resource-only-dll.md) obsahující prostředky aplikace, které lokalizovaný pro konkrétní jazyk. Když aplikace spustí, MFC automaticky načte lokalizovaný prostředek, který je nejvhodnější pro prostředí. Například můžete mít aplikace s anglickými prostředky s dvě satelitní knihovny DLL, jeden obsahuje francouzský překlad vašich prostředků a dalších obsahující němčině překlad. Když je aplikace spuštěna v anglické verzi systému, používá anglické prostředky. Pokud je spuštěna ve francouzštině systému, používá francouzské prostředky; Pokud je spuštěna na německém systému, používá německé prostředky.  
  
 Pro podporu lokalizované prostředky v aplikaci MFC MFC pokusí načíst satelitní knihovny DLL obsahující prostředky lokalizované pro konkrétní jazyk. Satelitní knihovny DLL jsou pojmenované *NázevAplikaceXXX*.dll, kde *ApplicationName* je název .exe nebo .dll použití prostředí MFC, a *XXX* je třípísmenný kód pro jazyk prostředky (například "ENU" nebo "DEU").  
  
 MFC, pokusí se načíst knihovnu DLL prostředku pro každý z těchto jazyků v pořadí, zastavení, pokud jej nalezne:  
  
1.  (Windows 2000 nebo vyšší) Aktuální uživatel výchozí jazyk uživatelského rozhraní, jak ho vrátila z rozhraní API Win32 GetUserDefaultUILanguage().  
  
2.  (Windows 2000 nebo vyšší) Aktuální uživatel výchozí jazyk uživatelského rozhraní, bez jakéhokoli konkrétního dílčího jazyka (tedy ŠIF [Kanadští anglické] stane ENU [USA V angličtině]).  
  
3.  Výchozí jazyk uživatelského rozhraní systému. V systému Windows 2000 nebo novější se vrátí z GetSystemDefaultUILanguage() rozhraní API. Na jiných platformách to je jazyk operačního systému.  
  
4.  Systémové výchozí jazyk uživatelského rozhraní, bez jakéhokoli konkrétního dílčího jazyka.  
  
5.  Falešný jazyk s kód 3 písmena místní  
  
 Pokud MFC nebyly nalezeny žádné satelitní knihovny DLL, používá ho, ať prostředky jsou obsažené v samotné aplikace.  
  
 Jako příklad předpokládejme, že aplikace LangExample.exe používá MFC a je spuštěna v systému Windows 2000 více uživatelského rozhraní systému; systémový jazyk uživatelského rozhraní je ENU [USA V angličtině] a jazyk uživatelského rozhraní aktuální uživatel je nastaven na FRC [francouzština (Kanada)]. MFC hledá následující knihovny DLL v následujícím pořadí:  
  
1.  LangExampleFRC.dll (jazyk uživatelského rozhraní uživatele).  
  
2.  LangExampleFRA.dll (jazyk uživatelského rozhraní uživatele bez dílčího jazyka, v tomto příkladu francouzština (Francie).  
  
3.  LangExampleENU.dll (jazyk uživatelského rozhraní systému).  
  
4.  LangExampleLOC.dll.  
  
 Pokud se nenajdou žádné z těchto knihoven DLL, používá MFC prostředky LangExample.exe.  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)   
 [TN057: Lokalizace komponent MFC](../mfc/tn057-localization-of-mfc-components.md)