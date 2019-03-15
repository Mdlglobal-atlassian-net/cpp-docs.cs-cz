---
title: Referenční dokumentace schématu souboru CMakeSettings.json
ms.date: 03/05/2019
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: d80829b1475e8718e1c4188ff4fb7d42a1d4b3b9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823365"
---
# <a name="cmakesettingsjson-schema-reference"></a>Referenční dokumentace schématu souboru CMakeSettings.json

`cmakesettings.json` Soubor obsahuje informace o tom, jak by měl Visual Studio pracovat s CMake pro sestavení projektu pro zadanou platformu. Tento soubor můžete použijte k ukládání informací, jako jsou proměnné prostředí a argumenty pro cmake.exe prostředí.

## <a name="environments"></a>Prostředí

`environments` Pole obsahuje seznam `items` typu `object` která definuje "prostředí". Prostředí může použít pro sadu proměnných `configuration`. Každá položka v `environments` pole se skládá ze:

- `namespace`: názvy prostředí tak, aby své proměnné můžete odkazovat z konfigurace ve formě `namespace.variable`. Je volána výchozím prostředí objektu `env` a naplní se určité proměnné prostředí systému, včetně `%USERPROFILE%`.
- `environment`: jednoznačně identifikuje této skupiny proměnných. Umožňuje členům skupiny dědit později v `inheritEnvironments` položka.
- `groupPriority`: Celé číslo, které určuje priorita těchto proměnných při jejich vyhodnocování. Položky s vyššími čísly se vyhodnocují první.
- `inheritEnvironments`: Pole hodnot, které určují sadu prostředí, která jsou zděděna touto skupinou. Můžete použít libovolné vlastní prostředí nebo tato předdefinovaná prostředí:
 
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

  - Visual Studio 15 2017
  - Visual Studio 15 2017 Win64
  - Visual Studio 15 2017 ARM
  - Visual Studio 14 2015
  - Visual Studio 14 2015 Win64
  - Visual Studio 14 2015 ARM
  - UNIX soubory pravidel
  - Ninja

- `configurationType`: Určuje konfiguraci typu sestavení pro vybraný generátor. Může být jedna z:
 
  - Ladit
  - Vydaná verze
  - MinSizeRel
  - RelWithDebInfo
 
- `inheritEnvironments`: Určuje jedno nebo více prostředí, které tato konfigurace závisí. Může být libovolné vlastní prostředí nebo jeden z předdefinovaných prostředí.
- `buildRoot`: skripty specifiesThe adresář, ve kterém CMake generuje sestavení pro zvolený generátor. Podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`. "
- `installRoot`: Určuje adresář, ve kterém CMake generuje cíle instalace pro zvolený generátor. Podporovaná makra patří `${workspaceRoot}`, `${workspaceHash}`, `${projectFile}`, `${projectDir}`, `${thisFile}`, `${thisFileDir}`, `${name}`, `${generator}`, `${env.VARIABLE}`. "
- `cmakeCommandArgs`: Určuje další možnosti příkazového řádku předané do programu CMake při vyvolání ke generování mezipaměti. "
- `cmakeToolchain`: Určuje soubor sady nástrojů. To je předané do programu CMake pomocí - DCMAKE_TOOLCHAIN_FILE. "
- `buildCommandArgs`: Určuje přepínače nativního sestavení předané do programu CMake po--build--. "
- `ctestCommandArgs`: Určuje další možnosti příkazového řádku předané do programu CTest při spouštění testů. "
- `codeAnalysisRuleset`: Určuje sada pravidel k použití při spuštění analýzy kódu. To může být úplná cesta nebo název souboru sady pravidel nainstalované sadou Visual Studio."
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
- `variables`: A `array` , který určuje proměnné, které jsou předány do programu CMake jako - Dname1 = hodnota1-Dname2 = hodnota2 atd. 


