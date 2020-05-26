---
title: 'Kurz: vcperf and Windows Performance Analyzer'
description: Kurz týkající se použití vcperf a WPA k analýze trasování sestavení v jazyce C++.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 724df913400abb6d33c333f0a16c20fb982769bc
ms.sourcegitcommit: 98139766b548c55181ff5ec5ad3bfd9db2bf5c89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83865049"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>Kurz: vcperf and Windows Performance Analyzer

::: moniker range="<=vs-2017"

Nástroje C++ Build Insights jsou k dispozici v aplikaci Visual Studio 2019. Chcete-li zobrazit dokumentaci k této verzi, nastavte ovládací prvek selektor **verzí** sady Visual Studio pro tento článek na sadu visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range="vs-2019"

V tomto kurzu se naučíte, jak pomocí *vcperf. exe* shromažďovat trasování sestavení v jazyce C++. Naučíte se také, jak zobrazit toto trasování v nástroji Windows Performance Analyzer.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Krok 1: instalace a konfigurace analyzátoru výkonu Windows

WPA je prohlížeč trasování, který je k dispozici v sadě Windows Assessment and Deployment Kit (ADK). Jedná se o samostatný nástroj, který není součástí komponent, které můžete nainstalovat pomocí instalačního programu sady Visual Studio.

