---
title: Vlastní nastavení sestavení CMake v sadě Visual Studio
ms.date: 05/16/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: d8102250fa59dc787cc48fc293ac740b81b4446c
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837111"
---
# <a name="customize-cmake-build-settings"></a>Vlastní nastavení sestavení CMake

::: moniker range="vs-2019"

V aplikaci Visual Studio 2019 nebo novější, můžete přidat konfigurace a jejich nastavení můžete přizpůsobit pomocí **editor nastavení CMake**. Editor je určen jako jednodušší alternativu k ruční úpravou souboru CMakeSettings.json, ale pokud chcete soubor upravit přímo, můžete kliknout **upravit JSON** odkaz v pravém horním rohu editoru. 

Pokud chcete otevřít editor, klikněte na **konfigurace** rozevírací seznam v hlavním panelu nástrojů a zvolte **spravovat konfigurace**.

![Konfigurace CMake rozevíracího seznamu](media/vs2019-cmake-manage-configurations.png)

Teď vidíte **nastavení editoru** konfigurací nainstalované na levé straně. 

![Editor nastavení CMake](media/cmake-settings-editor.png)

Visual Studio ve výchozím nastavení poskytuje dvě konfigurace: `x64-Debug` a `x86-Debug`. Další konfigurace, které můžete přidat kliknutím na zelený symbol plus. Nastavení, která se zobrazí v editoru se může lišit v závislosti na tom, které je vybrané konfigurace.

Možnosti, které vyberete v editoru se zapisují do souboru s názvem souboru CMakeSettings.json. Tento soubor obsahuje argumenty příkazového řádku a proměnných prostředí, které jsou předány do programu CMake při sestavování projektů. Visual Studio nikdy upraví soubor CMakeLists.txt automaticky. prostřednictvím souboru CMakeSettings.json můžete přizpůsobit prostřednictvím sady Visual Studio a nechat uložené soubory projektu CMake beze změny tak, aby jiní členové týmu mohou využívat jakékoli nástroje používají.

## <a name="cmake-general-settings"></a>Obecné nastavení CMake

Následující nastavení jsou k dispozici v rámci **Obecné** nadpisu:

### <a name="configuration-name"></a>Název konfigurace

Odpovídá **název** nastavení. Toto je název, který se zobrazí C++ rozevírajícího seznamu konfigurace. Můžete použít `${name}` – makro k vytvoření dalších hodnot vlastností, jako je například cesty.


### <a name="configuration-type"></a>Typ konfigurace

Odpovídá **výběru typu konfigurace** nastavení. Definuje typ konfigurace sestavení pro vybraný generátor. Aktuálně podporované hodnoty jsou "Debug", "MinSizeRel", "Verze" a "RelWithDebInfo".

### <a name="toolset"></a>Sada nástrojů

Odpovídá **inheritedEnvironments** nastavení. Definuje kompilátoru prostředí, který se použije k vybrané konfiguraci sestavení. Podporované hodnoty závisí na typu konfigurace. Chcete-li vytvořit vlastní prostředí, klikněte na tlačítko **upravit JSON** odkaz v pravém horním rohu editoru nastavení a přímo upravit soubor CMakeSettings.json.

### <a name="cmake-toolchain-file"></a>Soubor sady nástrojů CMake

Cesta k souboru sady nástrojů CMake. Se předají do programu CMake jako "-DCMAKE_TOOLCHAIN_FILE = \<cesta_k_souboru >".

### <a name="build-root"></a>Vytváření kořenové

Odpovídá **buildRoot**. Mapuje **-DCMAKE_BINARY_DIR** přepnutí a určuje, kde se vytvoří mezipaměť CMake. Pokud složka neexistuje, vytvoří se.

## <a name="command-arguments"></a>Argumenty příkazu

Následující nastavení jsou k dispozici v rámci **argumenty příkazového** nadpisu:

### <a name="cmake-command-arguments"></a>Argumenty příkazu CMake

Odpovídá **cmakeCommandArgs**. Určuje další přepínače, které chcete předat CMake.exe.

### <a name="build-command-arguments"></a>Argumenty příkazu

Odpovídá **buildCommandArgs**: Určuje další přepínače k předání do základního sestavovací systém. Například předávání - v, při použití generátor Ninja vynutí Ninja výstup příkazové řádky.


### <a name="ctest-command-arguments"></a>Argumenty příkazu CTest

Odpovídá**ctestCommandArgs**: Určuje další přepínače, které mají být předány do programu CTest při spouštění testů.

## <a name="general-settings-for-remote-builds"></a>Obecná nastavení pro vzdálené sestavení

Konfigurace jako je Linux, které používají Vzdálená sestavení jsou také následující nastavení k dispozici:

### <a name="rsync-command-arguments"></a>argumenty pro příkaz RSync

Zadejte všechny argumenty příkazu pro předaná pro příkaz rsync. 

## <a name="cmake-variables-and-cache"></a>Proměnné CMake a mezipaměť

Tato nastavení umožňují nastavit proměnné CMake a uložit do souboru CMakeSettings.json. Tyto budou v okamžiku sestavení předané do programu CMake a přepíše jakékoli hodnot je možné soubor CMakeLists.txt. V této části můžete použít stejným způsobem, který můžete použít CMakeGUI zobrazíte seznam všech dostupných k úpravám proměnných CMake. Klikněte na tlačítko **uložit a vygenerovat mezipaměť** tlačítko Zobrazit seznam všech proměnných CMake k dispozici pro úpravy, včetně pokročilých proměnných (za CMakeGUI). Seznam můžete filtrovat podle názvu proměnné. 

