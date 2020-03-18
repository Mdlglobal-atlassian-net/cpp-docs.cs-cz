---
title: Reference ke schématu CMakeSettings. JSON
ms.date: 11/22/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 542a469393d3655418f69e5d51d59adfa824ad15
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417388"
---
# <a name="cmakesettingsjson-schema-reference"></a>Reference ke schématu CMakeSettings. JSON

::: moniker range="vs-2015"

Projekty CMake jsou podporovány v sadě Visual Studio 2017 a novějších.

::: moniker-end

::: moniker range=">=vs-2017"

Soubor **CMakeSettings. JSON** obsahuje informace, které sada Visual Studio používá pro technologii IntelliSense a vytváření argumentů příkazového řádku, které předává cmaki. exe pro zadané prostředí *Konfigurace* a kompilátoru. Konfigurace určuje vlastnosti, které se vztahují na konkrétní platformu a typ sestavení, například `x86-Debug` nebo `Linux-Release`. Každá konfigurace určuje prostředí, které zapouzdřuje informace o sadě nástrojů kompilátoru, například MSVC, RSZ nebo Clang. CMake používá argumenty příkazového řádku k opětovnému vygenerování kořenového souboru *CMakeCache. txt* a dalších souborů projektu projektu. Hodnoty lze přepsat v souborech *CMakeLists. txt* . 

Můžete přidat nebo odebrat konfigurace v integrovaném vývojovém prostředí a pak je upravit přímo v souboru JSON nebo pomocí **editoru nastavení cmake** (Visual Studio 2019 a novější). V rozhraní IDE lze snadno přepínat mezi konfiguracemi, aby bylo možné generovat různé soubory projektu. Další informace najdete [v tématu Přizpůsobení nastavení buildu cmake v sadě Visual Studio](customize-cmake-settings.md) .

## <a name="configurations"></a>Konfigurace

Pole `configurations` obsahuje všechny konfigurace pro projekt CMake. Další informace o předdefinovaných konfiguracích najdete v tématu Referenční dokumentace k předdefinovaným [konfiguracím cmake](cmake-predefined-configuration-reference.md) . Do souboru můžete přidat libovolný počet předem definovaných nebo vlastních konfigurací. 

`configuration` má tyto vlastnosti:

