---
title: Referenční dokumentace schématu souboru CMakeSettings.json
ms.date: 05/16/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 018a755aa4f3acde44fe1dbb33b07b49c8d1c223
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837258"
---
# <a name="cmakesettingsjson-schema-reference"></a>Referenční dokumentace schématu souboru CMakeSettings.json

**Cmakesettings.json**' soubor obsahuje informace o tom, jak by měl Visual Studio pracovat s CMake pro sestavení projektu pro zadanou platformu. Soubor ukládá informace, jako jsou proměnné prostředí nebo argumenty pro cmake.exe prostředí. Můžete upravit přímo, nebo použít **editor nastavení CMake** (Visual Studio 2019 a novější). Zobrazit [nastavení v sadě Visual Studio sestavení přizpůsobit CMake](customize-cmake-settings.md) Další informace o editoru.

## <a name="environments"></a>Prostředí

`environments` Pole obsahuje seznam `items` typu `object` která definuje sadu nástrojů kompilátoru "prostředí". Prostředí může použít pro sadu proměnných `configuration`. Každá položka v `environments` pole se skládá ze:

- `namespace`: názvy prostředí tak, aby své proměnné můžete odkazovat z konfigurace ve formě `namespace.variable`. Je volána výchozím prostředí objektu `env` a naplní se určité proměnné prostředí systému, včetně `%USERPROFILE%`.
- `environment`: jednoznačně identifikuje této skupiny proměnných. Umožňuje členům skupiny dědit později v `inheritEnvironments` položka.
- `groupPriority`: Celé číslo, které určuje priorita těchto proměnných při jejich vyhodnocování. Položky s vyššími čísly se vyhodnocují první.
- `inheritEnvironments`: Pole hodnot, které určují sadu prostředí, která jsou zděděna touto skupinou. Tato funkce umožňuje dědit výchozí prostředí a vytvořit vlastní proměnné prostředí, které se předá CMake.exe při spuštění.

   ```json
   "inheritEnvironments": [ "msvc_x64_x64" ]
   ```

   Výše uvedený příklad je stejný jako spuštění **Developer Command Prompt for VS 2017** nebo **Developer Command Prompt for VS 2019** s **-arch = amd64 – host_arch = amd64** argumenty. Můžete použít libovolné vlastní prostředí nebo tato předdefinovaná prostředí:
 
  - linux_arm: Jako cíl ARM Linux vzdáleně.
  - linux_x64: Cíl x64 Linux vzdáleně.
  - linux_x86: Cíl x86 Linux vzdáleně.
  - msvc_arm: Cíl Windows ARM s kompilátorem MSVC.
  - msvc_arm_x64: Cíl Windows ARM s 64bitovým kompilátorem MSVC.
  - msvc_arm64: Cíl ARM64 Windows s kompilátorem MSVC.
  - msvc_arm64_x64: Cíl ARM64 Windows s 64bitovým kompilátorem MSVC.
  - msvc_x64: Cíl x64 Windows s kompilátorem MSVC.
  - msvc_x64_x64: Cíl x64 Windows s 64bitovým kompilátorem MSVC.
  - msvc_x86: Cíl x86 Windows s kompilátorem MSVC.
  - msvc_x86_x64: Cíl x86 Windows s 64bitovým kompilátorem MSVC.

## <a name="configurations"></a>Konfigurace

`configurations` Pole se skládá z objektů, které představují konfigurací CMake, které platí pro soubor CMakeLists.txt ve stejné složce. Tyto objekty můžete použít k definování několika konfiguracích sestavení a snadno přepínat mezi nimi v integrovaném vývojovém prostředí. 

A `configuration` má tyto vlastnosti:
- `name`: název konfigurace.
- `description`: popis této konfigurace, který se zobrazí v nabídkách.
- `generator`: Určuje generátoru CMake pro tuto konfiguraci. Může být jedna z:
  
  **Visual Studio. 2019 pouze:**
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
  - UNIX soubory pravidel
  - Ninja

Protože Ninja je určená pro rychlé sestavení rychlosti místo flexibilitu a funkce, je nastavit jako výchozí. Některé projekty CMake, ale možná nebudete moct správně programujte Ninja. Pokud k tomu dojde, můžete dát pokyn CMake pro generování projektu sady Visual Studio místo.

Chcete-li zadat generátoru Visual Studio v sadě Visual Studio 2017, otevřete `CMakeSettings.json` v hlavní nabídce výběrem **CMake | Změnit nastavení CMake**. Odstraňte "Ninja" a zadejte "V". Tím se aktivuje technologii IntelliSense, která vám umožní vybrat generátor, který chcete.

Zadejte v aplikaci Visual Studio 2019 generátoru Visual Studio, klikněte pravým tlačítkem na soubor CMakeLists.txt v **Průzkumníka řešení** a zvolte **nastavení CMake pro projekt** > **zobrazit Upřesňující nastavení** > **generátoru CMake**.

