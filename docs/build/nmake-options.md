---
title: NMake – možnosti | Dokumentace Microsoftu
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
ms.openlocfilehash: 89f71bff1d8f64da2ad029e300fe2427235eac0a
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894522"
---
# <a name="nmake-options"></a>NMAKE – možnosti

NMake – možnosti jsou popsány v následující tabulce. Možnosti předchází lomítka (/) nebo pomlčky (-) a nejsou velká a malá písmena. Použití [! CMDSWITCHES](../build/makefile-preprocessing-directives.md) Chcete-li změnit nastavení v souboru pravidel nebo Tools.ini.

|Možnost|Účel|
|------------|-------------|
|/A|Vynutí sestavení všechny vyhodnocené cíle, i když nejsou zastaralé s ohledem na závislé položky. Nevynutí sestavení nesouvisející cíle.|
|/B|Vynutí vytvářet i v případě, že jsou si rovny časová razítka. Doporučeno pouze pro velmi rychlé zpracování systémy (řešení 2 sekundy nebo kratší dobu).|
|/C|Potlačí výchozí výstup, včetně závažné chyby nástroje NMAKE nebo upozornění, časové razítko a zprávu o autorských právech NMAKE. Potlačí upozornění vydané /K.|
|/D|Zobrazuje časové razítko každého vyhodnotí cíl a závislé a napište zprávu, když cíl neexistuje. Je užitečný v případě /P pro ladění souboru pravidel. Použití **! CMDSWITCHES** nastavení nebo Vymazat /D pro část souboru pravidel.|
|/E|Způsobí, že proměnné prostředí k přepsání souboru pravidel definice maker.|
|/ ERRORREPORT [NONE &AMP;#124; VÝZVY &AMP;#124; FRONTY &AMP;#124; ODESLAT]|Pokud nmake.exe selže v době běhu, můžete použít/errorreport odesílat informace společnosti Microsoft o tyto vnitřní chyby.<br /><br /> Další informace o/errorreport najdete v tématu [/errorreport (sestava interními chybami kompilátoru)](../build/reference/errorreport-report-internal-compiler-errors.md).|
|/F *název souboru*|Určuje *filename* jako soubor pravidel. Mezery ani tabulátory může předcházet *filename*. Zadejte /F jednou pro každý soubor pravidel. Zadat soubor pravidel ze standardního vstupu, zadat pomlčku (-) pro *filename*a končí vstup z klávesnice s F6 nebo CTRL + Z.|
|/G|Zobrazí soubory pravidel součástí! #INCLUDE – direktiva.  Zobrazit [direktivy předběžného zpracování souboru pravidel](../build/makefile-preprocessing-directives.md) Další informace.|
|/ HELP, /?|Obsahuje stručný přehled NMAKE syntaxe příkazového řádku.|
|/I|Ignoruje se ukončovací kód z všechny příkazy. Chcete-li nastavit nebo zrušit /I pro část souboru pravidel, použijte **! CMDSWITCHES**. Chcete-li ignorovat ukončovací kód pro část souboru pravidel, použijte modifikátor příkaz pomlčky (-) nebo [. Ignorovat](../build/dot-directives.md). /K přepíše, pokud jsou zadány oba.|
|/K|Pokračuje nesouvisejících závislostí, sestavování, příkaz vrátí chybu. Také vyvolá upozornění a vrátí ukončovací kód z 1. Ve výchozím nastavení NMAKE zastaví, pokud některý příkaz vrátí nenulový ukončovací kód. Upozornění z /K se potlačil na /C; /I /K přepíše, pokud jsou zadány oba.|
|/N|Zobrazí, ale nemůžou provést příkazy. jsou spouštěny příkazy předzpracování. Příkazy v rekurzivní volání NMAKE nezobrazí. Užitečné při ladění souborů pravidel a kontrola časová razítka. Chcete-li nastavit nebo zrušit /N pro část souboru pravidel, použijte **! CMDSWITCHES**.|
|/NOLOGO|Potlačí zprávu o autorských právech NMAKE.|
|/P|Zobrazí informace (definice maker, pravidla odvozování, cíle, [. PŘÍPONY](../build/dot-directives.md) seznamu) do standardního výstupu, a pak spustí sestavení. Pokud neexistuje žádný soubor pravidel nebo příkazového řádku cíl, zobrazí pouze informace. Použití s /D k ladění souboru pravidel.|
|/Q|Časová razítka kontroly cílů; sestavení nelze spustit. Vrátí nenulový ukončovací kód je-li všechny cíle jsou aktuální a nenulový ukončovací kód, pokud žádné cíl není. Jsou spouštěny příkazy předzpracování. Užitečné při spuštění příkazu NMAKE z dávkového souboru.|
|/ R|Vymaže **. PŘÍPONY** seznamu a ignoruje pravidla odvozování a makra, která jsou definována v souboru Tools.ini nebo, které jsou předdefinované.|
|/S|Potlačí zobrazení provedených příkazů. Chcete-li potlačit zobrazení v části souboru pravidel, použijte **\@** modifikátor příkaz nebo [. TICHÉ](../build/dot-directives.md). Chcete-li nastavit nebo zrušit /S pro část souboru pravidel, použijte **! CMDSWITCHES**.|
|/T|Aktualizuje časové razítko cíle příkazového řádku (nebo první cíle souboru pravidel) a spustí příkazy předzpracování ale nebude provádět sestavení.|
|/U|Je potřeba použít ve spojení s /N. Vypíše vložených NMAKE souborů tak, aby /N výstup může sloužit jako dávkového souboru.|
|/X *název souboru*|Odešle NMAKE chybový výstup do *filename* místo standardní chybu. Mezery ani tabulátory může předcházet *filename*. K odeslání chybový výstup do standardního výstupu, zadat pomlčku (-) pro *filename*. Nemá vliv na výstupu příkazů do standardní chyby.|
|/Y|Zakáže dávková odvozená pravidla. Pokud je vybraná tato možnost, všechny dávková odvozená pravidla jsou považovány za regulární odvozená pravidla.|

## <a name="see-also"></a>Viz také

[Spuštění příkazu NMAKE](../build/running-nmake.md)