- `addressSanitizerEnabled`: Pokud `true` zkompiluje program pomocí programu pro úpravu adresy (experimentální ve Windows). V systému Linux zkompilujete pomocí-FNO-vynechání ukazatele na rámec a úroveň optimalizace kompilátoru – OS nebo-ó pro dosažení nejlepších výsledků.
- `addressSanitizerRuntimeFlags`: příznaky modulu runtime předané do AddressSanitizer prostřednictvím proměnné prostředí ASAN_OPTIONS. Formát: příznak1 = hodnota: flag2 = hodnota2.
- `buildCommandArgs`: Určuje přepínače nativního sestavení předané do CMake po--buildu--. Například v případě, že při použití generátoru expertem vynutí expertem pro výstup příkazových řádků. Další informace o příkazech expertem najdete v tématu [argumenty příkazového řádku expertem](#ninja) .
- `buildRoot`: Určuje adresář, ve kterém CMake generuje skripty sestavení pro zvolený generátor.  Provede mapování na **DCMAKE_BINARY_DIR** přepínač a určí, kde bude vytvořen *CMakeCache. txt* . Pokud složka neexistuje, vytvoří se. Mezi podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `cacheGenerationCommand`: Určuje nástroj příkazového řádku a argumenty, například *ladění gencache. bat* pro vygenerování mezipaměti. Příkaz se spustí z prostředí v zadaném prostředí pro konfiguraci, když uživatel explicitně vyžádá obnovení, nebo se upraví soubor CMakeLists. txt nebo CMakeSettings. JSON.
- `cacheRoot`: Určuje cestu k mezipaměti CMake. Tento adresář by měl obsahovat existující soubor *CMakeCache. txt* .
- `clangTidyChecks`: čárkami oddělený seznam upozornění, které se budou předávat Clang-uklizený; zástupné znaky jsou povoleny a předpona '-' odstraní kontroly.
- `cmakeCommandArgs`: Určuje další možnosti příkazového řádku předané do CMake při vyvolání za účelem generování souborů projektu.
- `cmakeToolchain`: Určuje soubor sada nástrojů. To se předává do CMake pomocí-DCMAKE_TOOLCHAIN_FILE. "
- `codeAnalysisRuleset`: Určuje RuleSet, který se má použít při spuštění nástroje Code Analysis. Může to být úplná cesta nebo název souboru ruleset nainstalovaného aplikací Visual Studio.
- `configurationType`: Určuje konfiguraci typu sestavení pro vybraný generátor. Může to být jedna z těchto:

  - Ladit
  - Vydaná verze
  - MinSizeRel
  - RelWithDebInfo
  
- `ctestCommandArgs`: Určuje další možnosti příkazového řádku předané do CTest při spuštění testů. "
- `description`: Popis této konfigurace, který se zobrazí v nabídkách.
- `enableClangTidyCodeAnalysis`: použijte Clang-uklizený pro analýzu kódu.
- `enableMicrosoftCodeAnalysis`: použijte nástroje pro analýzu kódu Microsoft pro analýzu kódu.
- `generator`: Určuje generátor CMake, který se má pro tuto konfiguraci použít. Může to být jedna z těchto:
  
  **Pouze Visual Studio 2019:**
  - Visual Studio 16 2019
  - Visual Studio 16 2019 Win64
  - Visual Studio 16 2019 ARM

  **Visual Studio 2017 a novější:**
  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - Soubory pravidel pro UNIX
  - Expertem

Vzhledem k tomu, že expertem je navržen pro rychlé rychlosti sestavení místo flexibility a funkce, je nastavena jako výchozí. Některé projekty CMake ale nemusí být možné správně sestavit pomocí expertem. Pokud k tomu dojde, můžete dát CMaki místo toho, aby vygenerovala projekty sady Visual Studio.

Chcete-li určit generátor sady Visual Studio v sadě Visual Studio 2017, otevřete z hlavní nabídky výběrem možnosti **cmake | Změnit nastavení CMake**. Odstraňte text "expertem" a zadejte "V". Tím se aktivuje IntelliSense, který umožňuje zvolit generátor, který chcete.

Chcete-li v sadě Visual Studio 2019 zadat generátor sady Visual Studio, klikněte pravým tlačítkem na soubor *CMakeLists. txt* v **Průzkumník řešení** a zvolte **nastavení cmake pro projekt** > **Zobrazit upřesňující nastavení** > **generátoru cmake**.

Pokud aktivní konfigurace určuje generátor sady Visual Studio, je ve výchozím nastavení vyvolána služba MSBuild. exe s argumenty `-m -v:minimal`. Chcete-li přizpůsobit sestavení v souboru *CMakeSettings. JSON* , můžete zadat další [argumenty příkazového řádku MSBuild](../build/reference/msbuild-visual-cpp-overview.md) , které mají být předány do systému sestavení prostřednictvím vlastnosti `buildCommandArgs`:

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `installRoot`: Určuje adresář, ve kterém CMake generuje cíle instalace pro zvolený generátor. Mezi podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `inheritEnvironments`: Určuje jedno nebo více prostředí kompilátoru, na kterých tato konfigurace závisí. Může se jednat o jakékoli vlastní prostředí nebo některé z předdefinovaných prostředí. Další informace najdete v tématu [prostředí](#environments).
- `intelliSenseMode`: Určuje režim používaný pro výpočet informací technologie IntelliSense. Může to být jedna z těchto:

  - windows-msvc-x86
  - windows-msvc-x64
  - windows-msvc-arm
  - windows-msvc-arm64
  - android-clang-x86
  - android-clang-x64
  - android-clang-arm
  - android-clang-arm64
  - ios-clang-x86
  - ios-clang-x64
  - iOS – Clang – ARM
  - ios-clang-arm64
  - windows-clang-x86
  - windows-clang-x64
  - windows-clang-arm
  - windows-clang-arm64
  - linux-gcc-x86
  - linux-gcc-x64
  - linux-gcc-arm"

- `name`: pojmenuje konfiguraci.  Další informace o předdefinovaných konfiguracích najdete v tématu Referenční dokumentace k předdefinovaným [konfiguracím cmake](cmake-predefined-configuration-reference.md) .
- `wslPath`: cesta ke Spouštěči instance subsystému Windows pro Linux.

### <a name="additional-settings-for-cmake-linux-projects"></a>Další nastavení pro projekty CMake pro Linux

- `remoteMachineName`: Určuje název vzdáleného počítače se systémem Linux, který je hostitelem CMake, sestavení a ladicího programu. Pomocí Správce připojení přidejte nové počítače se systémem Linux. Mezi podporovaná makra patří `${defaultRemoteMachineName}`.
- `remoteCopySourcesOutputVerbosity`: Určuje úroveň podrobností operace kopírování zdroje do vzdáleného počítače. Může to být jedna z "" normálního "," Verbose "nebo" Diagnostic ".
- `remoteCopySourcesConcurrentCopies`: Určuje počet souběžných kopií použitých během synchronizace zdrojů do vzdáleného počítače (pouze SFTP).
- `remoteCopySourcesMethod`: Určuje metodu kopírování souborů do vzdáleného počítače. Může být "rsync" nebo "SFTP".
- `remoteCMakeListsRoot`: Určuje adresář ve vzdáleném počítači, který obsahuje projekt CMake. Mezi podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteBuildRoot`: Určuje adresář ve vzdáleném počítači, ve kterém CMake generuje skripty sestavení pro zvolený generátor. Mezi podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteInstallRoot`: Určuje adresář ve vzdáleném počítači, ve kterém CMake generuje cíle instalace pro zvolený generátor. Mezi podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`a `${env.VARIABLE}`, kde `VARIABLE` je proměnná prostředí definovaná na úrovni systému, uživatele nebo relace.
- `remoteCopySources`: `boolean`, který určuje, zda má aplikace Visual Studio Kopírovat zdrojové soubory do vzdáleného počítače. Výchozí hodnota je true. Nastavte na hodnotu NEPRAVDA, pokud se synchronizace souborů spravuje sami.
- `remoteCopyBuildOutput`: `boolean`, který určuje, zda se mají kopírovat výstupy sestavení ze vzdáleného systému.
- `remoteCopyAdditionalIncludeDirectories`: další adresáře include, které se mají zkopírovat ze vzdáleného počítače, aby podporovaly technologii IntelliSense. Formátujte jako "/path1;/path2...".
- `remoteCopyExcludeDirectories`: zahrňte adresáře, které se nekopírují ze vzdáleného počítače. Formátujte jako "/path1;/path2...".
- `remoteCopyUseCompilerDefaults`: Určuje, zda se má použít výchozí definice kompilátoru a zahrnutí cest pro technologii IntelliSense. Hodnota by měla být false pouze v případě, že používané kompilátory nepodporují argumenty ve stylu RSZ.
- `rsyncCommandArgs`: Určuje sadu dalších možností příkazového řádku předaných do rsync.
- `remoteCopySourcesExclusionList`: `array`, který určuje seznam cest, které mají být vyloučeny při kopírování zdrojových souborů ': cesta může být název souboru nebo adresáře nebo cesta relativní ke kořenu kopie. Zástupné znaky \\\"*\\\" a \\\"?\\\" lze použít pro porovnávání vzorů glob.
- `cmakeExecutable`: Určuje úplnou cestu ke spustitelnému souboru programu CMake, včetně názvu souboru a přípony.
- `remotePreGenerateCommand`: Určuje příkaz, který se má spustit před spuštěním CMake k analýze souboru *CMakeLists. txt* .
- `remotePrebuildCommand`: Určuje příkaz, který se má spustit na vzdáleném počítači před sestavením.
- `remotePostbuildCommand`: Určuje příkaz, který se má spustit na vzdáleném počítači po sestavení.
- `variables`: obsahuje dvojici název-hodnota proměnných cmake, které se budou předávat **jako** *_název_=_hodnoty_* do cmake. Pokud vaše pokyny pro sestavení vašeho projektu CMake určují přidání jakýchkoli proměnných přímo do souboru *CMakeCache. txt* , doporučuje se místo toho přidat je sem. Následující příklad ukazuje, jak zadat páry název-hodnota pro sadu nástrojů 14.14.26428 MSVC:

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe",
      "type": "FILEPATH"
    }
  ]
```

Všimněte si, že pokud nedefinujete `"type"`, bude ve výchozím nastavení předpokládána typ `"STRING"`.
- `remoteCopyOptimizations`: vlastnosti sady **Visual Studio 2019 verze 16,5 nebo novější** pro řízení zdrojové kopie na vzdáleném cíli. Ve výchozím nastavení jsou povolené optimalizace. Zahrnuje `remoteCopyUseOptimizations`, `rsyncSingleDirectoryCommandArgs`a `remoteCopySourcesMaxSmallChange`.

## <a name="environments"></a>Environment

*Prostředí* zapouzdřuje proměnné prostředí, které jsou nastaveny v procesu, který aplikace Visual Studio používá k vyvolání cmake. exe. Pro projekty MSVC jsou proměnné, které jsou nastaveny v [příkazovém řádku vývojáře](building-on-the-command-line.md) pro konkrétní platformu. Například prostředí `msvc_x64_x64` je stejné jako spuštění **Developer Command Prompt pro vs 2017** nebo **Developer Command Prompt pro vs 2019** s argumenty **-arch = amd64-host_arch = amd64** . Pomocí syntaxe `env.{<variable_name>}` v *CMakeSettings. JSON* můžete odkazovat na jednotlivé proměnné prostředí, například pro vytváření cest ke složkám.  K dispozici jsou následující předdefinovaná prostředí:

- linux_arm: Zaměřte se na vzdálené Linux na platformě ARM.
- linux_x64: cílení na vzdálenou platformu x64 Linux.
- linux_x86: cílení na platformu x86 Linux vzdáleně.
- msvc_arm: cílová okna ARM s kompilátorem MSVC.
- msvc_arm_x64: cílová okna ARM s MSVC kompilátorem 64.
- msvc_arm64: cílová okna ARM64 s kompilátorem MSVC.
- msvc_arm64_x64: cílová okna ARM64 s MSVC kompilátorem 64.
- msvc_x64: cílová 64bitová okna s kompilátorem MSVC.
- msvc_x64_x64: cílení na 64bitové systémy Windows s MSVC kompilátorem 64.
- msvc_x86: cílová okna x86 s kompilátorem MSVC.
- msvc_x86_x64: cílová 32bitová okna s kompilátorem 64 MSVC.

### <a name="accessing-environment-variables-from-cmakeliststxt"></a>Přístup k proměnným prostředí z CMakeLists. txt

V souboru CMakeLists. txt se na všechny proměnné prostředí odkazuje syntaxí `$ENV{variable_name}`. Chcete-li zobrazit dostupné proměnné pro prostředí, otevřete odpovídající příkazový řádek a zadejte `SET`. Některé informace v proměnných prostředí jsou také k dispozici prostřednictvím proměnných introspekce systému CMak, ale může být vhodnější použít proměnnou prostředí. Například verze kompilátoru MSVC nebo verze Windows SDK lze snadno načíst prostřednictvím proměnných prostředí.

### <a name="custom-environment-variables"></a>Vlastní proměnné prostředí

V `CMakeSettings.json`můžete v poli `environments` definovat vlastní proměnné prostředí globálně nebo podle konfigurace. Vlastní prostředí je pohodlný způsob, jak seskupit sadu vlastností, které můžete použít místo předdefinovaného prostředí, nebo můžete zvětšit nebo upravit předdefinované prostředí. Každá položka v `environments`m poli se skládá z těchto položek:

- `namespace`: pojmenuje prostředí tak, aby na jeho proměnných bylo možné odkazovat z konfigurace ve formuláři `namespace.variable`. Výchozí objekt prostředí se nazývá `env` a je naplněn určitými proměnnými prostředí systému, včetně `%USERPROFILE%`.
- `environment`: jednoznačně identifikuje tuto skupinu proměnných. Povolí dědění skupiny později v položce `inheritEnvironments`.
- `groupPriority`: celé číslo, které určuje prioritu těchto proměnných při jejich vyhodnocování. Nejprve se vyhodnotí položky s vyšším počtem.
- `inheritEnvironments`: pole hodnot, které určují sadu prostředí děděných touto skupinou. Tato funkce umožňuje dědit výchozí prostředí a vytvořit vlastní proměnné prostředí, které se předávají do CMake. exe při spuštění. 

**Visual Studio 2019 verze 16,4 a novější:** Cíle ladění se automaticky spustí s prostředím, které zadáte v *CMakeSettings. JSON*. Můžete přepsat nebo přidat proměnné prostředí v závislosti na cíli nebo jednotlivých úkolech v [Launch. vs. JSON](launch-vs-schema-reference-cpp.md) a [Tasks. vs. JSON](tasks-vs-json-schema-reference-cpp.md).

Následující příklad definuje jednu globální proměnnou **builddir**, která je zděděna v konfiguraci x86-Debug i x64-Debug. Každá konfigurace používá proměnnou k určení hodnoty pro vlastnost **buildRoot** pro tuto konfiguraci. Všimněte si také, jak každá konfigurace používá vlastnost **inheritEnvironments** k určení proměnné, která se vztahuje pouze na tuto konfiguraci.

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x86 compiler.
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.BuildDir}\\${name}"    },
    {
      "name": "x64-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      // Inherit the defaults for using the MSVC x64 compiler.
      "inheritEnvironments": [ "msvc_x64" ],
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

V dalším příkladu konfigurace pro ladění x86 definuje svou vlastní hodnotu pro vlastnost **builddir** . Tato hodnota Přepisuje hodnotu nastavenou globální vlastností **builddir** tak, aby se **BuildRoot** vyhodnotila jako `D:\custom-builddir\x86-Debug`.

```json
{
  "environments": [
    {
      "BuildDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}",
    }
  ],

  "configurations": [
    {
      "name": "x86-Debug",

      // The syntax for this property is the same as the global one above.
      "environments": [
        {
          // Replace the global property entirely.
          "BuildDir": "D:\\custom-builddir"
          // This environment does not specify a namespace, hence by default "env" will be assumed.
          // "namespace" : "name" would require that this variable be referenced with "${name.BuildDir}".
        }
      ],

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      // Evaluates to "D:\custom-builddir\x86-Debug"
      "buildRoot": "${env.BuildDir}\\${name}"
    },
    {
      "name": "x64-Debug",

      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x64" ],
      // Since this configuration doesn't modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="macros"></a>Makra

V *CMakeSettings. JSON*lze použít následující makra:

- `${workspaceRoot}` – úplná cesta ke složce pracovního prostoru
- `${workspaceHash}` – hodnota hash umístění pracovního prostoru; užitečné pro vytvoření jedinečného identifikátoru pro aktuální pracovní prostor (například pro použití v cestách ke složkám).
- `${projectFile}` – úplná cesta k kořenovému souboru CMakeLists. txt
- `${projectDir}` – úplná cesta ke složce kořenového souboru CMakeLists. txt
- `${thisFile}` – úplná cesta k `CMakeSettings.json` souboru
- `${name}` – název konfigurace
- `${generator}` – název generátoru CMake použitého v této konfiguraci

Všechny odkazy na makra a proměnné prostředí v souboru *CMakeSettings. JSON* se rozbalí před předáním do příkazového řádku cmake. exe.

## <a name="ninja"></a>Argumenty příkazového řádku expertem

Pokud jsou cíle Nespecifikovány, aplikace vytvoří cíl default.

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Možnost|Popis|
|--------------|------------|
| --verze  | expertem verze tisku (1.7.1)|
|   -C DIR   | změnit na adresář před jakýmkoli jiným|
|   -f soubor  | zadat vstupní soubor sestavení (výchozí = Build. expertem)|
|   -j N     | spouštět úlohy N paralelně (výchozí = 14, odvozeno z dostupných CPU)|
|   -k N     | Pokračujte v práci, dokud N neselže úlohy (výchozí = 1).|
|   -l N     | Nespouštějte nové úlohy, pokud je průměr zatížení větší než N.|
|   -n       | suché spuštění (Nespouštět příkazy, ale funguje jako úspěšné)|
|   -v       | Zobrazit všechny příkazové řádky při sestavování|
|   -d – režim  | Povolit ladění (pro režimy seznamu použijte seznam-d)|
|   -t – Nástroj  | Spusťte dílčí nástroj (seznam použití-t k vypsání dílčích nástrojů). ukončí možnosti nejvyšší úrovně; k nástroji jsou předány další příznaky.|
|   -w – příznak  | upravit upozornění (pro výpis upozornění použijte seznam-w)|

::: moniker-end
