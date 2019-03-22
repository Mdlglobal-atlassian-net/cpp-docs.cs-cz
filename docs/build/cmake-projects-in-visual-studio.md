---
title: Projekty CMake v sadě Visual Studio
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 84511c0712fffcacc1f90d4bde808620e0a0ab0f
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356138"
---
# <a name="cmake-projects-in-visual-studio"></a>Projekty CMake v sadě Visual Studio

CMake je nástroj pro různé platformy, open source definovat procesy sestavení, které běží na různých platformách. Tento článek předpokládá, že máte zkušenosti s CMake. Další informace o něm na [sestavení, testování a balíček svůj Software s CMake](https://cmake.org/).

V sadě Visual Studio 2015, Visual Studio uživatelé můžou použít [generátoru CMake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) a vygenerujte soubory projektu MSBuild, které prostředí IDE potom využívá pro technologii IntelliSense, procházení a kompilace.

Visual Studio 2017 přináší bohatou podporu pro CMake, včetně [multiplatformní projekty CMake](../linux/cmake-linux-project.md). **Nástroje Visual C++ pro CMake** komponenta používá **otevřít složku** funkce umožňuje rozhraní IDE využívat soubory projektu CMake (například soubor CMakeLists.txt) přímo pro účely technologie IntelliSense a procházení. Generátory Ninja a sady Visual Studio jsou podporovány. Pokud používáte Visual Studio generátor, dočasný projekt souboru se vygeneruje a předat msbuild.exe, ale je nikdy načtena pro IntelliSense nebo prohlížením účely. Můžete importovat existující mezipaměť CMake; Visual Studio automaticky vybere vlastní proměnné a vytvoří předem naplněných **CMakeSettings.json** souboru. 

## <a name="installation"></a>Instalace

**Nástroje Visual C++ pro CMake** je ve výchozím nastavení nainstalován jako součást **vývoj desktopových aplikací pomocí C++** pracovního vytížení a jako součást **vývoj pro Linux v C++** pracovního vytížení.

![Komponenta CMake v C++ Desktop](media/cmake-install.png)

Další informace najdete v tématu [, nainstalujte úlohu C++ Linux v sadě Visual Studio](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>Integrace integrovaného vývojového prostředí

Pokud zvolíte **soubor | Otevřít | Složka** otevřete složku obsahující soubor CMakeLists.txt, se stane následujících věcí:

- Visual Studio přidá **CMake** položky nabídky do hlavní nabídky, s příkazy pro prohlížení a úpravy skriptů CMake.

- **Průzkumník řešení** zobrazí strukturu složek a souborů.

- Visual Studio spustí CMake.exe a volitelně generuje mezipaměť CMake pro výchozí *konfigurace*, což je x86 ladění. CMake příkazového řádku se zobrazí v **okno výstup**, společně s další výstup z CMake.

- Na pozadí spustí aplikace Visual Studio k indexování zdrojové soubory, které chcete povolit technologii IntelliSense, informací o procházení, refaktoring a tak dále. Při práci, Visual Studio sleduje změny v editoru a taky na disku pro synchronizaci jeho indexů se zdroji.

Můžete otevřít složek, které neobsahují libovolný počet projekty CMake. Visual Studio zjistí a nakonfiguruje všechny soubory "root" soubor CMakeLists.txt ve vašem pracovním prostoru. Operace CMake (konfigurovat, vytvářet, ladit) stejně jako C++ IntelliSense a procházení jsou k dispozici pro všechny projekty CMake v pracovním prostoru.

![Projekt CMake s více kořenových adresářů](media/cmake-multiple-roots.png)

Můžete také zobrazit projekty logicky uspořádané podle cíle. Zvolte **cílí na zobrazení** z rozevíracího seznamu v **Průzkumníka řešení** nástrojů:

![Tlačítko pro zobrazení cílů CMake](media/cmake-targets-view.png)

Visual Studio používá soubor s názvem **CMakeSettings.json** k uložení proměnné prostředí nebo parametrů příkazového řádku pro Cmake.exe. **CMakeSettings.json** také umožňuje vám umožňuje definovat a ukládat více CMake konfigurace sestavení a snadno mezi nimi přepínat v integrovaném vývojovém prostředí. 

Jinak použijte **CMakeLists.txt** stejně jako by v každém projektu CMake pro určení zdrojové soubory, najít knihovny, nastavit možnosti kompilátoru a propojovacího programu a zadáte druhého sestavení systému související informace.

Pokud potřebujete předat argumenty do spustitelného souboru chvíli ladění, můžete použít jiný soubor s názvem **souboru launch.vs.json**. V některých scénářích sady Visual Studio automaticky vytvoří tyto soubory. můžete upravit je ručně. Můžete také vytvořit soubor sami.

> [!NOTE]
> Pro jiné typy projektů, otevřete složku se používají dva další soubory JSON: **CppProperties.json** a **tasks.vs.json**. Ani jeden z nich jsou relevantní pro projekty CMake.

## <a name="import-an-existing-cache"></a>Importovat stávající mezipaměti

Při importu stávajícího souboru CMakeCache.txt sady Visual Studio automaticky vybere vlastní proměnné a vytvoří předem naplněných [ **CMakeSettings.json** ](#cmake_settings) na jejich základě souboru. Původní mezipaměti není žádným způsobem upravit a je stále možné z příkazového řádku nebo pomocí libovolné nástrojů nebo integrovaného vývojového prostředí byla použita k jeho vygenerování. Nové **CMakeSettings.json** soubor umístěn společně s projektu kořenový soubor CMakeLists.txt. Visual Studio vygeneruje nové mezipaměti na základě souboru nastavení. Můžete přepsat generování automatických mezipaměti v **nástroje | Možnosti | CMake | Obecné** dialogového okna.

Ne vše, co v mezipaměti je importován.  Vlastnosti, jako je generátor kódu a umístění kompilátory jsou nahrazeny výchozích hodnot, které se ví, že dobře fungují s integrovaného vývojového prostředí.

### <a name="to-import-an-existing-cache"></a>Chcete-li importovat existující mezipaměti

1. V hlavní nabídce zvolte **soubor | Otevřít | CMake**:

   ![Otevřete CMake](media/cmake-file-open.png "souboru, otevřít, CMake")

   Tím se zobrazí **Import CMake z mezipaměti** průvodce.

2. Přejděte k souboru CMakeCache.txt, který chcete importovat a potom klikněte na tlačítko **OK**. **Importem projektu CMake z mezipaměti** průvodce se zobrazí:

   ![Importovat mezipaměť CMake](media/cmake-import-wizard.png "otevřete Průvodce importem mezipaměti CMake")

   Po dokončení průvodce se zobrazí nový soubor CMakeCache.txt v **Průzkumníka řešení** vedle kořenový soubor CMakeLists.txt ve vašem projektu.

## <a name="building-cmake-projects"></a>Vytváření projektů CMake

Pokud chcete vytvořit projekt CMake, máte tyto možnosti:

1. Na panelu nástrojů obecné najít **konfigurace** rozevírací seznam; ve výchozím nastavení je vybrané pravděpodobně "Linux-Debug" nebo "x64-Debug". Vyberte požadované konfigurace a stiskněte klávesu **F5**, nebo klikněte na tlačítko **spustit** (zeleným trojúhelníkem) tlačítko na panelu nástrojů. Automaticky sestavení projektu nejprve, stejně jako řešení sady Visual Studio.

1. Klikněte pravým tlačítkem na soubor CMakeLists.txt a vyberte **sestavení** v místní nabídce. Pokud máte více cílů ve struktuře složek, můžete všechna nebo jenom jeden konkrétní cíl sestavení.

1. V hlavní nabídce vyberte **sestavení | Vytvoření řešení** (**F7** nebo **Ctrl + Shift + B**). Ujistěte se, že cíl CMake je už vybraná ve **položku při spuštění** rozevírací seznam v **Obecné** nástrojů.

![Vytvoření příkazu nabídky CMake](media/cmake-build-menu.png "CMake vytvoření příkazu nabídky")

Konfigurace sestavení, proměnné, argumenty příkazového řádku a další nastavení můžete přizpůsobit beze změny soubor CMakeLists.txt pomocí **CMakeSettings.json** souboru. Další informace najdete v tématu [nastavení přizpůsobení CMake](customize-cmake-settings.md).

Jak by jste očekávali, výsledky sestavení jsou uvedeny v **okno výstup** a **seznam chyb**.

![Chyby sestavení CMake](media/cmake-build-errors.png "chyby sestavení CMake")

Ve složce s více cílů pro sestavení, můžete použít **sestavení** položku **CMake** nabídky nebo **CMakeLists.txt** kontextovou nabídku k určení, které se zaměřují CMake k sestavení. Stisknutím klávesy **Ctrl + Shift + B** ve CMake projekt se sestaví aktuálně aktivní dokument.

## <a name="debugging-cmake-projects"></a>Ladění projektů CMake

Chcete-li ladit projekt CMake, vyberte požadované konfigurace a stiskněte klávesu **F5**, nebo stisknutím klávesy **spustit** tlačítko na panelu nástrojů. Pokud **spustit** tlačítku zobrazeno "Vybrat položku při spuštění", vyberte šipku rozevíracího seznamu a vyberte cíl, který chcete spustit. (V projektu CMake, "aktuální dokument" možnost je platná pouze pro soubory .cpp.)

![Spuštění CMake tlačítko](media/cmake-run-button.png "CMake spustit tlačítko")

**Spustit** nebo **F5** příkazy nejprve sestavte projekt, pokud se změnily od předchozího sestavení.

Můžete přizpůsobit CMake nastavením vlastností v relaci ladění **souboru launch.vs.json** souboru. Další informace najdete v tématu [konfigurace CMake ladicími relacemi](configure-cmake-debugging-sessions.md).


## <a name="editing-cmakeliststxt-files"></a>Úprava souborů CMakeLists.txt

Chcete-li upravit soubor CMakeLists.txt, klikněte pravým tlačítkem myši na soubor v **Průzkumníka řešení** a zvolte **otevřít**. Pokud provedete změny do souboru, se zobrazí žlutá stavový řádek a vás informuje, že technologie IntelliSense se aktualizuje a vám dává možnost zrušit operaci aktualizace. Informace o soubor CMakeLists.txt, najdete v článku [CMake dokumentaci](https://cmake.org/documentation/).

   ![Úpravy souboru CMakeLists.txt](media/cmake-cmakelists.png "úpravy souboru CMakeLists.txt")

Jakmile soubor uložíte, krok konfigurace automaticky znovu spustí a zobrazí informace v **výstup** okna. Chyby a upozornění se zobrazují v **seznam chyb** nebo **výstup** okna. Poklikejte na chybu **seznam chyb** přejděte k problémovému řádku v soubor CMakeLists.txt.

   ![Chyby soubor CMakeLists.txt](media/cmake-cmakelists-error.png "chyby souboru CMakeLists.txt")


## <a name="cmake-configure-step"></a>Krok konfigurace CMake

Když jsou provedeny významné změny **CMakeSettings.json** nebo na soubor CMakeLists.txt soubory sady Visual Studio automaticky znovu spustí CMake krok konfigurace. Krok konfigurace dokončí bez chyb, informace, které jsou shromažďovány, je k dispozici v C++ IntelliSense a jazykových služeb a také v sestavení a ladění operace.

Když více projektů CMake použijte stejný název konfigurace CMake (například x86-Debug), všechny z nich jsou konfigurovány a integrovanou (vlastní sestavení do kořenové složky) při výběru této konfigurace. Můžete ladit cíle ze všech projektů CMake, které jsou součástí konfigurace CMake.

   ![CMake vytvářet pouze položky nabídky](media/cmake-build-only.png "CMake vytvářet pouze položky nabídky")

Abyste omezili sestavení a ladění relace dílčích projektů v pracovním prostoru, vytvořit novou konfiguraci s jedinečným názvem ve značce **CMakeSettings.json** soubor a použít ji pro projekty pouze. Pokud je vybraná tato konfigurace, technologie IntelliSense a sestavení a ladění příkazy jsou povoleny pouze pro zadané projekty.

## <a name="troubleshooting-cmake-cache-errors"></a>Řešení potíží s chybami mezipaměti CMake

Pokud potřebujete další informace o stavu mezipaměti CMake k diagnostice problému, otevřete **CMake** hlavní nabídky nebo **CMakeLists.txt** kontextové nabídky **Průzkumníka řešení**na některou z těchto příkazů:

- **Zobrazení mezipaměti** otevře soubor CMakeCache.txt z kořenové složky sestavení v editoru. (Veškeré úpravy provedené tady CMakeCache.txt jsou dojde k vymazání Pokud vyčištění mezipaměti. Pokud chcete provést změny, které se zachovávají po vyčištění mezipaměti, naleznete v tématu [CMake nastavení a vlastní konfigurace](#cmake_settings) dříve v tomto článku.)

- **Otevřít složku mezipaměti** se otevře okno Průzkumníka ke kořenové složce sestavení.

- **Vyčištění mezipaměti** odstraní kořenové složce sestavení tak, aby krok začíná od čistá mezipaměť konfigurace další CMake.

- **Vygenerovat mezipaměť** vynutí generovat kroku spustit i v případě, že aplikace Visual Studio považuje aktuální prostředí.

Generování automatických mezipaměti můžete zakázat na **nástroje | Možnosti | CMake | Obecné** dialogového okna.

## <a name="single-file-compilation"></a>Kompilace jednoho souboru

Pokud chcete vytvořit jeden soubor projektu CMake, klikněte pravým tlačítkem na soubor v **Průzkumníka řešení** a zvolte **kompilaci**. Můžete také vytvořit soubor, který je právě otevřen v editoru pomocí hlavní nabídky CMake:

![Kompilace jednoho souboru CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Spuštění CMake z příkazového řádku

Pokud jste nainstalovali CMake z instalačního programu sady Visual Studio, můžete ji spustit z příkazového řádku pomocí následujících kroků:

1. Spusťte příslušné vsdevcmd.bat (x86/x64). Zobrazit [sestavení na příkazovém řádku](building-on-the-command-line.md) Další informace.

1. Přepnout do výstupní složky.

1. Spuštění CMake, sestavení a konfiguraci vaší aplikace.
  
## <a name="see-also"></a>Viz také

[Kurz: Vytváření projektů v jazyce C++ pro různé platformy v sadě Visual Studio](get-started-linux-cmake.md)<br/>
[Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)<br/>
[Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Vlastní nastavení sestavení CMake](customize-cmake-settings.md)<br/>
[Referenční informace k CMakeSettings.json](cmakesettings-reference.md)<br/>
[Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referenční dokumentace ke konfiguraci CMake předdefinované](cmake-predefined-configuration-reference.md)<br/>