Pokud aktivní konfigurace určuje generátoru Visual Studio, ve výchozím nastavení je MSBuild.exe volána s `-m -v:minimal` argumenty. Přizpůsobení sestavení, uvnitř `CMakeSettings.json` souboru, můžete zadat další [argumenty příkazového řádku MSBuild](../build/reference/msbuild-visual-cpp-overview.md) mají být předány prostřednictvím systému sestavení `buildCommandArgs` vlastnost:

   ```json
   "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
   ```

- `configurationType`: Určuje konfiguraci typu sestavení pro vybraný generátor. Může být jedna z:
 
  - Ladění
  - Vydaná verze
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`: Určuje jedno nebo více prostředí kompilátoru, tato konfigurace, na kterých závisí. Může být libovolné vlastní prostředí nebo jeden z předdefinovaných prostředí.
- `buildRoot`: Určuje adresář, ve kterém CMake generuje skripty sestavení pro zvolený generátor.  Mapuje **-DCMAKE_BINARY_DIR** přepnutí a určuje, kde se vytvoří mezipaměť CMake. Pokud složka neexistuje, vytvoří se. Podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `installRoot`: Určuje adresář, ve kterém CMake generuje cíle instalace pro zvolený generátor. Podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `cmakeCommandArgs`: Určuje další možnosti příkazového řádku předané do programu CMake při vyvolání ke generování mezipaměti.
- `cmakeToolchain`: Určuje soubor sady nástrojů. To je předané do programu CMake pomocí - DCMAKE_TOOLCHAIN_FILE. "
- `buildCommandArgs`: Určuje přepínače nativního sestavení předané do programu CMake po--build--. Například předávání - v, při použití generátor Ninja vynutí Ninja výstup příkazové řádky. Zobrazit [argumenty příkazového řádku Ninja](#ninja) Další informace o příkazech Ninja.
- `ctestCommandArgs`: Určuje další možnosti příkazového řádku předané do programu CTest při spouštění testů. "
- `codeAnalysisRuleset`: Určuje sada pravidel k použití při spuštění analýzy kódu. Může jít úplnou cestu nebo název souboru sady pravidel nainstalované sadou Visual Studio.
- `intelliSenseMode`: Určuje režim používaný pro výpočet informací technologie intellisense ". Může být jedna z:
 
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
  - ios-clang-arm
  - ios-clang-arm64
  - windows-clang-x86
  - windows-clang-x64
  - windows-clang-arm
  - windows-clang-arm64
  - linux-gcc-x86
  - linux-gcc-x64
  - linux-gcc-arm"

- `cacheRoot`: Určuje cestu k mezipaměti CMake. Tento adresář by měl obsahovat existující soubor CMakeCache.txt.

### <a name="additional-settings-for-cmake-linux-projects"></a>Další nastavení pro CMake Linuxové projekty. 

- `remoteMachineName`: Určuje název vzdáleného počítače s Linuxem, který je hostitelem CMake, sestavení a ladicí program. Pro přidání nového počítače s Linuxem použijte Connection Manager. Podporovaná makra patří `${defaultRemoteMachineName}`.
- `remoteCopySourcesOutputVerbosity`: Určuje úroveň podrobností operace kopírování zdroje do vzdáleného počítače. Může být jedna z "" normální","Verbose"nebo"Diagnostických".
- `remoteCopySourcesConcurrentCopies`: Určuje, kolik souběžných kopie používá během synchronizace zdroje do vzdáleného počítače.
- `remoteCopySourcesMethod`: Určuje metodu kopírování souborů do vzdáleného počítače. Může být "rsync" nebo "sftp".
- `remoteCMakeListsRoot`: Určuje adresář ve vzdáleném počítači, který obsahuje projekt CMake. Podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteBuildRoot`: Určuje adresář ve vzdáleném počítači, ve kterém CMake generuje skripty sestavení pro zvolený generátor. Podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`.
- `remoteInstallRoot`: Určuje adresář ve vzdáleném počítači, ve kterém CMake generuje cíle instalace pro zvolený generátor. Podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, a `${env.VARIABLE}` kde `VARIABLE` je proměnná prostředí, který má byly definovány na úrovni systému, uživatele nebo relace.
- `remoteCopySources`: A `boolean` , která určuje, zda sady Visual Studio by měl kopírovat zdrojové soubory do vzdáleného počítače. Výchozí hodnota je true. Nastavte na hodnotu false, pokud synchronizaci souborů spravujete sami.
- `remoteCopyBuildOutput`: A `boolean` , která určuje, jestli se má kopírovat výstupy sestavení ze vzdáleného systému.
- `rsyncCommandArgs`: Určuje další možnosti příkazového řádku předaná pro příkaz rsync sadu.
- `remoteCopySourcesExclusionList`: A `array` , která určuje seznam cest, které se mají vyloučit při kopírování zdrojových souborů: cesta může být název souboru/adresáře nebo cesta relativní vůči kořenovému kopie adresáři. Zástupné znaky \\ \" * \\ \" a \\ \"?\\ \" lze použít pro glob porovnávání vzorů.
- `cmakeExecutable`: Určuje úplnou cestu ke spustitelnému souboru programu CMake, včetně názvu souboru a přípony.
- `remotePreGenerateCommand`: Určuje příkaz pro spuštění před spuštěním CMake za účelem parsování souboru CMakeLists.txt.
- `remotePrebuildCommand`: Určuje příkaz pro spuštění na vzdáleném počítači před sestavením.
- `remotePostbuildCommand`: Určuje příkaz pro spuštění na vzdáleném počítači po sestavení.
- `variables`: obsahuje dvojice název hodnota proměnné CMake, které budou získat předány jako **-D** *_název_=_hodnotu_* do programu CMake. Pokyny k sestavení projektu CMake zadání přidání všech proměnných přímo do souboru mezipaměti CMake, se doporučuje jste je přidali tady místo. Následující příklad ukazuje, jak určit dvojice název hodnota pro 14.14.26428 MSVC sady nástrojů:

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

Poznámka: Pokud není definován `"type"`, předpokládá se typ "Řetězec" ve výchozím nastavení.

## <a name="environment-variables"></a>Proměnné prostředí

`CMakeSettings.json` také podporuje používání proměnných prostředí v některém z jeho vlastností uvedených výše. Syntaxe pro použití `${env.FOO}` rozšíření prostředí % variable % FOO.

Máte také přístup k předdefinované makra v tomto souboru:

- `${workspaceRoot}` – poskytuje úplnou cestu složky pracovního prostoru
- `${workspaceHash}` – Hodnota hash umístění pracovního prostoru. užitečné pro vytváření jedinečný identifikátor pro aktuální pracovní prostor (například pro použití v cesty ke složkám)
- `${projectFile}` – Úplná cesta kořenového souboru CMakeLists.txt
- `${projectDir}` – Úplná cesta ke složce kořenového souboru CMakeLists.txt
- `${thisFile}` – Úplná cesta `CMakeSettings.json` souboru
- `${name}` – Název konfigurace
- `${generator}` – Název generátoru CMake použít v této konfiguraci


### <a name="custom-environment-variables"></a>Vlastní proměnné prostředí

V `CMakeSettings.json`, můžete definovat vlastní proměnné prostředí globálně nebo podle konfigurace v **prostředí** vlastnost. Následující příklad definuje jeden globální proměnné, **BuildDir**, dědí se v konfiguracích ladění x86 i x64 ladění. Každá konfigurace používá zadat hodnotu pro proměnnou **buildRoot** vlastnosti pro tuto konfiguraci. Všimněte si také, jak jednotlivé konfigurace používá **inheritEnvironments** vlastnosti a určit proměnnou, která se vztahuje pouze na tuto konfiguraci.

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

V následujícím příkladu definuje konfiguraci ladění x86 jeho vlastní hodnotě. pro **BuildDir** vlastnost. Tato hodnota přepíše hodnoty nastavené v globální **BuildDir** vlastnost tak, aby **BuildRoot** vyhodnotí jako `D:\custom-builddir\x86-Debug`.

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
      // Since this configuration doesn’t modify BuildDir, it inherits
      // from the one defined globally.
      "buildRoot": "${env.BuildDir}\\${name}"
    }
  ]
}
```

## <a name="ninja"></a> Argumenty příkazového řádku ninja

Pokud nejsou specifikována cíle, vytvoří cíl "default".

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Možnost|Popis|
|--------------|------------|
| – verze  | vytisknout verzi ninja ("1.7.1")|
|   -C DIR   | změňte na adresář před provedením další akce|
|   -f souboru  | Zadejte soubor vstupní sestavení (default=build.ninja)|
|   -j N     | spouštění úloh N paralelně (výchozí = 14, odvozený z procesorů, které jsou k dispozici)|
|   -k N     | pokračujte dál, dokud N úloh selže (výchozí = 1)|
|   -l N     | nelze spustit nové úlohy, pokud je průměrné zatížení větší než N|
|   -n       | suší spuštění (nemusíte spouštět příkazy, ale fungovala tak, jako jsou proběhlo úspěšně)|
|   -v       | Zobrazit všechny příkazových řádků během sestavování|
|   -d režimu  | povolte ladění (použití -d režimy seznamu)|
|   t – nástroj  | Spusťte subtool (použijte -t seznamu podřízených nástrojích). Ukončí nejvyšší úrovně možnosti; Další příznaky jsou předány do nástroje|
|   -w příznak  | Upravte upozornění (použijte -w seznamu upozornění)|




