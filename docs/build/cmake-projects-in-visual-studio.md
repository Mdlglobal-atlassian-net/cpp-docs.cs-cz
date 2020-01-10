---
title: Projekty CMake v sadě Visual Studio
description: Jak vytvářet a sestavovat C++ projekty pomocí cmake v sadě Visual Studio.
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: be252759e93eb30d4f9b4ff1446dd4217fcdf2a6
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75791827"
---
# <a name="cmake-projects-in-visual-studio"></a>Projekty CMake v sadě Visual Studio

CMake je open source nástroj pro různé platformy, který slouží k definování procesů sestavení, které běží na různých platformách. Tento článek předpokládá, že jste obeznámeni s CMakí. Další informace o IT najdete v [sestavování, testování a zabalení softwaru pomocí cmake](https://cmake.org/).

> [!NOTE]
> Sada CMake se v sadě Visual Studio během posledních několika verzí stala více a více integrována. Pokud chcete zobrazit správné informace o verzi, kterou používáte, ujistěte se, že je správně nastavený selektor verzí v levém horním rohu této stránky.

::: moniker range="vs-2019"

Součást  **C++ cmake Tools for Windows** používá funkci [Otevřít složku](open-folder-projects-cpp.md) pro využívání souborů projektu cmake (například *CMakeLists. txt*) přímo pro účely IntelliSense a procházení. Podporují se expertem i generátory sady Visual Studio. Použijete-li generátor sady Visual Studio, vygeneruje dočasný soubor projektu a předá ho nástroji MSBuild. exe. Projekt se ale nikdy nenačte pro účely IntelliSense nebo procházení. Můžete také importovat stávající mezipaměť CMake.

## <a name="installation"></a>Instalace služby

Nástroje cmake pro Windows se instalují jako součást **vývoje desktopových aplikací s C++**  nástrojem a **vývoj pro C++ Linux s** využitím úloh. **C++** Další informace najdete v tématu [projekty cmake pro různé platformy](../linux/cmake-linux-project.md).

![Součást CMake v C++ pracovní ploše](media/cmake-install-2019.png)

Další informace najdete v tématu [instalace úlohy C++ pro Linux v aplikaci Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integrace IDE

Když vyberete **soubor > otevřít > složku** a otevřete složku obsahující soubor *CMakeLists. txt* , dojde k následujícím akcím:

- Sada Visual Studio přidá položky **cmake** do nabídky **projekt** s příkazy pro zobrazení a úpravy skriptů cmake.

- **Průzkumník řešení** zobrazuje strukturu a soubory složek.

- Sada Visual Studio spustí cmake. exe a vygeneruje soubor mezipaměti CMake (*CMakeCache. txt*) pro výchozí konfiguraci (ladění x64). V **okno výstup**se zobrazí příkazový řádek cmake spolu s dalším výstupem z cmake.

- Na pozadí Visual Studio začne indexovat zdrojové soubory, aby bylo možné povolit technologii IntelliSense, informace o procházení, refaktoring atd. Při práci Visual Studio monitoruje změny v editoru a také na disku, aby byl jeho index synchronizovaný se zdroji.

Můžete otevřít složky obsahující libovolný počet projektů CMake. Visual Studio detekuje a konfiguruje všechny "kořenové" soubory *CMakeLists. txt* v pracovním prostoru. Operace CMake (konfigurace, sestavení, ladění), C++ IntelliSense a procházení jsou k dispozici pro všechny projekty cmake v pracovním prostoru.

![Projekt CMake s více kořeny](media/cmake-multiple-roots.png)

Své projekty můžete také hierarchicky zobrazit podle cílů. V rozevíracím seznamu na panelu nástrojů **Průzkumník řešení** vyberte **zobrazení cílů** :

![Tlačítko zobrazení cílů CMake](media/cmake-targets-view.png)

Kliknutím na tlačítko **Zobrazit všechny soubory** v horní části **Průzkumník řešení** zobrazíte všechny výstupy vygenerované cmaki ve složkách *out/Build/\<config >* .

Visual Studio používá konfigurační soubor s názvem **CMakeSettings. JSON**. Tento soubor umožňuje definovat a ukládat více konfigurací sestavení a pohodlně přepínat mezi nimi v integrovaném vývojovém prostředí (IDE). *Konfigurace* je konstrukce sady Visual Studio, která zapouzdřuje nastavení specifická pro daný typ sestavení. Tato nastavení slouží ke konfiguraci výchozích možností příkazového řádku, které Visual Studio předá do cmake. exe. Tady můžete také zadat další možnosti CMake a definovat další proměnné, které chcete. Všechny možnosti jsou zapsány do mezipaměti CMake buď jako vnitřní, nebo jako externí proměnné. V sadě Visual Studio 2019 **Editor nastavení cmake** nabízí pohodlný způsob, jak upravit nastavení. Další informace najdete v tématu [přizpůsobení nastavení cmake](customize-cmake-settings.md).

Jedno nastavení `intelliSenseMode` není předáno do CMake, ale používá se pouze sada Visual Studio.

Použijte soubor **CMakeLists. txt** v každé složce projektu stejně jako v jakémkoli projektu cmake. Můžete určit zdrojové soubory, najít knihovny, nastavit možnosti kompilátoru a linkeru a zadat další informace související se systémem sestavení.

K předání argumentů spustitelnému souboru v době ladění můžete použít jiný soubor nazvaný **Launch. vs. JSON**. V některých scénářích aplikace Visual Studio tyto soubory automaticky generuje. Můžete je upravit ručně nebo dokonce vytvořit soubor sami.

> [!NOTE]
> Pro jiné druhy projektů otevřené složky se používají dva další soubory JSON: **CppProperties. JSON** a **Tasks. vs. JSON**. Ani jedna z těchto projektů není relevantní pro projekty CMake.

## <a name="open-an-existing-cache"></a>Otevřít existující mezipaměť

Když otevřete existující soubor mezipaměti CMake (*CMakeCache. txt*), Visual Studio se nepokusí spravovat mezipaměť a strom sestavení za vás. Vaše vlastní nebo preferované nástroje mají plnou kontrolu nad tím, jak CMake nakonfiguruje váš projekt. Pokud chcete otevřít existující mezipaměť v sadě Visual Studio, vyberte **soubor > otevřít > cmake**. Pak přejděte do existujícího souboru *CMakeCache. txt* .

Do otevřeného projektu můžete přidat existující mezipaměť CMake. To se provádí stejným způsobem jako při přidávání nové konfigurace. Další informace najdete v našem blogovém příspěvku o [otevření existující mezipaměti v aplikaci Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Sestavování projektů CMake

Chcete-li vytvořit projekt CMake, máte tyto možnosti:

1. Na panelu nástrojů obecné Najděte rozevírací seznam **Konfigurace** . Ve výchozím nastavení se pravděpodobně zobrazuje "x64-debug". Vyberte upřednostňovanou konfiguraci a stiskněte klávesu **F5**nebo klikněte na tlačítko **Spustit** (zelený trojúhelník) na panelu nástrojů. Projekt se nejprve automaticky sestaví jako řešení sady Visual Studio.

1. Klikněte pravým tlačítkem na *CMakeLists. txt* a v místní nabídce vyberte **sestavit** . Pokud máte ve struktuře složek více cílů, můžete si vybrat, jestli chcete sestavit jenom jeden konkrétní cíl.

1. V hlavní nabídce vyberte **sestavit > sestavit vše** (**F7** nebo **CTRL + SHIFT + B**). Ujistěte se, že cíl CMake je už vybraný v rozevíracím seznamu **položky po spuštění** na panelu nástrojů **Obecné** .

![Příkaz nabídky buildu CMake](media/cmake-build-menu.png "Nabídka příkazů pro sestavení CMake")

Jak byste očekávali, výsledky sestavení se zobrazí v **okno výstup** a **Seznam chyb**.

![Chyby sestavení CMake](media/cmake-build-errors.png "Chyby sestavení CMake")

Ve složce s více cíli sestavení můžete určit, který cíl CMake se má sestavit: zvolte položku **sestavení** v nabídce **cmake** nebo v kontextové nabídce *CMakeLists. txt* pro určení cíle. Pokud zadáte **CTRL + SHIFT + B** v projektu cmake, vytvoří se aktuální aktivní dokument.

## <a name="debugging-cmake-projects"></a>Ladění projektů CMake

Chcete-li ladit projekt CMake, zvolte upřednostňovanou konfiguraci a stiskněte klávesu **F5**nebo stiskněte tlačítko **Spustit** na panelu nástrojů. Pokud tlačítko **Spustit** uvádí možnost "vybrat položku po spuštění", vyberte šipku rozevíracího seznamu. Vyberte cíl, který chcete spustit. (V projektu CMake je možnost aktuální dokument platná jenom pro soubory. cpp.)

![Tlačítko spustit CMake](media/cmake-run-button.png "Tlačítko spustit CMake")

Příkazy **Run** nebo **F5** nejprve sestaví projekt, pokud byly od předchozího sestavení provedeny změny. Změny v *CMakeSettings. JSON* způsobí opětovné vygenerování mezipaměti cmake.

Relaci ladění CMake můžete přizpůsobit nastavením vlastností v souboru **Launch. vs. JSON** . Další informace najdete v tématu [Konfigurace relací ladění cmake](configure-cmake-debugging-sessions.md).

## <a name="just-my-code-for-cmake-projects"></a>Pouze můj kód pro projekty CMake

Projekty CMake mají při sestavování pro Windows pomocí kompilátoru MSVC podporu ladění Pouze můj kód. Chcete-li změnit nastavení Pouze můj kód, přejděte na **nástroje** > **možnosti** > **ladění** > **Obecné**.

## <a name="vcpkg-integration"></a>Integrace Vcpkg

Pokud jste nainstalovali [vcpkg](vcpkg.md), projekty cmake otevřené v sadě Visual Studio automaticky integrují soubor sada nástrojů vcpkg. To znamená, že pro použití vcpkg s projekty CMake není nutná žádná další konfigurace. Tato podpora funguje jak pro místní instalace vcpkg, tak pro instalace vcpkg na vzdálených systémech, které cílíte. Toto chování je automaticky zakázáno při zadání jakýchkoli dalších sada nástrojů v konfiguraci nastavení CMake.

## <a name="customize-configuration-feedback"></a>Přizpůsobení zpětné vazby konfigurace

Ve výchozím nastavení je většina konfiguračních zpráv potlačena, pokud nedošlo k chybě. Všechny zprávy můžete zobrazit tak, že tuto funkci povolíte v **nabídce nástroje** > **Možnosti** > **cmake**.

   ![Konfigurace možností diagnostiky CMake](media/vs2019-cmake-configure-options.png "Možnosti diagnostiky CMake")

## <a name="editing-cmakeliststxt-files"></a>Úpravy souborů CMakeLists. txt

Pokud chcete upravit soubor *CMakeLists. txt* , klikněte pravým tlačítkem na soubor v **Průzkumník řešení** a vyberte **otevřít**. Pokud provedete změny v souboru, zobrazí se žlutý stavový řádek, který bude informovat o aktualizaci IntelliSense. Nabízí možnost zrušit operaci aktualizace. Informace o *CMakeLists. txt*najdete v dokumentaci k [cmaki](https://cmake.org/documentation/).

   ![Úpravy souboru CMakeLists. txt](media/cmake-cmakelists.png "Úpravy souboru CMakeLists. txt")

Jakmile soubor uložíte, krok konfigurace se automaticky spustí znovu a zobrazí informace v okně **výstup** . Chyby a varování se zobrazí v okně **Seznam chyb** nebo **výstup** . Dvojím kliknutím na chybu v **Seznam chyb** přejděte na problematický řádek v *CMakeLists. txt*.

   ![Chyby souboru CMakeLists. txt](media/cmake-cmakelists-error.png "Chyby souboru CMakeLists. txt")

## <a name="cmake-configure-step"></a>Krok konfigurace CMake

Když provedete významné změny v souborech *CMakeSettings. JSON* nebo *CMakeLists. txt* , sada Visual Studio automaticky znovu spustí krok konfigurace cmake. Pokud se krok konfigurace dokončí bez chyb, shromažďované informace jsou k dispozici C++ v IntelliSense a v jazykových službách. Používá se také při operacích sestavení a ladění.

## <a name="troubleshooting-cmake-cache-errors"></a>Řešení chyb v mezipaměti CMake

Pokud potřebujete další informace o stavu mezipaměti CMake pro diagnostiku problému, otevřete hlavní nabídku **projektu** nebo místní nabídku *CMakeLists. txt* v **Průzkumník řešení** a spusťte jeden z těchto příkazů:

- Možnost **Zobrazit mezipaměť** otevře soubor *CMakeCache. txt* z kořenové složky sestavení v editoru. (Všechny úpravy, které uděláte v *CMakeCache. txt* , se při vyčištění mezipaměti vymažou. Pokud chcete provést změny, které budou trvalé po vyčištění mezipaměti, přečtěte si téma [přizpůsobení nastavení cmake](customize-cmake-settings.md).)

- **Složka otevřít mezipaměť** otevře okno Průzkumníka s kořenovou složkou sestavení.

- **Vyčištění mezipaměti** odstraní kořenovou složku sestavení tak, aby další krok konfigurace cmake začínal z čisté mezipaměti.

- **Vygenerovat mezipaměť** vynutí spuštění kroku generovat, i když Visual Studio posuzuje prostředí v aktuálním stavu.

Automatickou generaci mezipaměti je možné zakázat v dialogovém okně **nástroje > možnosti > cmake > obecné** .

## <a name="run-cmake-from-the-command-line"></a>Spuštění CMake z příkazového řádku

Pokud jste nainstalovali CMake z Instalační program pro Visual Studio, můžete ji spustit z příkazového řádku pomocí následujících kroků:

1. Spusťte příslušný vsdevcmd. bat (x86/x64). Další informace najdete v tématu [sestavování na příkazovém řádku](building-on-the-command-line.md).

1. Přepněte do výstupní složky.

1. Spusťte CMake a sestavte/nakonfigurujte svoji aplikaci.

::: moniker-end

::: moniker range="vs-2017"

Sada Visual Studio 2017 nabízí bohatou podporu pro CMake, včetně [projektů cmake pro různé platformy](../linux/cmake-linux-project.md). Komponenta **Visual C++ Tools for cmake** používá funkci **Otevřít složku** , která umožňuje integrovanému vývojovém prostředí (IDE) využívat soubory projektu cmake (například *CMakeLists. txt*) přímo pro účely IntelliSense a procházení. Podporují se expertem i generátory sady Visual Studio. Použijete-li generátor sady Visual Studio, vygeneruje dočasný soubor projektu a předá ho nástroji MSBuild. exe. Projekt se ale nikdy nenačte pro účely IntelliSense nebo procházení. Můžete také importovat stávající mezipaměť CMake.

## <a name="installation"></a>Instalace služby

**Visual C++ Tools for cmake** se instalují jako součást **vývoje C++ desktopových** aplikací a **vývoj pro Linux s C++**  využitím úloh.

![Součást CMake v C++ pracovní ploše](media/cmake-install.png)

Další informace najdete v tématu [instalace úlohy C++ pro Linux v aplikaci Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integrace IDE

Když vyberete **soubor > otevřít > složku** a otevřete složku obsahující soubor *CMakeLists. txt* , dojde k následujícím akcím:

- Sada Visual Studio přidá do hlavní nabídky položku nabídky **cmake** s příkazy pro zobrazení a úpravy skriptů cmake.

- **Průzkumník řešení** zobrazuje strukturu a soubory složek.

- Sada Visual Studio spustí CMake. exe a volitelně vygeneruje mezipaměť CMake pro výchozí *konfiguraci*, což je x86 Debug. V **okno výstup**se zobrazí příkazový řádek cmake spolu s dalším výstupem z cmake.

- Na pozadí Visual Studio začne indexovat zdrojové soubory, aby bylo možné povolit technologii IntelliSense, informace o procházení, refaktoring atd. Při práci Visual Studio monitoruje změny v editoru a také na disku, aby byl jeho index synchronizovaný se zdroji.

Můžete otevřít složky obsahující libovolný počet projektů CMake. Visual Studio detekuje a konfiguruje všechny "kořenové" soubory *CMakeLists. txt* v pracovním prostoru. Operace CMake (konfigurace, sestavení, ladění), C++ IntelliSense a procházení jsou k dispozici pro všechny projekty cmake v pracovním prostoru.

![Projekt CMake s více kořeny](media/cmake-multiple-roots.png)

Své projekty můžete také hierarchicky zobrazit podle cílů. V rozevíracím seznamu na panelu nástrojů **Průzkumník řešení** vyberte **zobrazení cílů** :

![Tlačítko zobrazení cílů CMake](media/cmake-targets-view.png)

Sada Visual Studio používá k ukládání proměnných prostředí nebo možností příkazového řádku pro cmake. exe soubor s názvem *CMakeSettings. JSON* . *CMakeSettings. JSON* také umožňuje definovat a ukládat více konfigurací sestavení cmake. Můžete snadno přepínat mezi nimi v integrovaném vývojovém prostředí.

V opačném případě použijte soubor *CMakeLists. txt* stejným způsobem jako v jakémkoli projektu cmake, abyste určili zdrojové soubory, našli knihovny, nastavili možnosti kompilátoru a linkeru a zadali další informace související se systémem sestavení.

Pokud potřebujete předat argumenty spustitelnému souboru v době ladění, můžete použít jiný soubor nazvaný **Launch. vs. JSON**. V některých scénářích aplikace Visual Studio tyto soubory automaticky generuje. Můžete je upravit ručně nebo dokonce vytvořit soubor sami.

> [!NOTE]
> Pro jiné druhy projektů otevřené složky se používají dva další soubory JSON: **CppProperties. JSON** a **Tasks. vs. JSON**. Ani jedna z těchto projektů není relevantní pro projekty CMake.

## <a name="import-an-existing-cache"></a>Importovat existující mezipaměť

Když importujete existující soubor *CMakeCache. txt* , Visual Studio automaticky extrahuje vlastní proměnné a na základě nich vytvoří předem vyplněný soubor *CMakeSettings. JSON* . Původní mezipaměť není nijak měněna. Pořád se dá použít z příkazového řádku nebo s jakýmkoli nástrojem nebo IDE použitým k jeho vygenerování. Nový soubor *CMakeSettings. JSON* se umístí vedle kořenového souboru *CMakeLists. txt*projektu. Visual Studio vygeneruje novou mezipaměť založenou na souboru nastavení. Automatické generování mezipaměti můžete přepsat v dialogovém okně **nástroje > možnosti > cmake > obecné** .

Ne vše v mezipaměti je importováno.  Vlastnosti, jako je generátor a umístění kompilátorů, se nahrazují výchozími hodnotami, které jsou známé pro správnou práci s IDE.

### <a name="to-import-an-existing-cache"></a>Import existující mezipaměti

1. V hlavní nabídce vyberte **soubor > otevřít > cmake**:

   ![Otevřít CMake](media/cmake-file-open.png "Soubor, otevřít, CMake")

   Tento příkaz vyvolá průvodce **importem cmake z mezipaměti** .

2. Přejděte k souboru *CMakeCache. txt* , který chcete importovat, a klikněte na tlačítko **OK**. Zobrazí se průvodce **importem projektu cmake z mezipaměti** :

   ![Import mezipaměti CMake](media/cmake-import-wizard.png "Otevřete Průvodce pro import mezipaměti CMake.")

   Po dokončení průvodce uvidíte nový soubor *CMakeCache. txt* v **Průzkumník řešení** vedle kořenového souboru *CMakeLists. txt* v projektu.

## <a name="building-cmake-projects"></a>Sestavování projektů CMake

Chcete-li vytvořit projekt CMake, máte tyto možnosti:

1. Na panelu nástrojů obecné Najděte rozevírací seznam **Konfigurace** . Ve výchozím nastavení se nejspíš zobrazuje "Linux-debug" nebo "x64-debug". Vyberte upřednostňovanou konfiguraci a stiskněte klávesu **F5**nebo klikněte na tlačítko **Spustit** (zelený trojúhelník) na panelu nástrojů. Projekt se nejprve automaticky sestaví jako řešení sady Visual Studio.

1. Klikněte pravým tlačítkem na *CMakeLists. txt* a v místní nabídce vyberte **sestavit** . Pokud máte ve struktuře složek více cílů, můžete si vybrat, jestli chcete sestavit jenom jeden konkrétní cíl.

1. V hlavní nabídce vyberte **sestavit > sestavit řešení** (**F7** nebo **CTRL + SHIFT + B**). Ujistěte se, že cíl CMake je už vybraný v rozevíracím seznamu **položky po spuštění** na panelu nástrojů **Obecné** .

![Příkaz nabídky buildu CMake](media/cmake-build-menu.png "Nabídka příkazů pro sestavení CMake")

Můžete přizpůsobit konfigurace sestavení, proměnné prostředí, argumenty příkazového řádku a další nastavení v souboru *CMakeSettings. JSON* . Umožňuje provádět změny bez změny souboru *CMakeLists. txt* . Další informace najdete v tématu [přizpůsobení nastavení cmake](customize-cmake-settings.md).

Jak byste očekávali, výsledky sestavení se zobrazí v **okno výstup** a **Seznam chyb**.

![Chyby sestavení CMake](media/cmake-build-errors.png "Chyby sestavení CMake")

Ve složce s více cíli sestavení můžete určit, který cíl CMake se má sestavit: zvolte položku **sestavení** v nabídce **cmake** nebo v kontextové nabídce *CMakeLists. txt* pro určení cíle. Pokud zadáte **CTRL + SHIFT + B** v projektu cmake, vytvoří se aktuální aktivní dokument.

## <a name="debugging-cmake-projects"></a>Ladění projektů CMake

Chcete-li ladit projekt CMake, zvolte upřednostňovanou konfiguraci a stiskněte klávesu **F5**. Nebo stiskněte tlačítko **Spustit** na panelu nástrojů. Pokud tlačítko **Spustit** uvádí možnost "vybrat položku po spuštění", vyberte šipku rozevíracího seznamu a zvolte cíl, který chcete spustit. (V projektu CMake je možnost aktuální dokument platná jenom pro soubory. cpp.)

![Tlačítko spustit CMake](media/cmake-run-button.png "Tlačítko spustit CMake")

Příkazy **Run** nebo **F5** nejprve sestaví projekt, pokud byly od předchozího sestavení provedeny změny.

Relaci ladění CMake můžete přizpůsobit nastavením vlastností v souboru **Launch. vs. JSON** . Další informace najdete v tématu [Konfigurace relací ladění cmake](configure-cmake-debugging-sessions.md).

## <a name="editing-cmakeliststxt-files"></a>Úpravy souborů CMakeLists. txt

Pokud chcete upravit soubor *CMakeLists. txt* , klikněte pravým tlačítkem na soubor v **Průzkumník řešení** a vyberte **otevřít**. Pokud provedete změny v souboru, zobrazí se žlutý stavový řádek, který bude informovat o aktualizaci IntelliSense. Nabízí možnost zrušit operaci aktualizace. Informace o *CMakeLists. txt*najdete v dokumentaci k [cmaki](https://cmake.org/documentation/).

   ![Úpravy souboru CMakeLists. txt](media/cmake-cmakelists.png "Úpravy souboru CMakeLists. txt")

Jakmile soubor uložíte, krok konfigurace se automaticky spustí znovu a zobrazí informace v okně **výstup** . Chyby a varování se zobrazí v okně **Seznam chyb** nebo **výstup** . Dvojím kliknutím na chybu v **Seznam chyb** přejděte na problematický řádek v *CMakeLists. txt*.

   ![Chyby souboru CMakeLists. txt](media/cmake-cmakelists-error.png "Chyby souboru CMakeLists. txt")

## <a name="cmake-configure-step"></a>Krok konfigurace CMake

Pokud jsou provedeny významné změny v souborech *CMakeSettings. JSON* nebo *CMakeLists. txt* , sada Visual Studio automaticky znovu spustí krok konfigurace cmake. Pokud se krok konfigurace dokončí bez chyb, shromažďované informace jsou k dispozici C++ v IntelliSense a v jazykových službách. Používá se také při operacích sestavení a ladění.

Více projektů CMake může používat stejný název konfigurace CMake (například x86-Debug). Všechny jsou nakonfigurovány a postaveny (ve vlastní kořenové složce sestavení), pokud je tato konfigurace vybrána. Cíle můžete ladit ze všech projektů CMake, které se účastní konfigurace CMake.

   ![Položka nabídky jenom pro sestavení CMake](media/cmake-build-only.png "Položka nabídky jenom pro sestavení CMake")

Můžete omezit sestavení a relace ladění na podmnožinu projektů v pracovním prostoru. V souboru *CMakeSettings. JSON* vytvořte novou konfiguraci s jedinečným názvem. Pak použijte konfiguraci jenom pro tyto projekty. Pokud je zvolena tato konfigurace, technologie IntelliSense a příkazy sestavení a ladění se vztahují pouze na ty zadané projekty.

## <a name="troubleshooting-cmake-cache-errors"></a>Řešení chyb v mezipaměti CMake

Pokud potřebujete další informace o stavu mezipaměti CMake pro diagnostiku problému, otevřete hlavní nabídku **cmake** nebo místní nabídku *CMakeLists. txt* v **Průzkumník řešení** a spusťte jeden z těchto příkazů:

- Možnost **Zobrazit mezipaměť** otevře soubor *CMakeCache. txt* z kořenové složky sestavení v editoru. (Všechny úpravy, které uděláte v *CMakeCache. txt* , se při vyčištění mezipaměti vymažou. Pokud chcete provést změny, které budou trvalé po vyčištění mezipaměti, přečtěte si téma [přizpůsobení nastavení cmake](customize-cmake-settings.md).)

- **Složka otevřít mezipaměť** otevře okno Průzkumníka s kořenovou složkou sestavení.

- **Vyčištění mezipaměti** odstraní kořenovou složku sestavení tak, aby další krok konfigurace cmake začínal z čisté mezipaměti.

- **Vygenerovat mezipaměť** vynutí spuštění kroku generovat, i když Visual Studio posuzuje prostředí v aktuálním stavu.

Automatickou generaci mezipaměti je možné zakázat v dialogovém okně **nástroje > možnosti > cmake > obecné** .

## <a name="single-file-compilation"></a>Kompilace jednoho souboru

Pokud chcete vytvořit jeden soubor v projektu CMake, klikněte pravým tlačítkem na soubor v **Průzkumník řešení**. V místní nabídce vyberte **kompilovat** . Aktuálně otevřený soubor můžete také vytvořit v editoru pomocí hlavní nabídky **cmake** :

![Kompilace jednoho souboru CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Spuštění CMake z příkazového řádku

Pokud jste nainstalovali CMake z Instalační program pro Visual Studio, můžete ji spustit z příkazového řádku pomocí následujících kroků:

1. Spusťte příslušný vsdevcmd. bat (x86/x64). Další informace najdete v tématu [sestavování na příkazovém řádku](building-on-the-command-line.md) .

1. Přepněte do výstupní složky.

1. Spusťte CMake a sestavte/nakonfigurujte svoji aplikaci.

::: moniker-end

::: moniker range="vs-2015"

V sadě Visual Studio 2015 mohou uživatelé sady Visual Studio použít [generátor cmake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) k vygenerování souborů projektu MSBuild, které rozhraní IDE pak spotřebuje pro technologii IntelliSense, procházení a kompilaci.

::: moniker-end

## <a name="see-also"></a>Viz také:

[Kurz: vytváření C++ projektů pro různé platformy v aplikaci Visual Studio](get-started-linux-cmake.md)\
[Konfigurace projektu Linux cmake](../linux/cmake-linux-project.md)\
[Připojte se ke vzdálenému počítači se systémem Linux](../linux/connect-to-your-remote-linux-computer.md)\
[Přizpůsobení nastavení buildu cmake](customize-cmake-settings.md)\
[Referenční\ schématu CMakeSettings. JSON](cmakesettings-reference.md)
[Konfigurace relací ladění cmake](configure-cmake-debugging-sessions.md)\
[Nasazení, spuštění a ladění projektu pro Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Odkaz na předdefinovaný konfigurační odkaz CMake](cmake-predefined-configuration-reference.md)
