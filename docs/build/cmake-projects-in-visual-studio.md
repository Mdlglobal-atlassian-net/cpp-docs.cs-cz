---
title: CMake projekty v sadě Visual Studio
description: Jak vytvořit a vytvořit projekty jazyka C++ pomocí CMake v sadě Visual Studio.
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 49ba53eaa8ac075ab6d3b2a66f33160c5c3ec410
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329164"
---
# <a name="cmake-projects-in-visual-studio"></a>CMake projekty v sadě Visual Studio

CMake je multiplatformní, open source nástroj pro definování procesů sestavení, které běží na více platformách. Tento článek předpokládá, že jste obeznámeni s CMake. Můžete se dozvědět více o tom [na sestavení, test a balíček softwaru s CMake](https://cmake.org/).

> [!NOTE]
> CMake se stala více a více integrovány s Visual Studio v posledních několika verzích. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

**Nástroje C++ CMake pro** součást Windows používají funkci Otevřít [složku](open-folder-projects-cpp.md) ke spotřebování souborů projektu CMake (například *CMakeLists.txt)* přímo pro účely technologie IntelliSense a procházení. Jsou podporovány generátory Ninja i Visual Studio. Pokud používáte generátor sady Visual Studio, generuje dočasný soubor projektu a předá jej msbuild.exe. Projekt se však nikdy nenačte pro účely technologie IntelliSense nebo procházení. Můžete také importovat existující mezipaměť CMake.

## <a name="installation"></a>Instalace

**Nástroje C++ CMake pro Windows** se instalují jako součást **vývoje plochy s c++** a **linuxovým vývojem s úlohami C++.** Další informace naleznete [v tématu Projekty CMake mezi platformami](../linux/cmake-linux-project.md).

![Komponenta CMake v pracovním zatížení plochy c++](media/cmake-install-2019.png)

Další informace naleznete [v tématu Instalace zatížení C++ Linuxu ve Visual Studiu](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integrace integrovaného vývojového prostředí (IDE)

Když zvolíte **Soubor > Otevřít > složku** a otevřete složku obsahující soubor *CMakeLists.txt,* dojde k následujícím akcím:

- Visual Studio přidá položky **CMake** do nabídky **Projekt** s příkazy pro zobrazení a úpravy skriptů CMake.

- **Průzkumník řešení** zobrazí strukturu složek a soubory.

- Visual Studio spustí cmake.exe a generuje soubor mezipaměti CMake (*CMakeCache.txt)* pro výchozí konfiguraci (x64 Debug). Příkazový řádek CMake se zobrazí ve **výstupním okně**spolu s dalším výstupem z CMake.

- Na pozadí visual studio začne indexovat zdrojové soubory, aby povolilo technologie IntelliSense, informace o procházení, refaktoring a tak dále. Při práci Visual Studio monitoruje změny v editoru a také na disku, aby jeho index v synchronizaci se zdroji.

Můžete otevřít složky obsahující libovolný počet projektů CMake. Visual Studio detekuje a konfiguruje všechny "kořenové" soubory *CMakeLists.txt* ve vašem pracovním prostoru. Operace CMake (konfigurace, sestavení, ladění), C++ IntelliSense a procházení jsou k dispozici pro všechny projekty CMake ve vašem pracovním prostoru.

![Projekt CMake s více kořeny](media/cmake-multiple-roots.png)

Můžete také zobrazit projekty uspořádané logicky podle cílů. Z **rozevíracího** přehledu cíle zvolte z rozbalovací nabídky na panelu nástrojů **Průzkumník řešení:**

![Tlačítko zobrazení cílů CMake](media/cmake-targets-view.png)

Kliknutím na tlačítko **Zobrazit všechny soubory** v horní části **Průzkumníka řešení** zobrazíte veškerý výstup generovaný cmakem ve *složkách>out/build/config.\<*

Visual Studio používá konfigurační soubor s názvem **CMakeSettings.json**. Tento soubor umožňuje definovat a ukládat více konfigurací sestavení a pohodlně mezi nimi přepínat v ide. *Konfigurace* je visual studio konstrukce, která zapouzdřuje nastavení, které jsou specifické pro daný typ sestavení. Nastavení slouží ke konfiguraci výchozích možností příkazového řádku, které visual studio předá cmake.exe. Můžete také zadat další možnosti CMake zde a definovat všechny další proměnné se vám líbí. Všechny možnosti jsou zapsány do mezipaměti CMake jako interní nebo externí proměnné. V Sadě Visual Studio 2019 poskytuje **Editor nastavení CMake** pohodlný způsob úprav nastavení. Další informace naleznete v [tématu Customize CMake settings](customize-cmake-settings.md).

Jedno nastavení `intelliSenseMode` není předáno CMake, ale používá se pouze visual studio.

Použijte soubor **CMakeLists.txt** v každé složce projektu stejně jako v každém projektu CMake. Můžete určit zdrojové soubory, najít knihovny, nastavit možnosti kompilátoru a propojovacího programu a zadat další informace související se systémem sestavení.

Chcete-li předat argumenty spustitelnému souboru v době ladění, můžete použít jiný soubor nazvaný **launch.vs.json**. V některých případech Visual Studio automaticky generuje tyto soubory. Můžete je upravit ručně nebo dokonce vytvořit soubor sami.

> [!NOTE]
> Pro jiné typy projektů otevřít složku se používají dva další soubory JSON: **CppProperties.json** a **tasks.vs.json**. Ani jeden z nich jsou relevantní pro projekty CMake.

## <a name="open-an-existing-cache"></a>Otevření existující mezipaměti

Když otevřete existující soubor mezipaměti CMake (*CMakeCache.txt*), Visual Studio se nepokouší spravovat mezipaměť a vytvořit strom za vás. Vaše vlastní nebo upřednostňované nástroje mají úplnou kontrolu nad tím, jak CMake konfiguruje váš projekt. Chcete-li otevřít existující mezipaměť v sadě Visual Studio, zvolte **Soubor > Otevřít > CMake**. Potom přejděte na existující soubor *CMakeCache.txt.*

Do otevřeného projektu můžete přidat existující mezipaměť CMake. Je to stejným způsobem, jakým byste přidali novou konfiguraci. Další informace najdete v našem příspěvku blogu o [otevření existující mezipaměti v sadě Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Vytváření projektů CMake

Chcete-li vytvořit projekt CMake, máte tyto možnosti:

1. V panelu nástrojů Obecné vyhledejte rozevírací informace **konfigurace.** Pravděpodobně ukazuje "x64-Debug" ve výchozím nastavení. Vyberte upřednostňovanou konfiguraci a stiskněte **klávesu F5**nebo klepněte na tlačítko **Spustit** (zelený trojúhelník) na panelu nástrojů. Projekt se automaticky vytvoří jako první, stejně jako řešení sady Visual Studio.

1. Klikněte pravým tlačítkem myši na *soubor CMakeLists.txt* a z kontextové nabídky vyberte **build.** Pokud máte ve struktuře složek více cílů, můžete vytvořit všechny nebo pouze jeden konkrétní cíl.

1. V hlavní nabídce vyberte **Build > Build All** **(F7** nebo **Ctrl+Shift+B**). Ujistěte se, že cíl CMake je již vybrán v rozevíracím **seznamu Položka po spuštění** na panelu nástrojů **Obecné.**

![Příkaz nabídky sestavení CMake](media/cmake-build-menu.png "CMake sestavení příkaz ové nabídky")

Jak byste očekávali, výsledky sestavení jsou zobrazeny ve **výstupním okně** a **seznamu chyb**.

![CMake chyby sestavení](media/cmake-build-errors.png "CMake chyby sestavení")

Ve složce s více cíli sestavení můžete určit, který cíl CMake má být sestavován: Chcete-li cíl určit, zvolte položku **Sestavení** v nabídce **CMake** nebo kontextovou nabídku *CMakeLists.txt.* Pokud zadáte **Ctrl+Shift+B** v projektu CMake, vytvoří aktuální aktivní dokument.

## <a name="debugging-cmake-projects"></a>Ladění projektů CMake

Chcete-li ladit projekt CMake, zvolte upřednostňovanou konfiguraci a stiskněte **klávesu F5**nebo stiskněte tlačítko **Spustit** na panelu nástrojů. Pokud je na tlačítku **Spustit** uvedeno "Vybrat položku po spuštění", vyberte šipku rozevíracího seznamu. Vyberte cíl, který chcete spustit. (V projektu CMake je možnost "Aktuální dokument" platná pouze pro soubory CPP.)

![Tlačítko CMake run](media/cmake-run-button.png "Tlačítko CMake run")

**Příkazy Run** nebo **F5** nejprve sestavení projektu, pokud byly provedeny změny od předchozího sestavení. Změny *CMakeSettings.json* způsobit CMake mezipaměti, které mají být generovány.

Relaci ladění CMake můžete přizpůsobit nastavením vlastností v souboru **launch.vs.json.** Další informace naleznete [v tématu Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md).

## <a name="just-my-code-for-cmake-projects"></a>Jen můj kód pro projekty CMake

Při vytváření pro Windows pomocí kompilátoru MSVC, CMake projekty mají podporu pouze můj kód ladění. Chcete-li změnit nastavení Pouze můj kód, přejděte na**obecné****ladění** > **možností** >  **nástrojů** > .

## <a name="vcpkg-integration"></a>Integrace Vcpkg

Pokud jste nainstalovali [vcpkg](vcpkg.md), projekty CMake otevřené v sadě Visual Studio automaticky integrují soubor řetězce nástrojů vcpkg. To znamená, že žádná další konfigurace je nutné použít vcpkg s cmake projekty. Tato podpora funguje jak pro místní instalace vcpkg, tak pro instalace vcpkg ve vzdálených systémech, na které cílíte. Toto chování je automaticky zakázáno, když zadáte další řetězec nástrojů v konfiguraci Nastavení CMake.

## <a name="customize-configuration-feedback"></a>Přizpůsobení zpětné vazby ke konfiguraci

Ve výchozím nastavení je většina konfiguračních zpráv potlačena, pokud nedojde k chybě. Všechny zprávy můžete zobrazit povolením této funkce v **nástroji** > **Možnosti** > **CMake**.

   ![Konfigurace možností diagnostiky CMake](media/vs2019-cmake-configure-options.png "CMake diagnostické možnosti")

## <a name="editing-cmakeliststxt-files"></a>Úpravy souborů CMakeLists.txt

Chcete-li upravit soubor *CMakeLists.txt,* klepněte pravým tlačítkem myši na soubor v **Průzkumníku řešení** a zvolte **Otevřít**. Pokud v souboru provedete změny, zobrazí se žlutý stavový řádek s informací, že se technologie IntelliSense aktualizuje. To vám dává možnost zrušit operaci aktualizace. Informace o *souboru CMakeLists.txt*naleznete v [dokumentaci k souboru CMake](https://cmake.org/documentation/).

   ![Úpravy souborů CMakeLists.txt](media/cmake-cmakelists.png "Úpravy souborů CMakeLists.txt")

Jakmile soubor uložíte, krok konfigurace se automaticky spustí znovu a zobrazí informace v okně **Výstup.** Chyby a upozornění jsou zobrazeny v okně **Seznam chyb** nebo **Výstup.** Poklepáním na chybu v **seznamu chyb** přejděte na problematický řádek v *souboru CMakeLists.txt*.

   ![Chyby souboru CMakeLists.txt](media/cmake-cmakelists-error.png "Chyby souboru CMakeLists.txt")

## <a name="cmake-configure-step"></a>Krok konfigurace cMake

Pokud provedete významné změny souborů *CMakeSettings.json* nebo *CMakeLists.txt,* Visual Studio automaticky znovu spustí krok konfigurace CMake. Pokud krok konfigurace skončí bez chyb, shromážděné informace jsou k dispozici v c++ IntelliSense a jazykových služeb. Používá se také v operacích sestavení a ladění.

## <a name="troubleshooting-cmake-cache-errors"></a>Poradce při potížích s chybami mezipaměti CMake

Pokud potřebujete další informace o stavu mezipaměti CMake pro diagnostiku problému, otevřete hlavní nabídku **aplikace Project** nebo kontextovou nabídku *CMakeLists.txt* v **Průzkumníku řešení** a spusťte jeden z těchto příkazů:

- **Mezipaměť zobrazení** otevře soubor *CMakeCache.txt* z kořenové složky sestavení v editoru. (Všechny úpravy, které zde provedete, na *Soubor CMakeCache.txt* budou vymazány, pokud vyčistíte mezipaměť. Chcete-li provést změny, které přetrvávají i po vyčištění mezipaměti, přečtěte si informace [o přizpůsobení nastavení CMake](customize-cmake-settings.md).)

- **Otevřít složku mezipaměti** otevře okno Průzkumníka do kořenové složky sestavení.

- **Čistá mezipaměť** odstraní kořenovou složku sestavení, takže další krok konfigurace CMake spustí z čisté mezipaměti.

- **Generovat mezipaměť** vynutí spuštění kroku generování, i když visual studio považuje prostředí za aktuální.

Automatické generování mezipaměti lze zakázat v dialogovém **okně Nástroje > možnosti > CMake > Obecné.**

## <a name="run-cmake-from-the-command-line"></a>Spuštění cmake z příkazového řádku

Pokud jste nainstalovali CMake z Instalační služby sady Visual Studio, můžete ji spustit z příkazového řádku následujícím postupem:

1. Spusťte příslušný vsdevcmd.bat (x86/x64). Další informace naleznete v [tématu Budova na příkazovém řádku](building-on-the-command-line.md).

1. Přepněte do výstupní složky.

1. Spusťte CMake a vytvořte nebo nakonfigurujte aplikaci.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 má bohatou podporu pro CMake, včetně [projektů CMake napříč platformami](../linux/cmake-linux-project.md). **Komponenta Visual C++ Tools for CMake** používá funkci **Otevřít složku** k tomu, aby ide mohlo využívat soubory projektu CMake (například *CMakeLists.txt)* přímo pro účely technologie IntelliSense a procházení. Jsou podporovány generátory Ninja i Visual Studio. Pokud používáte generátor sady Visual Studio, generuje dočasný soubor projektu a předá jej msbuild.exe. Projekt se však nikdy nenačte pro účely technologie IntelliSense nebo procházení. Můžete také importovat existující mezipaměť CMake.

## <a name="installation"></a>Instalace

**Visual C++ Tools for CMake** je nainstalován jako součást **vývoje plochy s C++** a **Linux Development s c++** úlohy.

![Komponenta CMake v pracovním zatížení plochy c++](media/cmake-install.png)

Další informace naleznete [v tématu Instalace zatížení C++ Linuxu ve Visual Studiu](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integrace ide

Když zvolíte **Soubor > Otevřít > složku** a otevřete složku obsahující soubor *CMakeLists.txt,* dojde k následujícím akcím:

- Visual Studio přidá položku nabídky **CMake** do hlavní nabídky s příkazy pro zobrazení a úpravy skriptů CMake.

- **Průzkumník řešení** zobrazí strukturu složek a soubory.

- Visual Studio spustí CMake.exe a volitelně generuje mezipaměť CMake pro výchozí *konfiguraci*, což je ladění x86. Příkazový řádek CMake se zobrazí ve **výstupním okně**spolu s dalším výstupem z CMake.

- Na pozadí visual studio začne indexovat zdrojové soubory, aby povolilo technologie IntelliSense, informace o procházení, refaktoring a tak dále. Při práci Visual Studio monitoruje změny v editoru a také na disku, aby jeho index v synchronizaci se zdroji.

Můžete otevřít složky obsahující libovolný počet projektů CMake. Visual Studio detekuje a konfiguruje všechny "kořenové" soubory *CMakeLists.txt* ve vašem pracovním prostoru. Operace CMake (konfigurace, sestavení, ladění), C++ IntelliSense a procházení jsou k dispozici pro všechny projekty CMake ve vašem pracovním prostoru.

![Projekt CMake s více kořeny](media/cmake-multiple-roots.png)

Můžete také zobrazit projekty uspořádané logicky podle cílů. Z **rozevíracího** přehledu cíle zvolte z rozbalovací nabídky na panelu nástrojů **Průzkumník řešení:**

![Tlačítko zobrazení cílů CMake](media/cmake-targets-view.png)

Visual Studio používá soubor s názvem *CMakeSettings.json* k ukládání proměnných prostředí nebo možností příkazového řádku pro Cmake.exe. *CMakeSettings.json* také umožňuje definovat a ukládat více konfigurací sestavení CMake. Můžete pohodlně přepínat mezi nimi v ide.

V opačném případě použijte *soubor CMakeLists.txt* stejně jako v libovolném projektu CMake k určení zdrojových souborů, hledání knihoven, nastavení možností kompilátoru a propojovacího programu a určení dalších informací týkajících se systému sestavení.

Pokud potřebujete předat argumenty spustitelnému souboru v době ladění, můžete použít jiný soubor nazvaný **launch.vs.json**. V některých případech Visual Studio automaticky generuje tyto soubory. Můžete je upravit ručně nebo dokonce vytvořit soubor sami.

> [!NOTE]
> Pro jiné typy projektů otevřít složku se používají dva další soubory JSON: **CppProperties.json** a **tasks.vs.json**. Ani jeden z nich jsou relevantní pro projekty CMake.

## <a name="import-an-existing-cache"></a>Import existující mezipaměti

Při importu existujícího souboru *CMakeCache.txt* visual studio automaticky extrahuje vlastní proměnné a vytvoří na nich předem vyplněný soubor *CMakeSettings.json.* Původní mezipaměť není žádným způsobem změněna. To může být stále používán z příkazového řádku, nebo s jakýmkoli nástrojem nebo IDE používá k jeho generování. Nový soubor *CMakeSettings.json* je umístěn vedle kořenového souboru *CMakeLists.txt*projektu . Visual Studio generuje novou mezipaměť založenou na souboru nastavení. Automatické generování mezipaměti můžete přepsat v dialogovém **okně Nástroje > možnosti > CMake > Obecné.**

Ne všechno v mezipaměti je importováno.  Vlastnosti, jako je například generátor a umístění kompilátorů jsou nahrazeny výchozí hodnoty, které je známo, že dobře pracovat s rozhraním IDE.

### <a name="to-import-an-existing-cache"></a>Import existující mezipaměti

1. V hlavní nabídce zvolte **Soubor > Otevřít > CMake**:

   ![Otevřít CMake](media/cmake-file-open.png "Soubor, Otevřít, CMake")

   Tento příkaz vyvolá Průvodce **importem CMake z mezipaměti.**

2. Přejděte na soubor *CMakeCache.txt,* který chcete importovat, a klepněte na tlačítko **OK**. Zobrazí se průvodce **Importovat projekt CMake z mezipaměti:**

   ![Import mezipaměti CMake](media/cmake-import-wizard.png "Otevření Průvodce importem mezipaměti CMake")

   Po dokončení průvodce se nový soubor *CMakeCache.txt* zobrazí v **Průzkumníku řešení** vedle kořenového souboru *CMakeLists.txt* v projektu.

## <a name="building-cmake-projects"></a>Vytváření projektů CMake

Chcete-li vytvořit projekt CMake, máte tyto možnosti:

1. V panelu nástrojů Obecné vyhledejte rozevírací informace **konfigurace.** Je to pravděpodobně ukazuje "Linux-Ladění" nebo "x64-Ladění" ve výchozím nastavení. Vyberte upřednostňovanou konfiguraci a stiskněte **klávesu F5**nebo klepněte na tlačítko **Spustit** (zelený trojúhelník) na panelu nástrojů. Projekt se automaticky vytvoří jako první, stejně jako řešení sady Visual Studio.

1. Klikněte pravým tlačítkem myši na *soubor CMakeLists.txt* a z kontextové nabídky vyberte **build.** Pokud máte ve struktuře složek více cílů, můžete vytvořit všechny nebo pouze jeden konkrétní cíl.

1. V hlavní nabídce vyberte **Build > Build Solution** (**F7** nebo **Ctrl+Shift+B**). Ujistěte se, že cíl CMake je již vybrán v rozevíracím **seznamu Položka po spuštění** na panelu nástrojů **Obecné.**

![Příkaz nabídky sestavení CMake](media/cmake-build-menu.png "CMake sestavení příkaz ové nabídky")

Konfigurace sestavení, proměnné prostředí, argumenty příkazového řádku a další nastavení můžete přizpůsobit v souboru *CMakeSettings.json.* Umožňuje provádět změny bez úprav souboru *CMakeLists.txt.* Další informace naleznete v [tématu Customize CMake settings](customize-cmake-settings.md).

Jak byste očekávali, výsledky sestavení jsou zobrazeny ve **výstupním okně** a **seznamu chyb**.

![CMake chyby sestavení](media/cmake-build-errors.png "CMake chyby sestavení")

Ve složce s více cíli sestavení můžete určit, který cíl CMake má být sestavován: Chcete-li cíl určit, zvolte položku **Sestavení** v nabídce **CMake** nebo kontextovou nabídku *CMakeLists.txt.* Pokud zadáte **Ctrl+Shift+B** v projektu CMake, vytvoří aktuální aktivní dokument.

## <a name="debugging-cmake-projects"></a>Ladění projektů CMake

Chcete-li ladit projekt CMake, zvolte upřednostňovanou konfiguraci a stiskněte **klávesu F5**. Nebo stiskněte tlačítko **Spustit** na panelu nástrojů. Pokud je na tlačítku **Spustit** uvedeno "Vybrat položku po spuštění", vyberte šipku rozevíracího seznamu a vyberte cíl, který chcete spustit. (V projektu CMake je možnost "Aktuální dokument" platná pouze pro soubory CPP.)

![Tlačítko CMake run](media/cmake-run-button.png "Tlačítko CMake run")

**Příkazy Run** nebo **F5** nejprve sestavení projektu, pokud byly provedeny změny od předchozího sestavení.

Relaci ladění CMake můžete přizpůsobit nastavením vlastností v souboru **launch.vs.json.** Další informace naleznete [v tématu Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md).

## <a name="editing-cmakeliststxt-files"></a>Úpravy souborů CMakeLists.txt

Chcete-li upravit soubor *CMakeLists.txt,* klepněte pravým tlačítkem myši na soubor v **Průzkumníku řešení** a zvolte **Otevřít**. Pokud v souboru provedete změny, zobrazí se žlutý stavový řádek s informací, že se technologie IntelliSense aktualizuje. To vám dává možnost zrušit operaci aktualizace. Informace o *souboru CMakeLists.txt*naleznete v [dokumentaci k souboru CMake](https://cmake.org/documentation/).

   ![Úpravy souborů CMakeLists.txt](media/cmake-cmakelists.png "Úpravy souborů CMakeLists.txt")

Jakmile soubor uložíte, krok konfigurace se automaticky spustí znovu a zobrazí informace v okně **Výstup.** Chyby a upozornění jsou zobrazeny v okně **Seznam chyb** nebo **Výstup.** Poklepáním na chybu v **seznamu chyb** přejděte na problematický řádek v *souboru CMakeLists.txt*.

   ![Chyby souboru CMakeLists.txt](media/cmake-cmakelists-error.png "Chyby souboru CMakeLists.txt")

## <a name="cmake-configure-step"></a>Krok konfigurace cMake

Při provádění významných změn v souborech *CMakeSettings.json* nebo *CMakeLists.txt* visual studio automaticky znovu spustí krok konfigurace CMake. Pokud krok konfigurace skončí bez chyb, shromážděné informace jsou k dispozici v c++ IntelliSense a jazykových služeb. Používá se také v operacích sestavení a ladění.

Více projektů CMake může používat stejný název konfigurace CMake (například x86-Debug). Všechny z nich jsou konfigurovány a sestaveny (ve vlastní kořenové složce sestavení), když je tato konfigurace vybrána. Můžete ladit cíle ze všech projektů CMake, které se účastní této konfigurace CMake.

   ![CMake Build Only položka nabídky](media/cmake-build-only.png "CMake Build Only položka nabídky")

Sestavení a ladění relací můžete omezit na podmnožinu projektů v pracovním prostoru. Vytvořte novou konfiguraci s jedinečným názvem v souboru *CMakeSettings.json.* Potom použít konfiguraci pouze pro tyto projekty. Pokud je tato konfigurace vybrána, technologie IntelliSense a příkazy sestavení a ladění se vztahují pouze na tyto zadané projekty.

## <a name="troubleshooting-cmake-cache-errors"></a>Poradce při potížích s chybami mezipaměti CMake

Pokud potřebujete další informace o stavu mezipaměti CMake pro diagnostiku problému, otevřete hlavní nabídku **CMake** nebo kontextovou nabídku *CMakeLists.txt* v **Průzkumníku řešení** a spusťte jeden z těchto příkazů:

- **Mezipaměť zobrazení** otevře soubor *CMakeCache.txt* z kořenové složky sestavení v editoru. (Všechny úpravy, které zde provedete, na *Soubor CMakeCache.txt* budou vymazány, pokud vyčistíte mezipaměť. Chcete-li provést změny, které přetrvávají i po vyčištění mezipaměti, přečtěte si informace [o přizpůsobení nastavení CMake](customize-cmake-settings.md).)

- **Otevřít složku mezipaměti** otevře okno Průzkumníka do kořenové složky sestavení.

- **Čistá mezipaměť** odstraní kořenovou složku sestavení, takže další krok konfigurace CMake spustí z čisté mezipaměti.

- **Generovat mezipaměť** vynutí spuštění kroku generování, i když visual studio považuje prostředí za aktuální.

Automatické generování mezipaměti lze zakázat v dialogovém **okně Nástroje > možnosti > CMake > Obecné.**

## <a name="single-file-compilation"></a>Kompilace jednoho souboru

Chcete-li vytvořit jeden soubor v projektu CMake, klepněte pravým tlačítkem myši na soubor v **Průzkumníku řešení**. Z rozbalovací nabídky zvolte **Kompilovat.** Můžete také vytvořit aktuálně otevřený soubor v editoru pomocí hlavní nabídky **CMake:**

![CMake kompilace jednoho souboru](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Spuštění cmake z příkazového řádku

Pokud jste nainstalovali CMake z Instalační služby sady Visual Studio, můžete ji spustit z příkazového řádku následujícím postupem:

1. Spusťte příslušný vsdevcmd.bat (x86/x64). Další informace naleznete v [tématu Vytváření na příkazovém řádku](building-on-the-command-line.md) .

1. Přepněte do výstupní složky.

1. Spusťte CMake a vytvořte nebo nakonfigurujte aplikaci.

::: moniker-end

::: moniker range="vs-2015"

V sadě Visual Studio 2015 mohou uživatelé sady Visual Studio pomocí [generátoru CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) ke generování souborů projektu MSBuild, které ide spotřebovává pro technologie IntelliSense, procházení a kompilaci.

::: moniker-end

## <a name="see-also"></a>Viz také

[Kurz: Vytvoření projektů napříč platformami jazyka C++ v sadě Visual Studio](get-started-linux-cmake.md)\
[Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)\
[Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)\
[Přizpůsobení nastavení sestavení CMake](customize-cmake-settings.md)\
[Odkaz na schéma CMakeSettings.json](cmakesettings-reference.md)\
[Konfigurace relací ladění CMake](configure-cmake-debugging-sessions.md)\
[Nasazení, spuštění a ladění projektu Linuxu](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake předdefinovaný odkaz na konfiguraci](cmake-predefined-configuration-reference.md)
