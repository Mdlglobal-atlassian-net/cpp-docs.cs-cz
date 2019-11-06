---
title: Začínáme se C++ sestavami Build Insights
description: Základní přehled o tom, jak používat nástroje pro analýzu výkonu při sestavování, které jsou součástí přehledů C++ buildu.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9c31d317cd7b9c6465362e3e532db2128303f602
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633103"
---
# <a name="get-started-with-c-build-insights"></a>Začínáme se C++ sestavami Build Insights

::: moniker range="<=vs-2017"

Nástroje C++ pro tvorbu sestav jsou k dispozici v aplikaci Visual Studio 2019. Chcete-li zobrazit dokumentaci k této verzi, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

C++Přehledy buildu jsou kolekce nástrojů, které poskytují lepší přehled o řetězcích C++ nástrojů Microsoft Visual (MSVC). Nástroje shromažďují data o vašich C++ sestaveních a prezentují je ve formátu, který vám může přispět k zodpovězení běžných otázek, třeba:

- Jsou moje buildy dostatečně paralelismuované?
- Co mám zahrnout do předkompilované hlavičky (PCH)?
- Je k dispozici konkrétní kritická místa, která by se měla soustředit na zvýšení rychlosti sestavení?

Mezi dvě hlavní součásti této technologie patří nástroj příkazového řádku *vcperf. exe* a doplněk pro prohlížeč trasování WPA (Windows Performance Analyzer). Nástroj se používá ke shromažďování trasování sestavení, zatímco doplněk umožňuje jejich zobrazení v WPA. Pokud chcete začít používat tyto dva nástroje, postupujte podle těchto kroků.

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>Krok 1: instalace a konfigurace analyzátoru výkonu Windows

WPA je prohlížeč trasování, který je k dispozici v sadě Windows Assessment and Deployment Kit (ADK). Jedná se o samostatný nástroj, který není součástí komponent, které můžete nainstalovat pomocí instalačního programu sady Visual Studio.

Verze WPA, která podporuje C++ Build Insights, je aktuálně dostupná jenom ve Windows ADK Insider Preview. Pokud chcete získat přístup k této verzi Preview, musíte se zaregistrovat do [programu Windows Insider](https://insider.windows.com). Abyste získali Windows ADK Preview, nemusíte instalovat operační systém Windows 10 Insider Preview. Musíte zaregistrovat účet Microsoft v programu Windows Insider.

### <a name="to-download-and-install-wpa"></a>Stažení a instalace WPA

1. Přejděte na [stránku pro stažení](https://www.microsoft.com/software-download/windowsinsiderpreviewADK)Windows ADK Insider Preview.

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

[Základy Windows Performance Analyzer](wpa-basics.md)\
Přečtěte si o běžných operacích WPA, které vám pomůžou analyzovat trasování sestavení.

[referenční\ vcperf. exe](vcperf-reference.md)
Odkaz na příkaz *vcperf. exe* obsahuje seznam všech dostupných možností příkazu.

[Referenční\ zobrazení analyzátoru výkonu systému Windows](wpa-views-reference.md)
Podrobnosti o zobrazeních přehledů C++ sestavení v WPA najdete v tomto článku.

[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)\
Oficiální web dokumentace WPA.

::: moniker-end
