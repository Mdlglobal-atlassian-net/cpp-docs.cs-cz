---
title: 'Kurz: vcperf a Windows Performance Analyzer'
description: Návod, jak používat vcperf a WPA pro analýzu trasování sestavení C++.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c22f3dfddfd346d4f0eee898cb5164fd8923336e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323413"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>Kurz: vcperf a Windows Performance Analyzer

::: moniker range="<=vs-2017"

Nástroje Přehledy sestavení C++ jsou dostupné ve Visual Studiu 2019. Chcete-li zobrazit dokumentaci pro tuto verzi, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range="vs-2019"

V tomto kurzu se dozvíte, jak pomocí *vcperf.exe* shromažďovat trasování sestavení Jazyka C++. Dozvíte se také, jak zobrazit toto trasování v nástroji Windows Performance Analyzer.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Krok 1: Instalace a konfigurace nástroje Windows Performance Analyzer

WPA je prohlížeč trasování dostupný v systému Windows Assessment and Deployment Kit (ADK). Jedná se o samostatný nástroj, který není součástí součástí, které můžete nainstalovat pomocí instalačního programu sady Visual Studio.

Verze WPA, která podporuje Přehledy sestavení C++, je momentálně dostupná jenom ve Windows ADK Insider Preview. Chcete-li získat přístup k této verzi preview, musíte se zaregistrovat do [programu Windows Insider](https://insider.windows.com). Abyste získali náhled Windows ADK, nemusíte instalovat operační systém Windows 10 Insider Preview. Účet Microsoft stačí zaregistrovat v programu Windows Insider.

### <a name="to-download-and-install-wpa"></a>Stažení a instalace wpa

Poznámka: Windows 8 nebo vyšší je nutné pro instalaci Windows Performance Analyzer.

1. Přejděte na [stránku pro stažení programu](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewADK)Windows ADK Insider Preview .

1. Stáhněte si náhled Windows ADK Insider. Je to obraz disku.

1. Otevřete bitovou kopii disku a spusťte instalační program *adksetup.exe.*

1. Po zobrazení výzvy k zadání funkcí, které chcete nainstalovat, vyberte **sadu Windows Performance Toolkit**. Pokud chcete, můžete vybrat další funkce, ale nejsou nutné k instalaci WPA.

   ![Obrazovka pro výběr funkcí nástroje Windows Performance Analyzeer](media/wpa-installation.png)

### <a name="to-configure-build-insights"></a><a name="configuration-steps"></a>Konfigurace přehledů sestavení

1. Spusťte WPA.

1. Vyberte **možnost Vybrat** > **tabulky okna (experimentální).**

1. Přejděte dolů do části **Diagnostika.**

1. Vyberte všechna zobrazení Přehledy sestavení MSVC.

   ![Panel pro výběr tabulky nástroje Windows Performance Analyzer](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Krok 2: Sledování sestavení pomocí vcperf.exe

Chcete-li zobrazit data přehledů sestavení jazyka C++, nejprve je shromážděte do trasovacího souboru následujícím postupem:

1. Otevřete nativní nástroje nebo příkazový řádek pro vývojáře cross tools pro Visual Studio 2019 v režimu správce. (Klepněte pravým tlačítkem myši na položku nabídky Start a zvolte **Další** > **spuštění jako správce**.)

1. Do okna příkazového řádku zadejte tento příkaz:

   **vcperf.exe /start _SessionName_**

   Zvolte název relace, který si zapamatujete pro *Název relace*.

1. Sestavte si svůj projekt, jak byste normálně. K sestavení není nutné používat stejné okno příkazového řádku.

1. Do okna příkazového řádku zadejte tento příkaz:

   **vcperf.exe /stop _SessionName_ _traceFile.etl_**

   Použijte stejný název relace, který jste zvolili pro *SessionName* dříve. Zvolte příslušný název trasovacího souboru *traceFile.etl.*

Zde je to, co typické *vcperf.exe* příkaz sekvence vypadá v okně příkazového řádku vývojáře:

![Jednoduchý scénář použití vcperf.exe](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Důležité poznámky o vcperf.exe

- Oprávnění správce jsou vyžadována ke spuštění nebo zastavení trasování *vcperf.exe.* Použijte okno příkazového řádku pro vývojáře, které otevřete pomocí **příkazu Spustit jako správce**.

- V počítači může být spuštěna pouze jedna relace trasování současně.

- Nezapomeňte si zapamatovat název relace, který jste použili ke spuštění trasování. Může být problematické zastavit spuštěnou relaci bez znalosti jejího názvu.

- Stejně jako *cl.exe* a *link.exe*, nástroj příkazového řádku *vcperf.exe* je součástí instalace MSVC. K získání této součásti nejsou nutné žádné další kroky.

- *vcperf.exe* shromažďuje informace o všech nástrojích MSVC spuštěných ve vašem systému. V důsledku toho není třeba spustit sestavení ze stejného příkazového řádku, který jste použili ke shromažďování trasování. Projekt můžete sestavit z jiného příkazového řádku nebo dokonce z visual studia.

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Krok 3: Zobrazení trasování v nástroji Windows Performance Analyzer

Spusťte WPA a otevřete stopu, kterou jste právě shromáždili. WPA by ho měla rozpoznat jako trasování přehledů sestavení c++ a následující zobrazení by se měla zobrazit v panelu Průzkumník a graf vlevo:

- Průzkumník sestavení
- Soubory
- Funkce

Pokud tato zobrazení nevidíte, zkontrolujte, zda je wpa správně nakonfigurováno, jak je popsáno v [kroku 1](#configuration-steps). Data sestavení můžete zobrazit přetažením pohledů do prázdného okna analýzy vpravo, jak je znázorněno zde:

![Zobrazení trasování přehledů sestavení c++ v nástroji Windows Performance Analyzer](media/wpa-viewing-trace.gif)

Další pohledy jsou k dispozici v panelu Průzkumník a grafů. Přetáhněte je do okna Analýza, když vás zajímají informace, které obsahují. Užitečným je zobrazení PROCESORU (Ukázkové), které zobrazuje využití procesoru v celém sestavení.

## <a name="more-information"></a>Další informace

[Kurz: Základy nástroje Windows Performance Analyzer](wpa-basics.md)\
Seznamte se s běžnými operacemi WPA, které vám můžou pomoct analyzovat trasování sestavení.

[Reference: příkazy vcperf](/cpp/build-insights/reference/vcperf-commands)\
Odkaz na příkaz *vcperf.exe* obsahuje všechny dostupné možnosti příkazu.

[Reference: Zobrazení nástroje Windows Performance Analyzer](/cpp/build-insights/reference/wpa-views)\
Podrobnosti o zobrazeních přehledů sestavení c++ v wpa naleznete v tomto článku.

[Analyzátor výkonu systému Windows](/windows-hardware/test/wpt/windows-performance-analyzer)\
Oficiální dokumentační web WPA.

::: moniker-end
