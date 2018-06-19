---
title: NMAKE – možnosti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, options
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2f7ad294a9f199d5dbe6821c61317ed0b6b2693
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373033"
---
# <a name="nmake-options"></a>NMAKE – možnosti
NMAKE – možnosti jsou popsané v následující tabulce. Možnosti předchází lomítko (/) nebo pomlčkou (-) a nejsou velká a malá písmena. Použití [! Cmdswitches –](../build/makefile-preprocessing-directives.md) možnost nastavení v souboru pravidel nebo v Tools.ini změnit.  
  
|Možnost|Účel|  
|------------|-------------|  
|/A|Vynutí sestavení všechny vyhodnotí cíle, i když nejsou zastaralé s ohledem na závislé objekty. Nevynutí sestavení nesouvisejícími cílů.|  
|/B|Vynutí vytvořit i v případě, že časová razítka jsou stejné. Doporučeno pouze pro velmi rychlé systémy (rozlišení dvou sekund nebo méně).|  
|/C|Potlačí výchozí výstup, včetně méně závažné chyby NMAKE nebo upozornění, časová razítka a zpráva o autorských právech NMAKE. Potlačí upozornění vystavený /K.|  
|/D|Časová razítka zobrazí jednotlivých vyhodnoceno cíle a závislé a zprávy, když cíl neexistuje. Je užitečný v případě /P pro ladění souboru pravidel. Použití **! Cmdswitches –** nastavení nebo vymazání /D pro součástí souboru pravidel.|  
|/E|Způsobí, že proměnné prostředí k přepsání souboru pravidel definice maker.|  
|/ ERRORREPORT [NONE &AMP;#124; VÝZVA &AMP;#124; FRONTY &AMP;#124; ODESLAT]|Pokud se nezdaří nmake.exe za běhu, můžete/errorreport odesílat informace společnosti Microsoft o tyto interní chyby.<br /><br /> Další informace o/errorreport najdete v tématu [/errorreport (sestava interními chybami kompilátoru)](../build/reference/errorreport-report-internal-compiler-errors.md).|  
|/F `filename`|Určuje `filename` jako souboru pravidel. Mezery nebo karty lze předcházet `filename`. Zadejte /F jednou pro každý soubor pravidel. K poskytování souboru pravidel ze standardního vstupu, zadejte pomlčkou (-) pro `filename`a končit vstup z klávesnice s F6 nebo CTRL + Z.|  
|/G|Soubory pravidel součástí zobrazí! INCLUDE – direktiva.  V tématu [předběžné zpracování direktiv souboru pravidel](../build/makefile-preprocessing-directives.md) Další informace.|  
|/ HELP, /?|Zobrazuje stručné souhrnné informace o NMAKE syntaxe příkazového řádku.|  
|/I|Ignoruje ukončovací kód z všechny příkazy. Chcete-li nastavit nebo zrušením zaškrtnutí /I pro součástí souboru pravidel, použijte **! Cmdswitches –**. Ignorovat ukončovací kód pro část souboru pravidel, použijte příkaz modifikátor pomlčky (-) nebo [. Ignorovat](../build/dot-directives.md). /K přepíše, pokud jsou zadány oba.|  
|/K|Pokračuje v sestavení nesouvisejícími závislosti, pokud příkaz vrátí chybu. Také vás upozorní a vrátí ukončovací kód 1. Ve výchozím nastavení NMAKE zastaví, pokud žádné příkaz vrátí nenulový ukončovací kód. Upozornění z /K jsou potlačit pomocí /C; /I přepíše /K, pokud jsou zadány oba.|  
|/ N|Zobrazuje však není provedena příkazy; předběžného zpracování příkazy jsou provedeny. Příkazy v rekurzivní NMAKE volání nezobrazí. Tato možnost je užitečná pro ladění soubory pravidel a kontrola časová razítka. Nastavení nebo vymazání/n pro součástí souboru pravidel, použijte **! Cmdswitches –**.|  
|/NOLOGO|Potlačí zprávu o autorských právech NMAKE.|  
|/P|Zobrazí informace (definice maker, odvozená pravidla, cíle, [. PŘÍPONY](../build/dot-directives.md) seznamu) na standardní výstup, a poté spustí sestavení. Pokud žádný soubor pravidel nebo příkazového řádku cílová existuje, zobrazí pouze informační charakter. Použití s /D k ladění souboru pravidel.|  
|/Q|Časová razítka kontroly cílů; nejde spustit sestavení. Vrátí nenulový ukončovací kód Pokud jsou všechny cíle aktuální a nenulový ukončovací kód, pokud žádné cíl není. Předběžného zpracování příkazy jsou provedeny. To užitečné, pokud se spuštění příkazu NMAKE z dávkového souboru.|  
|/R|Vymaže **. PŘÍPONY** seznamu a ignoruje odvozená pravidla a makra, které jsou definovány v souboru Tools.ini nebo které jsou předdefinovány.|  
|/S|Potlačí zobrazení spuštění příkazů. Chcete-li potlačit zobrazení v části souboru pravidel, použijte **@** příkaz modifikátor nebo [. TICHOU](../build/dot-directives.md). Chcete-li nastavit nebo zrušením zaškrtnutí /S pro součástí souboru pravidel, použijte **! Cmdswitches –**.|  
|/T|Aktualizace časového razítka příkazového řádku cíle (nebo prvního cíle makefile) a spouští příkazy předběžného zpracování, ale nespustí sestavení.|  
|/U|Musí použít ve spojení s /N. Vypíše vložené NMAKE soubory tak, aby výstup/n je možné použít jako dávkového souboru.|  
|/X `filename`|Odesílá výstup chyby NMAKE k `filename` místo standardní chyba. Mezery nebo karty lze předcházet `filename`. Chcete-li odeslat chyba výstup do standardního výstupního, zadejte pomlčkou (-) pro `filename`. Výstup z příkazů na standardní chyba neovlivňuje.|  
|/Y|Zakáže dávková odvozená pravidla. Pokud je vybraná tato možnost, všechny dávková odvozená pravidla jsou považovány za regulární odvozená pravidla.|  
  
## <a name="see-also"></a>Viz také  
 [Spuštění příkazu NMAKE](../build/running-nmake.md)