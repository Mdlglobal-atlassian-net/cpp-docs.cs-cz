---
title: Odkaz na schéma CMakeSettings.json
ms.date: 11/22/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: f9c864b66df86165090b7d6d6fc9c4fc51d65a5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328884"
---
# <a name="cmakesettingsjson-schema-reference"></a>Odkaz na schéma CMakeSettings.json

::: moniker range="vs-2015"

Projekty CMake jsou podporovány v sadě Visual Studio 2017 a novější.

::: moniker-end

::: moniker range=">=vs-2017"

Soubor **CMakeSettings.json** obsahuje informace, které visual studio používá pro IntelliSense a vytvořit argumenty příkazového řádku, které předá cmake.exe pro zadané *konfigurace* a kompilátorprostředí . *environment* Konfigurace určuje vlastnosti, které platí pro konkrétní platformu `x86-Debug` a `Linux-Release`typ sestavení, například nebo . Každá konfigurace určuje prostředí, které zapouzdřuje informace o sadě nástrojů kompilátoru, například MSVC, GCC nebo Clang. CMake používá argumenty příkazového řádku k regeneraci kořenového souboru *CMakeCache.txt* a dalších souborů projektu pro projekt. Hodnoty lze přepsat v souborech *CMakeLists.txt.*

Konfigurace v rozhraní IDE můžete přidat nebo odebrat a pak je upravit přímo v souboru JSON nebo použít **editor Nastavení CMake** (Visual Studio 2019 a novější). Můžete snadno přepínat mezi konfiguracemi v ide generovat různé soubory projektu. Další informace [najdete v tématu Customize CMake build settings in Visual Studio.](customize-cmake-settings.md)

## <a name="configurations"></a>Konfigurace

Pole `configurations` obsahuje všechny konfigurace pro projekt CMake. Další informace o předdefinovaných konfiguracích naleznete v [tématu CMake předdefinovaný odkaz](cmake-predefined-configuration-reference.md) na konfiguraci. Do souboru můžete přidat libovolný počet předdefinovaných nebo vlastních konfigurací.

A `configuration` má tyto vlastnosti:

