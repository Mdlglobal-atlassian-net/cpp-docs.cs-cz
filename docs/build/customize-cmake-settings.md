---
title: Přizpůsobení nastavení buildu CMake v sadě Visual Studio
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: ecd2964e035cbf3d48a737164b0067720e9b6b9a
ms.sourcegitcommit: 0df462d79ad617296095c3012badc2fe669bab2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69887056"
---
# <a name="customize-cmake-build-settings"></a>Vlastní nastavení sestavení CMake

::: moniker range="vs-2019"

V sadě Visual Studio 2019 a novějších můžete přidat konfigurace a přizpůsobit jejich nastavení pomocí **editoru nastavení cmake**. Editor je určený jako jednodušší alternativa k ruční úpravě souboru *CMakeSettings. JSON* , ale pokud dáváte přednost úpravám souboru přímo, můžete kliknout na odkaz **Upravit JSON** v pravém horním rohu editoru. 

Chcete-li otevřít Editor, klikněte na rozevírací nabídku **Konfigurace** na hlavním panelu nástrojů a vyberte možnost **spravovat konfigurace**.

![Rozevírací seznam konfigurace CMake](media/vs2019-cmake-manage-configurations.png)

Nyní uvidíte **Editor nastavení** s nainstalovanými konfiguracemi na levé straně. 

![Editor nastavení CMake](media/cmake-settings-editor.png)

Visual Studio poskytuje ve `x64-Debug` výchozím nastavení jednu konfiguraci. Kliknutím na zelený symbol plus můžete přidat další konfigurace. Nastavení, která se zobrazí v editoru, se můžou lišit v závislosti na tom, která konfigurace je vybraná.

Možnosti, které zvolíte v editoru, jsou zapsány do souboru s názvem *CMakeSettings. JSON*. Tento soubor poskytuje argumenty příkazového řádku a proměnné prostředí, které se předávají CMaki při sestavování projektů. Visual Studio nikdy nemění *CMakeLists. txt* automaticky; pomocí *CMakeSettings. JSON* si můžete sestavení přizpůsobit prostřednictvím sady Visual Studio a nechat soubory projektu cmake beze změny, aby je ostatní členové týmu mohli využívat bez jakýchkoli nástrojů, které používají.

## <a name="cmake-general-settings"></a>Obecná nastavení CMake

V **Obecné** hlavičce jsou k dispozici následující nastavení:

### <a name="configuration-name"></a>Název konfigurace

Odpovídá nastavení **názvu** . Tento název se zobrazí v C++ rozevírací nabídce konfigurace. `${name}` Makro lze použít k vytvoření dalších hodnot vlastností, jako jsou například cesty.


### <a name="configuration-type"></a>Typ konfigurace

Odpovídá nastavení **výběru** . Definuje typ konfigurace sestavení pro vybraný generátor. Aktuálně podporované hodnoty jsou "debug", "MinSizeRel", "Release" a "RelWithDebInfo". Mapuje se na [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html).

### <a name="toolset"></a>Sada nástrojů

Odpovídá nastavení **inheritedEnvironments** . Definuje prostředí kompilátoru, které se používá k sestavení vybrané konfigurace. Podporované hodnoty závisí na typu konfigurace. Pokud chcete vytvořit vlastní prostředí, klikněte na odkaz **Upravit JSON** v pravém horním rohu editoru nastavení a upravte soubor *CMakeSettings. JSON* přímo.

### <a name="cmake-toolchain-file"></a>Soubor sada nástrojů CMake

Cesta k [souboru sada nástrojů cmake](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html) Tato cesta se předává do cmake jako "-DCMAKE_TOOLCHAIN_FILE \<= FilePath >". Soubory sada nástrojů určují umístění kompilátorů a sada nástrojů nástrojů a další informace o cílové platformě a kompilátoru. Ve výchozím nastavení Visual Studio používá [soubor vcpkg sada nástrojů](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake) , pokud není toto nastavení určeno. 

### <a name="build-root"></a>Kořen sestavení

Odpovídá **buildRoot**. Provede mapování na [CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html)a určuje, kde se má vytvořit mezipaměť cmake. Zadaná složka se vytvoří, pokud neexistuje.

