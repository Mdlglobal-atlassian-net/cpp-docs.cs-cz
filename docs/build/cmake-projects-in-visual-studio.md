---
title: Projekty CMake v sadě Visual Studio
ms.date: 10/01/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 52ca34ef8522ada1881e2f7f5df212167c64c919
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816391"
---
# <a name="cmake-projects-in-visual-studio"></a>Projekty CMake v sadě Visual Studio

CMake je open source nástroj pro různé platformy, který slouží k definování procesů sestavení, které běží na různých platformách. Tento článek předpokládá, že máte zkušenosti s CMakí. Další informace o IT najdete v [sestavování, testování a zabalení softwaru pomocí cmake](https://cmake.org/). 

> [!NOTE]
> Sada CMake se v sadě Visual Studio během posledních několika verzí stala více a více integrována. Pokud chcete zobrazit správné informace o verzi, kterou používáte, ujistěte se, že je správně nastavený selektor verzí v levém horním rohu této stránky. 

::: moniker range="vs-2019"

Součást  **C++ cmake Tools for Windows** používá funkci [Otevřít složku](https://docs.microsoft.com/en-us/cpp/build/open-folder-projects-cpp?view=vs-2019) pro využívání souborů projektu cmake (například CMakeLists. txt) přímo pro účely IntelliSense a procházení. Podporují se expertem i generátory sady Visual Studio. Použijete-li generátor sady Visual Studio, je vytvořen dočasný soubor projektu nástroje MSBuild. exe, ale nikdy se nenačte pro účely IntelliSense nebo procházení. Můžete také importovat stávající mezipaměť CMake.

## <a name="installation"></a>Instalace

Nástroje cmake pro Windows se ve výchozím nastavení instalují jako součást **vývoje plochy s C++**  úlohou a jako součást vývoje pro **Linux s C++**  úlohou. **C++** Další informace najdete v tématu [projekty cmake pro různé platformy](../linux/cmake-linux-project.md) .

![Součást CMake v C++ pracovní ploše](media/cmake-install-2019.png)

Další informace najdete v tématu [instalace úlohy C++ pro Linux v aplikaci Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integrace IDE

Když vyberete **soubor > otevřít > složku** a otevřete složku obsahující soubor CMakeLists. txt, dojde k následujícím akcím:

- Sada Visual Studio přidá položky **cmake** do nabídky **projekt** s příkazy pro zobrazení a úpravy skriptů cmake.

- **Průzkumník řešení** zobrazuje strukturu a soubory složek.

- Sada Visual Studio spustí cmake. exe a vygeneruje mezipaměť CMake pro výchozí *konfiguraci*, což je x64 ladění. V **okno výstup**se zobrazí příkazový řádek cmake spolu s dalším výstupem z cmake.

- Na pozadí Visual Studio začne indexovat zdrojové soubory, aby bylo možné povolit technologii IntelliSense, informace o procházení, refaktoring atd. Při práci Visual Studio monitoruje změny v editoru a také na disku, aby byl jeho index synchronizovaný se zdroji.

Můžete otevřít složky obsahující libovolný počet projektů CMake. Visual Studio detekuje a konfiguruje všechny "kořenové" soubory CMakeLists. txt v pracovním prostoru. Operace CMake (konfigurace, sestavení, ladění) i C++ IntelliSense a procházení jsou k dispozici pro všechny projekty cmake v pracovním prostoru.

![Projekt CMake s více kořeny](media/cmake-multiple-roots.png)

Své projekty můžete také hierarchicky zobrazit podle cílů. V rozevíracím seznamu na panelu nástrojů **Průzkumník řešení** vyberte **zobrazení cílů** :

![Tlačítko zobrazení cílů CMake](media/cmake-targets-view.png)

Sada Visual Studio používá k ukládání proměnných prostředí nebo možností příkazového řádku pro cmake. exe soubor s názvem **CMakeSettings. JSON** . **CMakeSettings. JSON** také umožňuje definovat a ukládat více konfigurací sestavení cmake a pohodlně přepínat mezi nimi v integrovaném vývojovém prostředí (IDE). V sadě Visual Studio 2019 **Editor nastavení cmake** nabízí pohodlný způsob, jak upravit nastavení. Další informace najdete v tématu [přizpůsobení nastavení cmake](customize-cmake-settings.md) .

V opačném případě použijte **CMakeLists. txt** stejným způsobem jako v jakémkoli projektu cmake, abyste určili zdrojové soubory, našli knihovny, nastavili možnosti kompilátoru a linkeru a zadali další informace související se systémem sestavení.

Pokud potřebujete předat argumenty spustitelnému souboru v době ladění, můžete použít jiný soubor nazvaný **Launch. vs. JSON**. V některých scénářích aplikace Visual Studio tyto soubory automaticky vygeneruje. můžete je upravit ručně. Soubor můžete také vytvořit sami.

> [!NOTE]
> Pro jiné druhy projektů otevřené složky se používají dva další soubory JSON: **CppProperties. JSON** a **Tasks. vs. JSON**. Ani jedna z těchto projektů není relevantní pro projekty CMake.

## <a name="import-an-existing-cache"></a>Importovat existující mezipaměť

Když importujete existující soubor CMakeCache. txt, Visual Studio automaticky extrahuje vlastní proměnné a na základě nich vytvoří předem vyplněný soubor **CMakeSettings. JSON** . Původní mezipaměť není nijak upravována a lze ji nadále používat z příkazového řádku nebo s jakýmkoli nástrojem nebo IDE použitým k jejich vygenerování. Nový soubor **CMakeSettings. JSON** se umístí vedle kořenového souboru CMakeLists. txt projektu. Visual Studio vygeneruje novou mezipaměť založenou na souboru nastavení. Automatické generování mezipaměti můžete přepsat v dialogovém okně **nástroje > možnosti > cmake > obecné** .

Ne vše v mezipaměti je importováno. Vlastnosti, jako je generátor a umístění kompilátorů, se nahrazují výchozími hodnotami, které jsou známé pro správnou práci s IDE.

## <a name="open-an-existing-cache"></a>Otevřít existující mezipaměť

Když otevřete existující mezipaměť CMake, Visual Studio se nebude pokoušet spravovat vaši mezipaměť a strom sestavení za vás. Díky tomu mají vaše vlastní nebo preferované nástroje úplnou kontrolu nad tím, jak CMake nakonfiguruje váš projekt. V sadě Visual Studio můžete otevřít existující mezipaměť prostřednictvím **souboru > otevřít > cmake** a přejít na existující soubor CMakeCache. txt. Případně, pokud jste již otevřeli projekt v aplikaci Visual Studio, můžete do něj přidat existující mezipaměť stejným způsobem, jako byste přidali novou konfiguraci. Další informace najdete v našem blogovém příspěvku o [otevření existující mezipaměti v aplikaci Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Sestavování projektů CMake

Chcete-li vytvořit projekt CMake, máte tyto možnosti:

1. Na panelu nástrojů obecné Najděte rozevírací seznam **Konfigurace** . Ve výchozím nastavení se pravděpodobně zobrazuje "x64-debug". Vyberte požadovanou konfiguraci a stiskněte klávesu **F5**nebo klikněte na tlačítko **Spustit** (zelený trojúhelník) na panelu nástrojů. Projekt se nejprve automaticky sestaví jako řešení sady Visual Studio.

1. Klikněte pravým tlačítkem na CMakeLists. txt a v místní nabídce vyberte **sestavit** . Pokud máte ve struktuře složek více cílů, můžete si vybrat, jestli chcete sestavit jenom jeden konkrétní cíl.

1. V hlavní nabídce vyberte **sestavit > sestavit vše** (**F7** nebo **CTRL + SHIFT + B**). Ujistěte se, že cíl CMake je už vybraný v rozevíracím seznamu **položky po spuštění** na panelu nástrojů **Obecné** .

![Nabídka sestavení cmake příkazu](media/cmake-build-menu.png "cmake – příkaz nabídky sestavení")

Můžete přizpůsobit konfigurace sestavení, proměnné prostředí, argumenty příkazového řádku a další nastavení, aniž byste museli upravovat soubor CMakeLists. txt pomocí **editoru nastavení cmake**. Další informace najdete v tématu [přizpůsobení nastavení cmake](customize-cmake-settings.md).

Jak byste očekávali, výsledky sestavení se zobrazí v **okno výstup** a **Seznam chyb**.

![Chyby buildu cmake]Chyba(media/cmake-build-errors.png "buildu cmake")

Ve složce s více cíli sestavení můžete zvolit položku **sestavení** v nabídce **cmake** nebo v kontextové nabídce **CMakeLists. txt** a určit tak, který cíl cmake se má sestavit. Stisknutím **kombinace kláves CTRL + SHIFT + B** v projektu cmake sestavíte aktuální aktivní dokument.

## <a name="debugging-cmake-projects"></a>Ladění projektů CMake

Chcete-li ladit projekt CMake, zvolte požadovanou konfiguraci a stiskněte klávesu **F5**nebo stiskněte tlačítko **Spustit** na panelu nástrojů. Pokud tlačítko **Spustit** uvádí možnost "vybrat položku po spuštění", vyberte šipku rozevíracího seznamu a zvolte cíl, který chcete spustit. (V projektu CMake je možnost aktuální dokument platná jenom pro soubory. cpp.)

Tlačítko spustit(media/cmake-run-button.png "cmake") ![tlačítka Spustit]cmake

Příkazy **Run** nebo **F5** nejprve sestaví projekt, pokud byly od předchozího sestavení provedeny změny.

Relaci ladění CMake můžete přizpůsobit nastavením vlastností v souboru **Launch. vs. JSON** . Další informace najdete v tématu [Konfigurace relací ladění cmake](configure-cmake-debugging-sessions.md).

## <a name="just-my-code-for-cmake-projects"></a>Pouze můj kód pro projekty CMake

Při sestavování pro Windows pomocí kompilátoru MSVC, projekty CMake mají podporu pouze pro ladění pouze můj kód v kompilátoru a linkeru, pokud je v sadě Visual Studio povolena možnost. Pokud chcete nastavení změnit, přejděte na **nástroje** > **možnosti**-1  > **ladění** > **Obecné**.

## <a name="vcpkg-integration"></a>Integrace Vcpkg

Pokud jste nainstalovali [vcpkg](vcpkg.md), projekty cmake otevřené v sadě Visual Studio automaticky integrují soubor sada nástrojů vcpkg. To znamená, že pro použití vcpkg s projekty CMake není nutná žádná další konfigurace. Tato podpora funguje jak pro místní instalace vcpkg, tak pro instalace vcpkg na vzdálených systémech, které cílíte. Toto chování je automaticky zakázáno při zadání jakýchkoli dalších sada nástrojů v konfiguraci nastavení CMake.

## <a name="customize-configuration-feedback"></a>Přizpůsobení zpětné vazby konfigurace

Ve výchozím nastavení je většina konfiguračních zpráv potlačena, pokud nedošlo k chybě. Všechny zprávy můžete zobrazit tak, že tuto funkci povolíte v **nástrojích**@no__t**možnosti**-1  > **cmake**.

   ![Konfigurace možností diagnostiky cmake]možnosti(media/vs2019-cmake-configure-options.png "diagnostiky")

## <a name="editing-cmakeliststxt-files"></a>Úpravy souborů CMakeLists. txt

Pokud chcete upravit soubor CMakeLists. txt, klikněte pravým tlačítkem na soubor v **Průzkumník řešení** a vyberte **otevřít**. Pokud provedete změny v souboru, zobrazí se žlutý stavový řádek, který vám bude informovat o tom, že technologie IntelliSense bude aktualizována a nabídne vám možnost zrušit operaci aktualizace. Informace o CMakeLists. txt najdete v dokumentaci k [cmaki](https://cmake.org/documentation/).

   Úprava souboru ![CMakeLists. txt úpravou](media/cmake-cmakelists.png "souboru CMakeLists. txt")

Jakmile soubor uložíte, krok konfigurace se automaticky spustí znovu a zobrazí informace v okně **výstup** . Chyby a varování se zobrazí v okně **Seznam chyb** nebo **výstup** . Dvojím kliknutím na chybu v **Seznam chyb** přejděte na problematický řádek v CMakeLists. txt.

   ![CMakeLists. txt]– chyby(media/cmake-cmakelists-error.png "souboru CMakeLists. txt")


## <a name="cmake-configure-step"></a>Krok konfigurace CMake

Pokud jsou provedeny významné změny v souborech **CMakeSettings. JSON** nebo CMakeLists. txt, sada Visual Studio automaticky znovu spustí krok konfigurace cmake. Pokud se krok konfigurace dokončí bez chyb, shromažďované informace jsou k dispozici C++ v technologii IntelliSense a jazykové služby a také v operacích sestavení a ladění.

## <a name="troubleshooting-cmake-cache-errors"></a>Řešení chyb v mezipaměti CMake

Pokud potřebujete další informace o stavu mezipaměti CMake pro diagnostiku problému, otevřete hlavní nabídku **projektu** nebo místní nabídku **CMakeLists. txt** v **Průzkumník řešení** a spusťte jeden z těchto příkazů:

- Možnost **Zobrazit mezipaměť** otevře soubor CMakeCache. txt z kořenové složky sestavení v editoru. (Všechny úpravy, které uděláte v CMakeCache. txt, se při vyčištění mezipaměti vymažou. Pokud chcete provést změny, které budou trvalé po vyčištění mezipaměti, přečtěte si téma [přizpůsobení nastavení cmake](customize-cmake-settings.md).)

- **Složka otevřít mezipaměť** otevře okno Průzkumníka s kořenovou složkou sestavení.

- **Vyčištění mezipaměti** odstraní kořenovou složku sestavení tak, aby další krok konfigurace cmake začínal z čisté mezipaměti.

- **Vygenerovat mezipaměť** vynutí spuštění kroku generovat, i když Visual Studio posuzuje prostředí v aktuálním stavu.

Automatickou generaci mezipaměti je možné zakázat v dialogovém okně **nástroje > možnosti > cmake > obecné** .

## <a name="run-cmake-from-the-command-line"></a>Spuštění CMake z příkazového řádku

Pokud jste nainstalovali CMake z Instalační program pro Visual Studio, můžete ji spustit z příkazového řádku pomocí následujících kroků:

1. Spusťte příslušný vsdevcmd. bat (x86/x64). Další informace naleznete v tématu [sestavování na příkazovém řádku](building-on-the-command-line.md) .

1. Přepněte do výstupní složky.

1. Spusťte CMake a sestavte/nakonfigurujte svoji aplikaci.

::: moniker-end

::: moniker range="vs-2017"

Sada Visual Studio 2017 nabízí bohatou podporu pro CMake, včetně [projektů cmake pro různé platformy](../linux/cmake-linux-project.md). Komponenta **Visual C++ Tools for cmake** používá funkci **Otevřít složku** , která umožňuje integrovanému vývojovém prostředí (IDE) využívat soubory projektu cmake (například CMakeLists. txt) přímo pro účely IntelliSense a procházení. Podporují se expertem i generátory sady Visual Studio. Použijete-li generátor sady Visual Studio, je vytvořen dočasný soubor projektu nástroje MSBuild. exe, ale nikdy se nenačte pro účely IntelliSense nebo procházení. Můžete také importovat stávající mezipaměť CMake. 

## <a name="installation"></a>Instalace

**Visual C++ Tools for cmake** se ve výchozím nastavení instalují jako součást **vývoje plochy s C++**  úlohou a jako součást vývoje pro **Linux s C++**  úlohou.

![Součást CMake v C++ pracovní ploše](media/cmake-install.png)

Další informace najdete v tématu [instalace úlohy C++ pro Linux v aplikaci Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integrace IDE

Když vyberete **soubor > otevřít > složku** a otevřete složku obsahující soubor CMakeLists. txt, dojde k následujícím akcím:

- Sada Visual Studio přidá do hlavní nabídky položku nabídky **cmake** s příkazy pro zobrazení a úpravy skriptů cmake.

- **Průzkumník řešení** zobrazuje strukturu a soubory složek.

- Sada Visual Studio spustí CMake. exe a volitelně vygeneruje mezipaměť CMake pro výchozí *konfiguraci*, což je x86 Debug. V **okno výstup**se zobrazí příkazový řádek cmake spolu s dalším výstupem z cmake.

- Na pozadí Visual Studio začne indexovat zdrojové soubory, aby bylo možné povolit technologii IntelliSense, informace o procházení, refaktoring atd. Při práci Visual Studio monitoruje změny v editoru a také na disku, aby byl jeho index synchronizovaný se zdroji.

Můžete otevřít složky obsahující libovolný počet projektů CMake. Visual Studio detekuje a konfiguruje všechny "kořenové" soubory CMakeLists. txt v pracovním prostoru. Operace CMake (konfigurace, sestavení, ladění) i C++ IntelliSense a procházení jsou k dispozici pro všechny projekty cmake v pracovním prostoru.

![Projekt CMake s více kořeny](media/cmake-multiple-roots.png)

Své projekty můžete také hierarchicky zobrazit podle cílů. V rozevíracím seznamu na panelu nástrojů **Průzkumník řešení** vyberte **zobrazení cílů** :

![Tlačítko zobrazení cílů CMake](media/cmake-targets-view.png)

Sada Visual Studio používá k ukládání proměnných prostředí nebo možností příkazového řádku pro cmake. exe soubor s názvem **CMakeSettings. JSON** . **CMakeSettings. JSON** také umožňuje definovat a ukládat více konfigurací sestavení cmake a pohodlně přepínat mezi nimi v integrovaném vývojovém prostředí (IDE). 

V opačném případě použijte soubor **CMakeLists. txt** stejným způsobem jako v jakémkoli projektu cmake, abyste určili zdrojové soubory, našli knihovny, nastavili možnosti kompilátoru a linkeru a zadali další informace související se systémem sestavení.

Pokud potřebujete předat argumenty spustitelnému souboru v době ladění, můžete použít jiný soubor nazvaný **Launch. vs. JSON**. V některých scénářích aplikace Visual Studio tyto soubory automaticky vygeneruje. můžete je upravit ručně. Soubor můžete také vytvořit sami.

> [!NOTE]
> Pro jiné druhy projektů otevřené složky se používají dva další soubory JSON: **CppProperties. JSON** a **Tasks. vs. JSON**. Ani jedna z těchto projektů není relevantní pro projekty CMake.

## <a name="import-an-existing-cache"></a>Importovat existující mezipaměť

Když importujete existující soubor CMakeCache. txt, Visual Studio automaticky extrahuje vlastní proměnné a na základě nich vytvoří předem vyplněný soubor **CMakeSettings. JSON** . Původní mezipaměť není nijak upravována a lze ji nadále používat z příkazového řádku nebo s jakýmkoli nástrojem nebo IDE použitým k jejich vygenerování. Nový soubor **CMakeSettings. JSON** se umístí vedle kořenového souboru CMakeLists. txt projektu. Visual Studio vygeneruje novou mezipaměť založenou na souboru nastavení. Automatické generování mezipaměti můžete přepsat v dialogovém okně **nástroje > možnosti > cmake > obecné** .

Ne vše v mezipaměti je importováno.  Vlastnosti, jako je generátor a umístění kompilátorů, se nahrazují výchozími hodnotami, které jsou známé pro správnou práci s IDE.

### <a name="to-import-an-existing-cache"></a>Import existující mezipaměti

1. V hlavní nabídce vyberte **soubor > otevřít > cmake**:

   ![Otevřít soubor cmake](media/cmake-file-open.png ", otevřít, cmake")

   Tím se otevře průvodce **importem cmake z mezipaměti** .

2. Přejděte k souboru CMakeCache. txt, který chcete importovat, a klikněte na tlačítko **OK**. Zobrazí se průvodce **importem projektu cmake z mezipaměti** :

   ![Import mezipaměti cmake](media/cmake-import-wizard.png "otevřete Průvodce importem mezipaměti cmake") .

   Po dokončení průvodce uvidíte nový soubor CMakeCache. txt v **Průzkumník řešení** vedle kořenového souboru CMakeLists. txt v projektu.

## <a name="building-cmake-projects"></a>Sestavování projektů CMake

Chcete-li vytvořit projekt CMake, máte tyto možnosti:

1. Na panelu nástrojů obecné Najděte rozevírací seznam **Konfigurace** ; ve výchozím nastavení se pravděpodobně zobrazuje "Linux-debug" nebo "x64-debug". Vyberte požadovanou konfiguraci a stiskněte klávesu **F5**nebo klikněte na tlačítko **Spustit** (zelený trojúhelník) na panelu nástrojů. Projekt se nejprve automaticky sestaví jako řešení sady Visual Studio.

1. Klikněte pravým tlačítkem na CMakeLists. txt a v místní nabídce vyberte **sestavit** . Pokud máte ve struktuře složek více cílů, můžete si vybrat, jestli chcete sestavit jenom jeden konkrétní cíl.

1. V hlavní nabídce vyberte **sestavit > sestavit řešení** (**F7** nebo **CTRL + SHIFT + B**). Ujistěte se, že cíl CMake je už vybraný v rozevíracím seznamu **položky po spuštění** na panelu nástrojů **Obecné** .

![Nabídka sestavení cmake příkazu](media/cmake-build-menu.png "cmake – příkaz nabídky sestavení")

Můžete přizpůsobit konfigurace sestavení, proměnné prostředí, argumenty příkazového řádku a další nastavení beze změny souboru CMakeLists. txt pomocí souboru **CMakeSettings. JSON** . Další informace najdete v tématu [přizpůsobení nastavení cmake](customize-cmake-settings.md).

Jak byste očekávali, výsledky sestavení se zobrazí v **okno výstup** a **Seznam chyb**.

![Chyby buildu cmake]Chyba(media/cmake-build-errors.png "buildu cmake")

Ve složce s více cíli sestavení můžete zvolit položku **sestavení** v nabídce **cmake** nebo v kontextové nabídce **CMakeLists. txt** a určit tak, který cíl cmake se má sestavit. Stisknutím **kombinace kláves CTRL + SHIFT + B** v projektu cmake sestavíte aktuální aktivní dokument.

## <a name="debugging-cmake-projects"></a>Ladění projektů CMake

Chcete-li ladit projekt CMake, zvolte požadovanou konfiguraci a stiskněte klávesu **F5**nebo stiskněte tlačítko **Spustit** na panelu nástrojů. Pokud tlačítko **Spustit** uvádí možnost "vybrat položku po spuštění", vyberte šipku rozevíracího seznamu a zvolte cíl, který chcete spustit. (V projektu CMake je možnost aktuální dokument platná jenom pro soubory. cpp.)

Tlačítko spustit(media/cmake-run-button.png "cmake") ![tlačítka Spustit]cmake

Příkazy **Run** nebo **F5** nejprve sestaví projekt, pokud byly od předchozího sestavení provedeny změny.

Relaci ladění CMake můžete přizpůsobit nastavením vlastností v souboru **Launch. vs. JSON** . Další informace najdete v tématu [Konfigurace relací ladění cmake](configure-cmake-debugging-sessions.md).


## <a name="editing-cmakeliststxt-files"></a>Úpravy souborů CMakeLists. txt

Pokud chcete upravit soubor CMakeLists. txt, klikněte pravým tlačítkem na soubor v **Průzkumník řešení** a vyberte **otevřít**. Pokud provedete změny v souboru, zobrazí se žlutý stavový řádek, který vám bude informovat o tom, že technologie IntelliSense bude aktualizována a nabídne vám možnost zrušit operaci aktualizace. Informace o CMakeLists. txt najdete v dokumentaci k [cmaki](https://cmake.org/documentation/).

   Úprava souboru ![CMakeLists. txt úpravou](media/cmake-cmakelists.png "souboru CMakeLists. txt")

Jakmile soubor uložíte, krok konfigurace se automaticky spustí znovu a zobrazí informace v okně **výstup** . Chyby a varování se zobrazí v okně **Seznam chyb** nebo **výstup** . Dvojím kliknutím na chybu v **Seznam chyb** přejděte na problematický řádek v CMakeLists. txt.

   ![CMakeLists. txt]– chyby(media/cmake-cmakelists-error.png "souboru CMakeLists. txt")


## <a name="cmake-configure-step"></a>Krok konfigurace CMake

Pokud jsou provedeny významné změny v souborech **CMakeSettings. JSON** nebo CMakeLists. txt, sada Visual Studio automaticky znovu spustí krok konfigurace cmake. Pokud se krok konfigurace dokončí bez chyb, shromažďované informace jsou k dispozici C++ v technologii IntelliSense a jazykové služby a také v operacích sestavení a ladění.

Pokud více projektů CMake používá stejný název konfigurace CMake (například x86-Debug), všechny jsou nakonfigurovány a sestaveny (ve vlastní kořenové složce sestavení), když je tato konfigurace vybrána. Cíle můžete ladit ze všech projektů CMake, které se účastní konfigurace CMake.

   Položka(media/cmake-build-only.png "nabídky cmake") jenom sestavení cmake ![jenom pro sestavení cmake]

Chcete-li omezit sestavení a relace ladění na podmnožinu projektů v pracovním prostoru, vytvořte novou konfiguraci s jedinečným názvem v souboru **CMakeSettings. JSON** a použijte ji pouze pro tyto projekty. Pokud je zvolena tato konfigurace, příkazy IntelliSense a sestavení a ladění jsou povoleny pouze pro ty zadané projekty.

## <a name="troubleshooting-cmake-cache-errors"></a>Řešení chyb v mezipaměti CMake

Pokud potřebujete další informace o stavu mezipaměti CMake pro diagnostiku problému, otevřete hlavní nabídku **cmake** nebo místní nabídku **CMakeLists. txt** v **Průzkumník řešení** a spusťte jeden z těchto příkazů:

- Možnost **Zobrazit mezipaměť** otevře soubor CMakeCache. txt z kořenové složky sestavení v editoru. (Všechny úpravy, které uděláte v CMakeCache. txt, se při vyčištění mezipaměti vymažou. Pokud chcete provést změny, které budou trvalé po vyčištění mezipaměti, přečtěte si téma [přizpůsobení nastavení cmake](customize-cmake-settings.md).)

- **Složka otevřít mezipaměť** otevře okno Průzkumníka s kořenovou složkou sestavení.

- **Vyčištění mezipaměti** odstraní kořenovou složku sestavení tak, aby další krok konfigurace cmake začínal z čisté mezipaměti.

- **Vygenerovat mezipaměť** vynutí spuštění kroku generovat, i když Visual Studio posuzuje prostředí v aktuálním stavu.

Automatickou generaci mezipaměti je možné zakázat v dialogovém okně **nástroje > možnosti > cmake > obecné** .

## <a name="single-file-compilation"></a>Kompilace jednoho souboru

Chcete-li vytvořit jeden soubor v projektu CMake, klikněte pravým tlačítkem na soubor v **Průzkumník řešení** a vyberte možnost **kompilovat**. Můžete také vytvořit soubor, který je aktuálně otevřený v editoru pomocí hlavní nabídky CMake:

![Kompilace jednoho souboru CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Spuštění CMake z příkazového řádku

Pokud jste nainstalovali CMake z Instalační program pro Visual Studio, můžete ji spustit z příkazového řádku pomocí následujících kroků:

1. Spusťte příslušný vsdevcmd. bat (x86/x64). Další informace naleznete v tématu [sestavování na příkazovém řádku](building-on-the-command-line.md) .

1. Přepněte do výstupní složky.

1. Spusťte CMake a sestavte/nakonfigurujte svoji aplikaci.

::: moniker-end

::: moniker range="vs-2015"

V sadě Visual Studio 2015 mohou uživatelé sady Visual Studio použít [generátor cmake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) k vygenerování souborů projektu MSBuild, které rozhraní IDE pak spotřebuje pro technologii IntelliSense, procházení a kompilaci.

::: moniker-end


## <a name="see-also"></a>Další informace najdete v tématech

[Kurz: vytváření C++ projektů pro různé platformy v aplikaci Visual Studio](get-started-linux-cmake.md)<br/>
[Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)<br/>
[Připojení ke vzdálenému počítači se systémem Linux](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Přizpůsobení nastavení sestavení CMake](customize-cmake-settings.md)<br/>
[Odkaz na CMakeSettings. JSON](cmakesettings-reference.md)<br/>
[Konfigurace relací ladění CMake](configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu pro Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Odkaz na předdefinovaný konfigurační odkaz CMake](cmake-predefined-configuration-reference.md)<br/>
