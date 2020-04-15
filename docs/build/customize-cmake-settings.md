---
title: Přizpůsobení nastavení sestavení CMake v sadě Visual Studio
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: c6bd1404799ccc9ad6b689646cd066849d48fca8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328683"
---
# <a name="customize-cmake-build-settings"></a>Vlastní nastavení sestavení CMake

::: moniker range="vs-2019"

V Sadě Visual Studio 2019 a novějších můžete přidat konfigurace a přizpůsobit jejich nastavení pomocí **editoru nastavení CMake**. Editor má být jednodušší alternativou k ruční úpravě souboru *CMakeSettings.json,* ale pokud dáváte přednost úpravě souboru přímo, můžete kliknout na odkaz **Upravit JSON** v pravém horním části editoru.

Chcete-li editor otevřít, klikněte na rozevírací panel **Konfigurace** na hlavním panelu nástrojů a zvolte **Spravovat konfigurace**.

![Rozevírací položky konfigurace CMake](media/vs2019-cmake-manage-configurations.png)

Nyní vidíte **Editor nastavení** s nainstalovanými konfiguracemi vlevo.

![Editor nastavení CMake](media/cmake-settings-editor.png)

Visual Studio `x64-Debug` poskytuje jednu konfiguraci ve výchozím nastavení. Další konfigurace můžete přidat kliknutím na zelené znaménko plus. Nastavení, která se zobrazí v editoru, se mohou lišit v závislosti na vybrané konfiguraci.

Možnosti, které zvolíte v editoru, jsou zapsány do souboru s názvem *CMakeSettings.json*. Tento soubor obsahuje argumenty příkazového řádku a proměnné prostředí, které jsou předány CMake při vytváření projektů. Visual Studio nikdy automaticky upravuje *soubor CMakeLists.txt.* pomocí *CMakeSettings.json* můžete přizpůsobit sestavení prostřednictvím sady Visual Studio a ponechat soubory projektu CMake nedotčené, aby je ostatní členové vašeho týmu mohli využívat pomocí nástrojů, které používají.

## <a name="cmake-general-settings"></a>CMake Obecné nastavení

V nadpisu **Obecné** jsou k dispozici následující nastavení:

### <a name="configuration-name"></a>Název konfigurace

Odpovídá nastavení **názvu.** Tento název se zobrazí v rozevíracím souboru konfigurace jazyka C++. `${name}` Makro můžete použít k komponovat další hodnoty vlastností, například cesty.

### <a name="configuration-type"></a>Typ konfigurace

Odpovídá nastavení **configurationType.** Definuje typ konfigurace sestavení pro vybraný generátor. Aktuálně podporované hodnoty jsou "Ladění", "MinSizeRel", "Release" a "RelWithDebInfo". Mapuje se na [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html).

### <a name="toolset"></a>Sada nástrojů

Odpovídá **zděděné prostředí** nastavení. Definuje prostředí kompilátoru, které se používá k sestavení vybrané konfigurace. Podporované hodnoty závisí na typu konfigurace. Chcete-li vytvořit vlastní prostředí, zvolte odkaz **Upravit JSON** v pravém horním rohu editoru Nastavení a přímo upravte soubor *CMakeSettings.json.*

### <a name="cmake-toolchain-file"></a>Soubor řetězce nástrojů CMake

Cesta k [souboru řetězce nástrojů CMake](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html). Tato cesta je předána CMake \<jako "-DCMAKE_TOOLCHAIN_FILE = cesta k souboru>". Soubory řetězce nástrojů určují umístění kompilátorů a nástrojů řetězce nástrojů a další informace související s cílovou platformou a kompilátorem. Ve výchozím nastavení visual studio používá [soubor řetězce nástrojů vcpkg,](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake) pokud toto nastavení není určeno.

### <a name="build-root"></a>Vytvořit kořen

Odpovídá **buildRoot**. Mapuje na [CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html)a určuje, kde se má vytvořit mezipaměť CMake. Zadaná složka je vytvořena, pokud neexistuje.