## <a name="command-arguments"></a>Argumenty příkazu

V nadpisu **argumentů příkazu** jsou k dispozici následující nastavení:

### <a name="cmake-command-arguments"></a>Argumenty příkazu CMake

Odpovídá **cmakeCommandArgs**. Určuje další [Možnosti příkazového řádku](https://cmake.org/cmake/help/latest/manual/cmake.1.html) předané do cmake. exe.

### <a name="build-command-arguments"></a>Argumenty příkazu sestavení

Odpovídá **buildCommandArgs**. Určuje další přepínače, které mají být předána základnímu systému sestavení. Například předání `-v` při použití generátoru expertem vynutí expertem pro výstup příkazových řádků.


### <a name="ctest-command-arguments"></a>Argumenty příkazu CTest

Odpovídá **ctestCommandArgs**. Určuje další [Možnosti příkazového řádku](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html) , které se mají předat CTest při spouštění testů.

## <a name="general-settings-for-remote-builds"></a>Obecná nastavení pro vzdálená sestavení

Pro konfigurace, jako je Linux, které používají vzdálené sestavení, jsou k dispozici také následující nastavení:

### <a name="rsync-command-arguments"></a>argumenty příkazu rsync

Další možnosti příkazového řádku předané do [rsync](https://download.samba.org/pub/rsync/rsync.html), rychlý a univerzální nástroj pro kopírování souborů. 

## <a name="cmake-variables-and-cache"></a>CMake – proměnné a mezipaměť

Tato nastavení umožňují nastavit proměnné CMake a uložit je do souboru *CMakeSettings. JSON*. Jsou předány do CMake v době sestavení a přepisují jakékoli hodnoty v souboru *CMakeLists. txt* . Tuto část můžete použít stejným způsobem, jakým můžete použít CMakeGUI k zobrazení seznamu všech proměnných CMak, které jsou k dispozici pro úpravy. Kliknutím na tlačítko **Uložit a generovat mezipaměť** zobrazíte seznam všech proměnných cmake, které jsou k dispozici pro úpravy, včetně pokročilých proměnných (na CMakeGUI). Seznam můžete filtrovat podle názvu proměnné. 

Odpovídá proměnným. Obsahuje dvojici název-hodnota proměnných cmake předaných **jako** *_hodnota_ _názvu_=* pro cmake. Pokud vaše pokyny pro sestavení vašeho projektu CMake určují přidání jakýchkoli proměnných přímo do souboru mezipaměti CMake, doporučujeme je místo toho přidat.

## <a name="advanced-settings"></a>Pokročilá nastavení

### <a name="cmake-generator"></a>Generátor CMake

Odpovídá generátoru. Provede mapování na přepínač CMake **-G** a určí [generátor cmake](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) , který se má použít. Tuto vlastnost lze použít také jako makro, `${generator}`při vytváření dalších hodnot vlastností. Sada Visual Studio aktuálně podporuje následující generátory CMake:

  - Expertem
  - "Soubory pravidel pro UNIX"
  - "Visual Studio 16 2019"
  - "Visual Studio 16 2019 Win64"
  - "Visual Studio 16 2019 ARM"
  - "Visual Studio 15 2017"
  - "Visual Studio 15 2017 Win64"
  - "Visual Studio 15 2017 ARM"
  - "Visual Studio 14 2015"
  - "Visual Studio 14 2015 Win64"
  - "Visual Studio 14 2015 ARM"
  
Vzhledem k tomu, že expertem je navržen pro rychlé rychlosti sestavení místo flexibility a funkce, je nastavena jako výchozí. Některé projekty CMake ale nemusí být možné správně sestavit pomocí expertem. Pokud k tomu dojde, můžete pro CMake dát pokyn pro vygenerování projektu sady Visual Studio.

### <a name="intellisense-mode"></a>Režim IntelliSense

Režim IntelliSense používaný modulem IntelliSense. Pokud není vybrán žádný režim, sada Visual Studio bude dědit ze zadané sady nástrojů.  

### <a name="install-directory"></a>Instalační adresář

Adresář, do kterého se instaluje CMake. Mapuje se na [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html). 

### <a name="cmake-executable"></a>Spustitelný soubor CMake

Úplná cesta ke spustitelnému souboru programu CMake, včetně názvu souboru a přípony Umožňuje používat vlastní verzi CMake v sadě Visual Studio. U vzdálených sestavení určete umístění CMake na vzdáleném počítači.

Pro konfigurace, jako je Linux, které používají vzdálené sestavení, jsou k dispozici také následující nastavení:

### <a name="remote-cmakeliststxt-root"></a>Vzdálený kořenový adresář CMakeLists. txt

Adresář ve vzdáleném počítači, který obsahuje kořenový soubor *CMakeLists. txt* .

### <a name="remote-install-root"></a>Kořenová složka pro vzdálenou instalaci

Adresář ve vzdáleném počítači, ve kterém se instaluje CMake. Mapuje se na [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html). 

### <a name="remote-copy-sources"></a>Vzdálené kopírování zdrojů

Určuje, jestli se mají kopírovat zdrojové soubory do vzdáleného počítače, a umožní vám určit, jestli se má používat rsync nebo SFTP. 

## <a name="directly-edit-cmakesettingsjson"></a>Přímo upravit CMakeSettings. JSON

Můžete také přímo upravit *CMakeSettings. JSON* a vytvořit vlastní konfigurace. **Editor nastavení** obsahuje v pravém horním rohu tlačítko **Upravit JSON** , které otevírá soubor pro úpravy. 

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

JSON IntelliSense vám pomůže s úpravou souboru *CMakeSettings. JSON* :

   ![IntelliSense – JSON] pro cmake (media/cmake-json-intellisense.png "IntelliSense – JSON") pro cmake

Editor JSON vás také informuje, když zvolíte nekompatibilní nastavení.

Další informace o jednotlivých vlastnostech v souboru naleznete v tématu [reference ke schématu CMakeSettings. JSON](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Sada Visual Studio 2017 poskytuje několik konfigurací CMake definujících způsob, jakým se vyvolal CMake. exe pro vytvoření mezipaměti CMake pro daný projekt. Chcete-li přidat novou konfiguraci, klikněte na rozevírací nabídku Konfigurace na panelu nástrojů a vyberte možnost **spravovat konfigurace**:

   ![Správa konfigurací CMake](media/cmake-manage-configurations.png)

Můžete si vybrat ze seznamu předdefinovaných konfigurací:

   ![Předdefinované konfigurace CMake](media/cmake-configurations.png)

Při prvním výběru konfigurace aplikace Visual Studio vytvoří soubor *CMakeSettings. JSON* v kořenové složce vašeho projektu. Tento soubor slouží k opětovnému vytvoření souboru mezipaměti CMake, například po operaci **Vyčištění** . 

Pokud chcete přidat další konfiguraci, klikněte pravým tlačítkem na *CMakeSettings. JSON* a vyberte **Přidat konfiguraci**. 

   ![Přidat konfiguraci cmake](media/cmake-add-configuration.png "Přidat konfiguraci cmake")

Soubor můžete také upravit pomocí **editoru nastavení cmake**. V **Průzkumník řešení** klikněte pravým tlačítkem na *CMakeSettings. JSON* a vyberte **Upravit nastavení cmake**. Případně vyberte možnost **spravovat konfigurace** v rozevíracím seznamu konfigurace v horní části okna editoru. 

Můžete také přímo upravit *CMakeSettings. JSON* a vytvořit vlastní konfigurace. Následující příklad ukazuje ukázkovou konfiguraci, kterou můžete použít jako výchozí bod:

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

JSON IntelliSense vám pomůže s úpravou souboru *CMakeSettings. JSON* :

   ![IntelliSense – JSON] pro cmake (media/cmake-json-intellisense.png "IntelliSense – JSON") pro cmake

Další informace o jednotlivých vlastnostech v souboru naleznete v tématu [reference ke schématu CMakeSettings. JSON](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Viz také:

[Projekty CMake v sadě Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)<br/>
[Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Odkaz na předdefinovaný konfigurační odkaz CMake](cmake-predefined-configuration-reference.md)
