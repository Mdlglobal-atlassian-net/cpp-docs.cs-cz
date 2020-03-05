---
title: 'Kurz: vcperf and Windows Performance Analyzer'
description: Kurz týkající se použití vcperf a WPA k analýze C++ trasování sestavení.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 091e366da9342f2561620d975ead2f01b5439bad
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332409"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>Kurz: vcperf and Windows Performance Analyzer

::: moniker range="<=vs-2017"

Nástroje C++ pro tvorbu sestav jsou k dispozici v aplikaci Visual Studio 2019. Chcete-li zobrazit dokumentaci k této verzi, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

V tomto kurzu se naučíte, jak pomocí *vcperf. exe* shromažďovat trasování svého C++ sestavení. Naučíte se také, jak zobrazit toto trasování v nástroji Windows Performance Analyzer.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Krok 1: instalace a konfigurace analyzátoru výkonu Windows

WPA je prohlížeč trasování, který je k dispozici v sadě Windows Assessment and Deployment Kit (ADK). Jedná se o samostatný nástroj, který není součástí komponent, které můžete nainstalovat pomocí instalačního programu sady Visual Studio.

Verze WPA, která podporuje C++ Build Insights, je aktuálně dostupná jenom ve Windows ADK Insider Preview. Pokud chcete získat přístup k této verzi Preview, musíte se zaregistrovat do [programu Windows Insider](https://insider.windows.com). Abyste získali Windows ADK Preview, nemusíte instalovat operační systém Windows 10 Insider Preview. Musíte zaregistrovat účet Microsoft v programu Windows Insider.

### <a name="to-download-and-install-wpa"></a>Stažení a instalace WPA

Poznámka: pro instalaci analyzátoru výkonu Windows se vyžaduje systém Windows 8 nebo novější.

1. Přejděte na [stránku pro stažení](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewADK)Windows ADK Insider Preview.

1. Stáhněte si Windows ADK Insider Preview. Jedná se o bitovou kopii disku.

1. Otevřete image disku a spusťte instalační program *adksetup. exe* .

1. Po zobrazení výzvy k zadání funkcí, které chcete nainstalovat, vyberte **sadu Windows Performance Toolkit**. Pokud chcete, můžete vybrat jiné funkce, ale není nutné instalovat WPA.

   ![Obrazovka výběru funkcí instalačního programu analyzátoru výkonu systému Windows](media/wpa-installation.png)

### <a name="configuration-steps"></a>Konfigurace přehledů sestavení

1. Spusťte WPA.

1. Vyberte **okno** > **Vybrat tabulky (experimentální)** .

1. Přejděte dolů do části **Diagnostika** .

1. Vyberte všechna zobrazení MSVC Build Insights.

   ![Panel výběru tabulky pro nástroj Windows Performance Analyzer](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>Krok 2: trasování sestavení pomocí vcperf. exe

Pokud chcete C++ zobrazit data o sestavách buildu, nejdřív je Shromážděte do trasovacího souboru pomocí následujících kroků:

1. Otevřete v režimu správce nativní nástroje nebo příkazový řádek pro vývojáře pro různé nástroje pro Visual Studio 2019. (Klikněte pravým tlačítkem myši na položku nabídky Start a vyberte možnost **další** > **Spustit jako správce**.)

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

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>Krok 3: zobrazení trasování v analyzátoru výkonu Windows

Spusťte WPA a otevřete právě shromážděné trasování. WPA by ho měl rozpoznat jako C++ trasování Build Insights a následující zobrazení by se měla zobrazit na panelu Průzkumník grafů vlevo:

- Průzkumník sestavení
- Soubory
- Funkce

Pokud tato zobrazení nevidíte, zkontrolujte, že je správně nakonfigurovaný WPA, jak je popsáno v [kroku 1](#configuration-steps). Data sestavení můžete zobrazit přetažením zobrazení do prázdného okna analýzy napravo, jak je znázorněno zde:

![Zobrazení trasování C++ Build Insights v analyzátoru výkonu Windows](media/wpa-viewing-trace.gif)

Další zobrazení jsou k dispozici na panelu Průzkumník grafů. Přetáhněte je do okna analýzy, pokud vás zajímá informace, které obsahují. To je užitečné pro zobrazení procesoru (vzorkování), které ukazuje využití procesoru v celém sestavení.

## <a name="more-information"></a>Další informace

[Kurz: Základy Windows Performance Analyzer](wpa-basics.md)\
Přečtěte si o běžných operacích WPA, které vám pomůžou analyzovat trasování sestavení.

[Reference:\ příkazy vcperf](/cpp/build-insights/reference/vcperf-commands)
Odkaz na příkaz *vcperf. exe* obsahuje seznam všech dostupných možností příkazu.

[Referenční dokumentace: zobrazení analyzátoru výkonu systému Windows](/cpp/build-insights/reference/wpa-views)\
Podrobnosti o zobrazeních přehledů C++ sestavení v WPA najdete v tomto článku.

[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)\
Oficiální web dokumentace WPA.

::: moniker-end