## <a name="command-arguments"></a>Argumenty příkazu

V záhlaví **Argumenty příkazu** jsou k dispozici následující nastavení:

### <a name="cmake-command-arguments"></a>CMake argumenty příkazu

Odpovídá **cmakeCommandArgs**. Určuje všechny další [možnosti příkazového řádku](https://cmake.org/cmake/help/latest/manual/cmake.1.html) předané souboru CMake.exe.

### <a name="build-command-arguments"></a>Argumenty příkazů sestavení

Odpovídá **buildCommandArgs**. Určuje další přepínače, které mají být předávány základnímu systému sestavení. Například předávání `-v` při použití generátoru Ninja nutí Ninju k výstupu příkazových řádků.

### <a name="ctest-command-arguments"></a>Argumenty příkazů CTest

Odpovídá **ctestCommandArgs**. Určuje další [možnosti příkazového řádku,](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html) které mají být při spuštění testů předávány ctestu.

## <a name="general-settings-for-remote-builds"></a>Obecná nastavení pro vzdálená sestavení

Pro konfigurace, jako je Linux, které používají vzdálená sestavení, jsou k dispozici také následující nastavení:

### <a name="rsync-command-arguments"></a>argumenty příkazů rsync

Další možnosti příkazového řádku předané [rsync](https://download.samba.org/pub/rsync/rsync.html), rychlý a všestranný nástroj pro kopírování souborů.

## <a name="cmake-variables-and-cache"></a>CMake proměnné a mezipaměť

Tato nastavení umožňují nastavit proměnné CMake a uložit je do *souboru CMakeSettings.json*. Jsou předány CMake v době sestavení a přepsat všechny hodnoty jsou v souboru *CMakeLists.txt.* Tento oddíl můžete použít stejným způsobem, že můžete použít CMakeGUI k zobrazení seznamu všech cmake proměnné, které jsou k dispozici pro úpravy. Kliknutím na tlačítko **Uložit a generovat mezipaměť** zobrazíte seznam všech proměnných CMake, které jsou k dispozici pro úpravy, včetně pokročilých proměnných (podle CMakeGUI). Seznam můžete filtrovat podle názvu proměnné.

Odpovídá **proměnným**. Obsahuje dvojici název-hodnota CMake proměnné předány jako **-D** * _název_=hodnoty* CMake. Pokud vaše CMake projektu sestavení pokyny zadat přidání všechny proměnné přímo do souboru mezipaměti CMake, doporučujeme přidat je zde místo.

## <a name="advanced-settings"></a>Upřesnit nastavení

### <a name="cmake-generator"></a>CMake generátor

Odpovídá **generátoru**. Mapuje na přepínač CMake **-G** a určuje [generátor CMake,](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) který se má použít. Tuto vlastnost lze také použít `${generator}`jako makro , při vytváření jiných hodnot vlastností. Visual Studio aktuálně podporuje následující generátory CMake:

- "Ninja"
- "Unix makefiles"
- "Visual Studio 16 2019"
- "Visual Studio 16 2019 Win64"
- "Visual Studio 16 2019 ARM"
- "Visual Studio 15 2017"
- "Visual Studio 15 2017 Win64"
- "Visual Studio 15 2017 ARM"
- "Visual Studio 14 2015"
- "Visual Studio 14 2015 Win64"
- "Visual Studio 14 2015 ARM"
  
Protože Ninja je navržen pro rychlé rychlosti sestavení namísto flexibility a funkce, je nastaven jako výchozí. Některé projekty CMake však nemusí být schopen správně sestavit pomocí Ninja. Pokud k tomu dojde, můžete pokyn CMake generovat projekt sady Visual Studio místo.

### <a name="intellisense-mode"></a>Režim IntelliSense

Režim IntelliSense používaný motorem IntelliSense. Pokud není vybrán žádný režim, pak Visual Studio dědí ze zadané sady nástrojů.  

### <a name="install-directory"></a>Nainstalovat adresář

Adresář, ve kterém CMake instaluje cíle. Mapy na [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="cmake-executable"></a>CMake spustitelný soubor

Úplná cesta ke spustitelnému souboru programu CMake, včetně názvu souboru a přípony. Umožňuje používat vlastní verzi CMake s Visual Studio. Pro vzdálená sestavení zadejte umístění CMake ve vzdáleném počítači.

Pro konfigurace, jako je Linux, které používají vzdálená sestavení, jsou k dispozici také následující nastavení:

### <a name="remote-cmakeliststxt-root"></a>Vzdálený kořen CMakeLists.txt

Adresář ve vzdáleném počítači, který obsahuje kořenový soubor *CMakeLists.txt.*

### <a name="remote-install-root"></a>Kořenová instalace vzdálené instalace

Adresář na vzdáleném počítači, ve kterém CMake instaluje cíle. Mapy na [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="remote-copy-sources"></a>Zdroje vzdálené kopie

Určuje, zda se mají kopírovat zdrojové soubory do vzdáleného počítače, a umožňuje určit, zda se má použít rsync nebo sftp.

## <a name="directly-edit-cmakesettingsjson"></a>Přímo upravit CMakeSettings.json

Můžete také přímo upravit *CMakeSettings.json* vytvořit vlastní konfigurace. **Editor nastavení** má v pravém horním horním části tlačítko **Upravit JSON,** které otevírá soubor pro úpravy.

Následující příklad ukazuje ukázkovou konfiguraci, kterou můžete použít jako výchozí bod:

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
```

Technologie JSON IntelliSense pomáhá upravovat soubor *CMakeSettings.json:*

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Editor JSON vás také informuje, když zvolíte nekompatibilní nastavení.

Další informace o jednotlivých vlastnostech v souboru naleznete v [tématu CMakeSettings.json odkaz na schéma](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 poskytuje několik cmake konfigurace, které definují, jak CMake.exe je vyvolána k vytvoření mezipaměti CMake pro daný projekt. Chcete-li přidat novou konfiguraci, klepněte na rozevírací soubor konfigurace na panelu nástrojů a zvolte **Spravovat konfigurace**:

   ![CMake spravovat konfigurace](media/cmake-manage-configurations.png)

Můžete si vybrat ze seznamu předdefinovaných konfigurací:

   ![CMake předdefinované konfigurace](media/cmake-configurations.png)

Při prvním výběru konfigurace vytvoří visual studio soubor *CMakeSettings.json* v kořenové složce projektu. Tento soubor se používá k opětovnému vytvoření souboru mezipaměti CMake, například po operaci **Clean.**

Chcete-li přidat další konfiguraci, klepněte pravým tlačítkem myši na soubor *CMakeSettings.json* a zvolte **Přidat konfiguraci**.

   ![CMake Přidat konfiguraci](media/cmake-add-configuration.png "CMake Přidat konfiguraci")

Soubor můžete také upravit pomocí **Editoru nastavení CMake**. Klepněte pravým tlačítkem myši na *soubor CMakeSettings.json* v **Průzkumníku řešení** a zvolte **Upravit nastavení CMake**. Nebo vyberte **Spravovat konfigurace** z rozbalovacího okna konfigurace v horní části okna editoru.

Můžete také přímo upravit *CMakeSettings.json* vytvořit vlastní konfigurace. Následující příklad ukazuje ukázkovou konfiguraci, kterou můžete použít jako výchozí bod:

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
```

Technologie JSON IntelliSense pomáhá upravovat soubor *CMakeSettings.json:*

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Další informace o jednotlivých vlastnostech v souboru naleznete v [tématu CMakeSettings.json odkaz na schéma](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Viz také

[CMake projekty v sadě Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)<br/>
[Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake předdefinovaný odkaz na konfiguraci](cmake-predefined-configuration-reference.md)