Odpovídá **proměnné**: obsahuje dvojice název hodnota proměnné CMake, které budou získat předány jako **-D** *_název_ =  _Hodnota_* do programu CMake. Pokyny k sestavení projektu CMake zadání přidání všech proměnných přímo do souboru mezipaměti CMake, se doporučuje jste je přidali tady místo.

## <a name="advanced-settings"></a>Pokročilá nastavení

### <a name="cmake-generator"></a>Generátoru CMake

Odpovídá **generátor**: mapuje na CMake **- G** přepnutí a určuje generátor, který se má použít. Tato vlastnost slouží také jako makra, `${generator}`, při vytváření dalších hodnot vlastností. Visual Studio v současné době podporuje následující generátorů CMake:

  - "Ninja"
  - "Soubory pravidel systému Unix"
  - "Visual Studio 16 2019"
  - "Visual Studio 16 2019 Win64"
  - - "Visual Studio 16 2019 ARM"
  - "Visual Studio 15 2017"
  - "Visual Studio 15 2017 Win64"
  - "Visual Studio 15 2017 ARM"
  - "Visual Studio 14 2015"
  - "Visual Studio 14 2015 Win64"
  - "Visual Studio 14 2015 ARM"
  
  Protože Ninja je určená pro rychlé sestavení rychlosti místo flexibilitu a funkce, je nastavit jako výchozí. Některé projekty CMake, ale možná nebudete moct správně programujte Ninja. Pokud k tomu dojde, můžete dát pokyn CMake pro generování projektu sady Visual Studio místo.

### <a name="intellisense-mode"></a>Režim IntelliSense

Pro přesné technologie IntelliSense nastavte na odpovídající hodnoty pro váš projekt.

### <a name="install-directory"></a>Instalační adresář

Adresář, ve kterém CMake nainstaluje cíle, které se sestaví.

### <a name="cmake-executable"></a>Spustitelný soubor CMake

Úplná cesta ke spustitelnému souboru CMake, včetně názvu souboru a přípony. Pro vzdálené sestavení zadejte umístění CMake na vzdáleném počítači.

Konfigurace jako je Linux, které používají Vzdálená sestavení jsou také následující nastavení k dispozici:

### <a name="remote-cmakeliststxt-root"></a>Vzdálený kořen CMakeLists.txt

Adresář ve vzdáleném počítači, který obsahuje kořenový soubor CMakeLists.txt.

### <a name="remote-install-root"></a>Kořen Vzdálená instalace

Adresář ve vzdáleném počítači, ve kterém CMake nainstaluje cíle.

### <a name="remote-copy-sources"></a>Vzdálená kopie zdroje

Určuje, jestli se má kopírovat zdrojové soubory na vzdálený počítač a umožní vám určit, zda se příkaz rsync nebo sftp. 

## <a name="directly-edit-cmakesettingsjson"></a>Directly edit CMakeSettings.json

Můžete také přímo upravit `CMakeSettings.json` k vytvoření vlastní konfigurace. **Nastavení editoru** má **upravit JSON** tlačítko v pravém horním rohu, který otevře soubor pro úpravy. 

Následující příklad ukazuje ukázkové konfiguraci, kterou můžete použít jako výchozí bod:

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

Technologie IntelliSense JSON umožňuje upravit `CMakeSettings.json` souboru:

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

JSON editor se také poznáte, když zvolíte nekompatibilní nastavení.

Další informace o jednotlivých vlastností v souboru najdete v tématu [referenční dokumentace schématu souboru CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 obsahuje několik konfigurací CMake, které definují, jak je CMake.exe vyvolá pro vytvoření mezipaměti CMake pro daný projekt. Chcete-li přidat novou konfiguraci, klikněte na konfigurace rozevíracího seznamu na panelu nástrojů a zvolte **spravovat konfigurace**:

   ![Správa konfigurací CMake](media/cmake-manage-configurations.png)

Můžete vybrat ze seznamu předdefinovaných konfigurací:

   ![Konfigurace předdefinovaných CMake](media/cmake-configurations.png)

Při prvním vyberte konfiguraci, vytvoří Visual Studio `CMakeSettings.json` soubor v kořenové složce vašeho projektu. Tento soubor slouží k vytvoření souboru mezipaměti CMake znovu například po **Vyčistit** operace. 

Chcete-li přidat další konfiguraci, klikněte pravým tlačítkem myši klikněte na tlačítko `CMakeSettings.json` a zvolte **Přidat konfiguraci**. 

   ![Přidat CMake konfiguraci](media/cmake-add-configuration.png "CMake Přidat konfiguraci")

Můžete také upravit soubor pomocí **Editor nastavení CMake**. Klikněte pravým tlačítkem na `CMakeSettings.json` v **Průzkumníka řešení** a zvolte **upravit nastavení CMake**. Nebo vyberte **spravovat konfigurace** z konfigurace rozevíracího seznamu v horní části okna editoru. 

Můžete také přímo upravit `CMakeSettings.json` k vytvoření vlastních konfigurací následující příklad ukazuje ukázkové konfiguraci, kterou můžete použít jako výchozí bod:

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

Technologie IntelliSense JSON umožňuje upravit `CMakeSettings.json` souboru:

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Další informace o jednotlivých vlastností v souboru najdete v tématu [referenční dokumentace schématu souboru CMakeSettings.json](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Viz také:

[Projekty CMake v sadě Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)<br/>
[Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referenční dokumentace ke konfiguraci CMake předdefinované](cmake-predefined-configuration-reference.md)<br/>