Verze WPA, která podporuje C++ Build Insights, je aktuálně dostupná jenom ve Windows ADK Insider Preview. Pokud chcete získat přístup k této verzi Preview, musíte se zaregistrovat do [programu Windows Insider](https://insider.windows.com). Abyste získali Windows ADK Preview, nemusíte instalovat operační systém Windows 10 Insider Preview. Musíte zaregistrovat účet Microsoft v programu Windows Insider.

### <a name="to-download-and-install-wpa"></a>Stažení a instalace WPA

Poznámka: pro instalaci analyzátoru výkonu Windows se vyžaduje systém Windows 8 nebo novější.

1. Přejděte na [stránku pro stažení](https://docs.microsoft.com/windows-hardware/get-started/adk-install)Windows ADK.

1. Stáhněte a nainstalujte si nejnovější verzi sady Windows ADK.

1. Po zobrazení výzvy k zadání funkcí, které chcete nainstalovat, vyberte **sadu Windows Performance Toolkit**. Pokud chcete, můžete vybrat jiné funkce, ale není nutné instalovat WPA.

   ![Obrazovka výběru funkcí instalačního programu analyzátoru výkonu systému Windows](media/wpa-installation.png)

### <a name="to-configure-wpa"></a><a name="configuration-steps"></a>Konfigurace WPA

Zobrazení trasování C++ Build Insights v WPA vyžaduje speciální doplněk. Pomocí těchto kroků ji nainstalujte:

1. Získejte doplněk stažením jedné z následujících součástí. Nemusíte získat obojí. Vyberte ten, který vyhledáte nejpohodlnější.
    1. [Visual Studio 2019 verze 16,6 a vyšší](https://visualstudio.microsoft.com/downloads/)nebo,
    1. [Balíček NuGet pro C++ Build Insights](https://www.nuget.org/packages/Microsoft.Cpp.BuildInsights/)

1. Zkopírujte `perf_msvcbuildinsights.dll` soubor do instalačního adresáře WPA.
    1. V aplikaci Visual Studio 2019 verze 16,6 a vyšší je tento soubor umístěný zde: `C:\Program Files (x86)\Microsoft Visual Studio\2019\{Edition}\VC\Tools\MSVC\{Version}\bin\Host{Architecture}\{Architecture}` .
    1. V balíčku NuGet pro C++ Build Insights je tento soubor umístěný tady: `wpa\{Architecture}` .
    1. Na cestách výše nahraďte proměnné obklopené složenými závorkami takto:
        1. `{Edition}`je vaše edice sady Visual Studio 2019, jako je například komunita, Professional nebo Enterprise.
        1. `{Version}`je vaše verze MSVC. Vyberte nejvyšší dostupnou.
        1. `{Architecture}`: vyberte, `x64` jestli máte 64 verzi Windows. V opačném případě vyberte `x86` .
    1. Instalační adresář WPA je typicky: `C:\Program Files (x86)\Windows Kits\10\Windows Performance Toolkit` .

1. V instalačním adresáři WPA otevřete `perfcore.ini` soubor a přidejte položku pro `perf_msvcbuildinsights.dll` .

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Krok 2: trasování sestavení pomocí vcperf. exe

Pokud chcete zobrazit data C++ Build Insights, nejdřív je Shromážděte do trasovacího souboru pomocí následujících kroků:

1. Otevřete **x64** nebo **x86 Native Tools Command Prompt pro vs 2019** v režimu správce. (Klikněte pravým tlačítkem myši na položku nabídky Start a vyberte možnost **Další**  >  . **Spustit jako správce**.)
    1. Pokud máte 64 verzi Windows, vyberte **x64** . V opačném případě vyberte **x86**.

1. V okně příkazového řádku zadejte tento příkaz:

   **vcperf. exe/start _název_relace_**

   Vyberte název relace, pro kterou si pamatujete název *relace*.

1. Sestavte projekt obvyklým způsobem. K sestavení nemusíte použít stejné okno příkazového řádku.

1. V okně příkazového řádku zadejte tento příkaz:

   **vcperf. exe/stop _název_relace_ _traceFile. ETL_**

   Použijte stejný název relace, který jste si zvolili pro *relaci* před. Vyberte vhodný název trasovacího souboru *traceFile. ETL* .

V okně příkazového řádku pro vývojáře vypadá typická sekvence příkazů *vcperf. exe* :

![Jednoduchý scénář použití vcperf. exe](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Důležité poznámky k vcperf. exe

- Ke spuštění nebo zastavení trasování *vcperf. exe* jsou nutná oprávnění správce. Použijte okno příkazového řádku pro vývojáře, které otevřete pomocí příkazu **Spustit jako správce**.

- V jednom okamžiku může být spuštěna pouze jedna relace trasování.

- Nezapomeňte si pamatovat název relace, který jste použili ke spuštění vašeho trasování. Může být komplikované zastavit běžící relaci bez znalosti jejího názvu.

- Podobně jako *CL. exe* a *Link. exe*je nástroj příkazového řádku *VCPERF. exe* součástí instalace MSVC. K získání této součásti nejsou nutné žádné další kroky.

- *vcperf. exe* shromažďuje informace o všech nástrojích MSVC spuštěných ve vašem systému. V důsledku toho nemusíte spouštět sestavení ze stejného příkazového řádku, který jste použili ke shromáždění trasování. Svůj projekt můžete sestavit buď z jiného příkazového řádku, nebo dokonce i v aplikaci Visual Studio.

### <a name="vcperfexe-is-open-source"></a>vcperf. exe je open source.

Pokud chcete sestavit a spustit svou vlastní verzi *vcperf. exe*, můžete ji naklonovat z [úložiště GitHub vcperf](https://github.com/microsoft/vcperf).

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Krok 3: zobrazení trasování v analyzátoru výkonu Windows

Spusťte WPA a otevřete právě shromážděné trasování. WPA by ho měl rozpoznat jako trasování C++ Build Insights a následující zobrazení by se měla zobrazit na panelu Průzkumník grafů vlevo:

- Průzkumník sestavení
- Soubory
- Funkce
- Instance šablon

Pokud tato zobrazení nevidíte, zkontrolujte, že je správně nakonfigurovaný WPA, jak je popsáno v [kroku 1](#configuration-steps). Data sestavení můžete zobrazit přetažením zobrazení do prázdného okna analýzy napravo, jak je znázorněno zde:

![Zobrazení trasování C++ Build Insights v analyzátoru výkonu Windows](media/wpa-viewing-trace.gif)

Další zobrazení jsou k dispozici na panelu Průzkumník grafů. Přetáhněte je do okna analýzy, pokud vás zajímá informace, které obsahují. To je užitečné pro zobrazení procesoru (vzorkování), které ukazuje využití procesoru v celém sestavení.

## <a name="more-information"></a>Další informace

[Kurz: Základy Windows Performance Analyzer](wpa-basics.md)\
Přečtěte si o běžných operacích WPA, které vám pomůžou analyzovat trasování sestavení.

[Reference: příkazy vcperf](/cpp/build-insights/reference/vcperf-commands)\
Odkaz na příkaz *vcperf. exe* obsahuje seznam všech dostupných možností příkazu.

[Referenční dokumentace: zobrazení Windows Performance Analyzer](/cpp/build-insights/reference/wpa-views)\
Podrobnosti o zobrazeních přehledů sestavení v jazyce C++ v WPA najdete v tomto článku.

[Analyzátor výkonu systému Windows](/windows-hardware/test/wpt/windows-performance-analyzer)\
Oficiální web dokumentace WPA.

::: moniker-end