- `addressSanitizerEnabled`: `true` Pokud zkompiluje program s Address Sanitizer (Experimentální v systému Windows). Na Linuxu kompilujte s -fno-omit-frame-pointer a úrovní optimalizace kompilátoru -Os nebo -Oo pro dosažení nejlepších výsledků.
- `addressSanitizerRuntimeFlags`: runtime příznaky předány AddressSanitizer prostřednictvím proměnné prostředí ASAN_OPTIONS. Formát: flag1=value:flag2=value2.
- `buildCommandArgs`: Určuje nativní přepínače sestavení předané cmake po --build --. Například předávání -v při použití generátoru Ninja nutí Ninja k výstupu příkazových řádků. Další informace o příkazech Ninja naleznete v [argumentech příkazového řádku Ninja.](#ninja)
- `buildRoot`: určuje adresář, ve kterém CMake generuje skripty sestavení pro vybraný generátor.  Mapuje na **přepínač -DCMAKE_BINARY_DIR** a určuje, kde bude vytvořen *soubor CMakeCache.txt.* Pokud složka neexistuje, je vytvořena. Mezi podporovaná `${workspaceRoot}` `${workspaceHash}`makra `${thisFileDir}`patří `${name}` `${generator}`, `${env.VARIABLE}` `${projectFile}`, `${projectDir}`, `${thisFile}`, , , , .
- `cacheGenerationCommand`: určuje nástroj příkazového řádku a argumenty, například *ladění gencache.bat* pro generování mezipaměti. Příkaz je spuštěn z prostředí v zadaném prostředí pro konfiguraci, když uživatel explicitně požaduje regeneraci nebo je změněn soubor CMakeLists.txt nebo CMakeSettings.json.
- `cacheRoot`: určuje cestu k mezipaměti CMake. Tento adresář by měl obsahovat existující soubor *CMakeCache.txt.*
- `clangTidyChecks`: seznam varování oddělených čárkami, která budou předána clang-tidy; zástupné znaky jsou povoleny a předpona '-' odstraní kontroly.
- `cmakeCommandArgs`: Určuje další možnosti příkazového řádku předané cMake při vyvolání ke generování souborů projektu.
- `cmakeToolchain`: určuje soubor řetězce nástrojů. To je předánc CMake pomocí -DCMAKE_TOOLCHAIN_FILE."
- `codeAnalysisRuleset`: Určuje sadu pravidel, která se má použít při spuštění analýzy kódu. Může se jedná o úplnou cestu nebo název souboru sady pravidel nainstalovaného aplikací Visual Studio.
- `configurationType`: Určuje konfiguraci typu sestavení pro vybraný generátor. Může být jedním z:

  - Ladit
  - Vydat
  - MinSizeRel
  - RelWithDebInfo
  
- `ctestCommandArgs`: Určuje další možnosti příkazového řádku předané CTest při spuštění testů."
- `description`: popis této konfigurace, která se zobrazí v nabídkách.
- `enableClangTidyCodeAnalysis`: Pro analýzu kódu použijte Clang-Tidy.
- `enableMicrosoftCodeAnalysis`: Pro analýzu kódu použijte nástroje pro analýzu kódu společnosti Microsoft.
- `generator`: určuje generátor CMake, který se má použít pro tuto konfiguraci. Může být jedním z:
  
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
  - Unix Makefiles
  - Ninja

Vzhledem k tomu, že Ninja je navržen pro rychlé rychlosti sestavení namísto flexibility a funkce, je nastaven jako výchozí. Některé projekty CMake však nemusí být schopen správně sestavit pomocí Ninja. Pokud k tomu dojde, můžete pokyn CMake generovat projekty sady Visual Studio místo.

Chcete-li v sadě Visual Studio 2017 zadat generátor sady Visual Studio, otevřete hlavní nabídku výběrem **možnosti CMake | Změnit nastavení CMake**. Odstraňte "Ninja" a zadejte "V". Tím se aktivuje technologie IntelliSense, která vám umožní vybrat si požadovaný generátor.

Chcete-li v sadě Visual Studio 2019 určit generátor sady Visual Studio, klepněte pravým tlačítkem myši na soubor *CMakeLists.txt* v **Průzkumníku řešení** a zvolte **Nastavení CMake pro projekt** > **Zobrazit generátor cmake pokročilých nastavení** > **CMake Generator**.

Pokud aktivní konfigurace určuje generátor sady Visual Studio, je ve výchozím `-m -v:minimal` nastavení msbuild.exe vyvolán s argumenty. Chcete-li přizpůsobit sestavení, můžete v souboru *CMakeSettings.json* zadat další [argumenty příkazového řádku MSBuild,](../build/reference/msbuild-visual-cpp-overview.md) které mají být předány systému sestavení prostřednictvím vlastnosti: `buildCommandArgs`

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `installRoot`: určuje adresář, ve kterém CMake generuje cíle instalace pro vybraný generátor. Mezi podporovaná `${workspaceRoot}` `${workspaceHash}`makra `${thisFileDir}`patří `${name}` `${generator}`, `${env.VARIABLE}` `${projectFile}`, `${projectDir}`, `${thisFile}`, , , , .
- `inheritEnvironments`: Určuje jedno nebo více prostředí kompilátoru, na kterých závisí tato konfigurace. Může být libovolné vlastní prostředí nebo jedno z předdefinovaných prostředí. Další informace naleznete v [tématu Prostředí](#environments).
- `intelliSenseMode`: určuje režim používaný pro výpočet informací intellisense". Může být jedním z:

  - windows-msvc-x86
  - windows-msvc-x64
  - windows-msvc-rameno
  - windows-msvc-arm64
  - android-clang-x86
  - android-clang-x64
  - android-clang-paže
  - android-clang-arm64
  - ios-clang-x86
  - ios-clang-x64
  - ios-clang-rameno
  - ios-clang-arm64
  - okna-clang-x86
  - okna-clang-x64
  - okna-clang-rameno
  - okna-clang-arm64
  - linux-gcc-x86
  - linux-gcc-x64
  - linux-gcc-paže"

- `name`: pojmenuje konfiguraci.  Další informace o předdefinovaných konfiguracích naleznete v [tématu CMake předdefinovaný odkaz](cmake-predefined-configuration-reference.md) na konfiguraci.
- `wslPath`: cesta ke spouštěči instance podsystému Windows pro Linux.

### <a name="additional-settings-for-cmake-linux-projects"></a>Další nastavení pro projekty CMake Linux

- `remoteMachineName`: určuje název vzdáleného počítače s Linuxem, který je hostitelem CMake, sestavení a ladicího programu. Pro přidání nových počítačů s Linuxem použijte Správce připojení. Mezi podporovaná `${defaultRemoteMachineName}`makra patří .
- `remoteCopySourcesOutputVerbosity`: Určuje úroveň podrobností operace zdrojového kopírování do vzdáleného počítače. Může být jedním z ""Normální", "Verbose", nebo "Diagnostika".
- `remoteCopySourcesConcurrentCopies`: Určuje počet souběžných kopií použitých při synchronizaci zdrojů se vzdáleným počítačem (pouze sftp).
- `remoteCopySourcesMethod`: Určuje způsob kopírování souborů do vzdáleného počítače. Může být "rsync" nebo "sftp".
- `remoteCMakeListsRoot`: Určuje adresář ve vzdáleném počítači, který obsahuje projekt CMake. Mezi podporovaná `${workspaceRoot}` `${workspaceHash}`makra `${thisFileDir}`patří `${name}` `${generator}`, `${env.VARIABLE}` `${projectFile}`, `${projectDir}`, `${thisFile}`, , , , .
- `remoteBuildRoot`: Určuje adresář na vzdáleném počítači, ve kterém CMake generuje skripty sestavení pro vybraný generátor. Mezi podporovaná `${workspaceRoot}` `${workspaceHash}`makra `${thisFileDir}`patří `${name}` `${generator}`, `${env.VARIABLE}` `${projectFile}`, `${projectDir}`, `${thisFile}`, , , , .
- `remoteInstallRoot`: Určuje adresář na vzdáleném počítači, ve kterém CMake generuje cíle instalace pro vybraný generátor. Podporovaná makra `${projectFile}` `${projectDir}`zahrnují `${thisFile}` `${workspaceRoot}` `${workspaceHash}`, `${generator}`, `${env.VARIABLE}` , `VARIABLE` `${thisFileDir}`, `${name}`, , a kde je proměnná prostředí, která byla definována na úrovni systému, uživatele nebo relace.
- `remoteCopySources`: `boolean` A, který určuje, zda má visual studio kopírovat zdrojové soubory do vzdáleného počítače. Výchozí hodnota je true. Pokud synchronizaci souborů spravujete sami, nastavte na hodnotu false.
- `remoteCopyBuildOutput`: `boolean` A, který určuje, zda se mají zkopírovat výstupy sestavení ze vzdáleného systému.
- `remoteCopyAdditionalIncludeDirectories`: Další zahrnují adresáře, které mají být zkopírovány ze vzdáleného počítače pro podporu technologie IntelliSense. Formátovat jako "/path1;/path2...".
- `remoteCopyExcludeDirectories`: Zahrnout adresáře, které nelze kopírovat ze vzdáleného počítače. Formátovat jako "/path1;/path2...".
- `remoteCopyUseCompilerDefaults`: Určuje, zda se má použít výchozí hodnota kompilátoru definuje a zahrnuje cesty pro technologie IntelliSense. By měla být pouze false, pokud kompilátory v použití nepodporují gcc-style argumenty.
- `rsyncCommandArgs`: Určuje sadu dalších možností příkazového řádku předaných rsync.
- `remoteCopySourcesExclusionList`: `array` A, který určuje seznam cest, které mají být vyloučeny při kopírování zdrojových souborů:cesta může být název souboru/adresáře nebo cesta vzhledem ke kořenovému adresáři kopie. Zástupné \\ \" * \\ \" \\ \"znaky a ? \\ lze použít pro glob vzor \" odpovídající.
- `cmakeExecutable`: Určuje úplnou cestu ke spustitelnému souboru programu CMake, včetně názvu souboru a přípony.
- `remotePreGenerateCommand`: Určuje příkaz, který má být spuštěn před spuštěním souboru CMakePro, aby byl analyzován soubor *CMakeLists.txt.*
- `remotePrebuildCommand`: Určuje příkaz, který má být spuštěn na vzdáleném počítači před sestavením.
- `remotePostbuildCommand`: Určuje příkaz, který má být spuštěn na vzdáleném počítači po sestavení.
- `variables`: obsahuje dvojici název-hodnota CMake proměnné, které budou předány jako **-D** * _název_=hodnoty* CMake. Pokud vaše CMake projektu sestavení pokyny určit přidání všech proměnných přímo do souboru *CMakeCache.txt,* je doporučeno přidat je zde místo. Následující příklad ukazuje, jak zadat dvojice název-hodnota pro sadu nástrojů 14.14.26428 MSVC:

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

Všimněte si, že `"type"`pokud `"STRING"` nedefinujete , bude typ předpokládá ve výchozím nastavení.

- `remoteCopyOptimizations`: **Visual Studio 2019 verze 16.5 nebo novější** vlastnosti pro řízení zdrojové kopie vzdáleného cíle. Optimalizace jsou ve výchozím nastavení povoleny. Zahrnuje `remoteCopyUseOptimizations` `rsyncSingleDirectoryCommandArgs`, `remoteCopySourcesMaxSmallChange`, a .

## <a name="environments"></a><a name="environments"></a>Prostředí

*Prostředí* zapouzdřuje proměnné prostředí, které jsou nastaveny v procesu, který Visual Studio používá k vyvolání cmake.exe. Pro projekty MSVC jsou proměnné ty, které jsou nastaveny v [příkazovém řádku pro vývojáře](building-on-the-command-line.md) pro konkrétní platformu. `msvc_x64_x64` Například prostředí je stejné jako spuštění **příkazového řádku pro vývojáře pro VS 2017** nebo **Příkazový řádek pro vývojáře pro VS 2019** s argumenty **-arch=amd64 -host_arch=amd64.** Syntaxi souboru `env.{<variable_name>}` *CMakeSettings.json* můžete použít k odkazování na jednotlivé proměnné prostředí, například k vytvoření cest ke složkám.  K dispozici jsou následující předdefinovaná prostředí:

- linux_arm: Cíl ARM Linux na dálku.
- linux_x64: Cíl x64 Linux na dálku.
- linux_x86: Cíl x86 Linux na dálku.
- msvc_arm: Cílarm Windows s kompilátorem MSVC.
- msvc_arm_x64: Cílarm Windows s 64bitovým kompilátorem MSVC.
- msvc_arm64: CílARM64 Windows s kompilátorem MSVC.
- msvc_arm64_x64: CílARM64 Windows s 64bitovým kompilátorem MSVC.
- msvc_x64: Zacilte na systém x64 Windows s kompilátorem MSVC.
- msvc_x64_x64: Zacilte na x64 Windows s 64bitovým kompilátorem MSVC.
- msvc_x86: Cílte na x86 Windows s kompilátorem MSVC.
- msvc_x86_x64: Zacilte na x86 Windows s 64bitovým kompilátorem MSVC.

### <a name="accessing-environment-variables-from-cmakeliststxt"></a>Přístup k proměnným prostředí z souboru CMakeLists.txt

Ze souboru CMakeLists.txt jsou všechny proměnné prostředí `$ENV{variable_name}`odkazovány syntaxí . Chcete-li zobrazit dostupné proměnné pro prostředí, otevřete `SET`odpovídající příkazový řádek a zadejte . Některé informace v proměnných prostředí je také k dispozici prostřednictvím cmake systému introspekce proměnných, ale může být vhodnější použít proměnné prostředí. Například verze kompilátoru MSVC nebo verze sady Windows SDK jsou snadno načteny prostřednictvím proměnných prostředí.

### <a name="custom-environment-variables"></a>Proměnné vlastního prostředí

V `CMakeSettings.json`programu můžete definovat proměnné vlastního prostředí globálně nebo `environments` podle konfigurace v poli. Vlastní prostředí je pohodlný způsob, jak seskupit sadu vlastností, které můžete použít místo předdefinovaného prostředí, nebo rozšířit nebo upravit předdefinované prostředí. Každá položka `environments` v poli se skládá z:

- `namespace`: pojmenuje prostředí tak, aby jeho proměnné mohly `namespace.variable`být odkazovány z konfigurace ve formuláři . Výchozí objekt prostředí `env` je volán a je naplněn `%USERPROFILE%`určitými proměnnými systémového prostředí včetně .
- `environment`: jednoznačně identifikuje tuto skupinu proměnných. Umožňuje, aby byla skupina zděděna později v položce. `inheritEnvironments`
- `groupPriority`: Celé číslo, které určuje prioritu těchto proměnných při jejich vyhodnocení. Vyšší počet položek jsou vyhodnoceny jako první.
- `inheritEnvironments`: Pole hodnot, které určují sadu prostředí, které jsou zděděny touto skupinou. Tato funkce umožňuje dědit výchozí prostředí a vytvářet vlastní proměnné prostředí, které jsou při spuštění předány cmake.exe.

**Visual Studio 2019 verze 16.4 a novější:** Ladění cílů jsou automaticky spuštěny s prostředím, které zadáte v *CMakeSettings.json*. Proměnné prostředí můžete přepsat nebo přidat na základě cíle nebo na úkol v [launch.vs.json](launch-vs-schema-reference-cpp.md) a [tasks.vs.json](tasks-vs-json-schema-reference-cpp.md).

Následující příklad definuje jednu globální proměnnou **BuildDir**, která je zděděna v konfiguracích x86-Debug a x64-Debug. Každá konfigurace používá proměnnou k určení hodnoty vlastnosti **buildRoot** pro danou konfiguraci. Všimněte si také, jak každá konfigurace používá **vlastnost inheritEnvironments** k určení proměnné, která se vztahuje pouze na tuto konfiguraci.

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

V dalším příkladu konfigurace x86-Debug definuje vlastní hodnotu pro vlastnost **BuildDir.** Tato hodnota přepíše hodnotu nastavenou globální vlastností **BuildDir** tak, aby **buildroot** vyhodnocuje na `D:\custom-builddir\x86-Debug`.

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

Následující makra lze použít v *souboru CMakeSettings.json*:

- `${workspaceRoot}`– úplná cesta ke složce pracovního prostoru
- `${workspaceHash}`– hash umístění pracovního prostoru; užitečné pro vytvoření jedinečného identifikátoru pro aktuální pracovní prostor (například pro použití v cestách složek)
- `${projectFile}`– úplná cesta kořenového souboru CMakeLists.txt
- `${projectDir}`– úplná cesta ke složce kořenového souboru CMakeLists.txt
- `${thisFile}`– úplná cesta `CMakeSettings.json` k souboru
- `${name}`– název konfigurace
- `${generator}`– název generátoru CMake použitého v této konfiguraci

Všechny odkazy na makra a proměnné prostředí v *souboru CMakeSettings.json* jsou před předáním do příkazového řádku cmake.exe rozbaleny.

## <a name="ninja-command-line-arguments"></a><a name="ninja"></a>Argumenty příkazového řádku Ninja

Pokud cíle nejsou určeny, vytvoří cíl 'default'.

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Možnost|Popis|
|--------------|------------|
| --verze  | tisk ninja verze ("1.7.1")|
|   -C DIR   | změna na DIR předtím, než dělat něco jiného|
|   -f SOUBOR  | zadejte vstupní soubor sestavení (default=build.ninja)|
|   -j N     | spustit n úlohy paralelně (default=14, odvozený z procesorů k dispozici)|
|   -k N     | pokračovat, dokud n úlohy nezdaří (default=1)|
|   -l N     | nezahajujte nové úlohy, pokud je průměr zatížení větší než N|
|   -n       | suchý běh (nespouštějte příkazy, ale jednat, jako by se podařilo)|
|   -v       | zobrazit všechny příkazové řádky při vytváření|
|   -d REŽIM  | povolit ladění (použití seznamu -d do režimů seznamu)|
|   -t NÁSTROJ  | spusťte podnástroj (použijte -t seznam podnástrojů). ukončí možnosti nejvyšší úrovně; další vlajky jsou předány nástroji|
|   -w VLAJKA  | upravit upozornění (použití -w seznam na seznam upozornění)|

::: moniker-end
