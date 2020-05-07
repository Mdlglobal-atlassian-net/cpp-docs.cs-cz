---
title: Odkaz na CppProperties. JSON
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: be6db52e1e62244e9f44db8ac86238242ab50ca0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328720"
---
# <a name="cpppropertiesjson-reference"></a>Odkaz na CppProperties. JSON

Projekty otevřené složky, které nepoužívají CMake, mohou ukládat nastavení konfigurace projektu pro technologii IntelliSense v souboru *CppProperties. JSON* . (Projekty CMake používají soubor [CMakeSettings. JSON](customize-cmake-settings.md) .) Konfigurace se skládá z dvojice název/hodnota a definuje #include cesty, přepínače kompilátoru a další parametry. Další informace o tom, jak přidat konfigurace v projektu otevřené složky, naleznete v tématu [Otevřít složku projekty pro C++](open-folder-projects-cpp.md) . V následujících částech najdete souhrn různých nastavení. Úplný popis schématu získáte tak, že přejdete na *CppProperties_schema. JSON*, jehož úplná cesta je uvedena v horní části editoru kódu, když je *CppProperties. JSON* otevřený.

## <a name="configuration-properties"></a>Vlastnosti konfigurace

Konfigurace může mít některou z následujících vlastností:

|||
|-|-|
|`inheritEnvironments`| Určuje, která prostředí se vztahují na tuto konfiguraci.|
|`name`|Název konfigurace, který se zobrazí v rozevíracím seznamu konfigurace C++|
|`includePath`|Seznam složek oddělených čárkami, které se mají zadat v cestě include (mapuje se na/I pro většinu kompilátorů)|
|`defines`|Seznam maker, která se mají definovat (mapuje na/D pro většinu kompilátorů)|
|`compilerSwitches`|Jeden nebo více dalších přepínačů, které mohou ovlivnit chování technologie IntelliSense|
|`forcedInclude`|Hlavička, která má být automaticky zahrnuta v každé kompilační jednotce (mapuje se na/FI pro MSVC nebo-include for Clang)|
|`undefines`|Seznam maker, která se mají nedefinovat (mapuje se na/U pro MSVC)|
|`intelliSenseMode`|Modul IntelliSense, který se má použít. Můžete zadat jednu z předdefinovaných variant specifických pro architekturu pro MSVC, RSZ nebo Clang.|
|`environments`|Uživatelsky definované sady proměnných, které se chovají jako proměnné prostředí v příkazovém řádku a jsou dostupné pomocí $ {env.\< Makro proměnné>}.|

### <a name="intellisensemode-values"></a>hodnoty režim intellisensemode

Editor kódu zobrazuje dostupné možnosti, když začnete psát:

![Otevřít složku IntelliSense](media/open-folder-intellisense-mode.png "Otevřít složku IntelliSense")

Podporovány jsou následující hodnoty:

- Windows – MSVC – x86
- Windows – MSVC – x64
- Windows – MSVC – ARM
- Windows – MSVC – arm64
- Android – Clang – x86
- Android – Clang – x64
- Android – Clang – ARM
- Android – Clang – arm64
- iOS – Clang – x86
- iOS – Clang – x64
- iOS – Clang – ARM
- iOS – Clang – arm64
- Windows – Clang – x86
- Windows – Clang – x64
- Windows – Clang – ARM
- Windows – Clang – arm64
- Linux – RSZ – x86
- Linux – RSZ – x64
- Linux – RSZ – ARM

Poznámka: hodnoty `msvc-x86` a `msvc-x64` jsou podporované jenom z původních důvodů. Místo toho `windows-msvc-*` použijte varianty.

## <a name="pre-defined-environments"></a>Předem definovaná prostředí

Visual Studio poskytuje následující předdefinovaná prostředí pro Microsoft C++, která se mapují na odpovídající Developer Command Prompt. Při dědění jednoho z těchto prostředí můžete odkazovat na libovolné proměnné prostředí pomocí globální vlastnosti `env` s touto syntaxí makra: $ {env.\< PROMĚNNÁ>}.

|Název proměnné|Popis|
|-----------|-----------------|
|vsdev|Výchozí prostředí sady Visual Studio|
|msvc_x86|Kompilovat pro x86 pomocí nástrojů x86|
|msvc_x64|Kompilovat pro AMD64 pomocí 64 bitových nástrojů|
|msvc_arm|Kompilovat pro ARM pomocí nástrojů x86|
|msvc_arm64|Kompilovat pro ARM64 pomocí nástrojů x86|
|msvc_x86_x64|Kompilovat pro AMD64 pomocí nástrojů x86|
|msvc_arm_x64|Kompilovat pro ARM pomocí 64 bitových nástrojů|
|msvc_arm64_x64|Kompilovat pro ARM64 pomocí 64 bitových nástrojů|

Po instalaci úlohy se systémem Linux jsou k dispozici následující prostředí pro vzdálenou cílení na systémy Linux a WSL:

|Název proměnné|Popis|
|-----------|-----------------|
|linux_x86|Vzdálené cílení na x86 Linux|
|linux_x64|Cílení na vzdálené x64 Linux|
|linux_arm|Vzdálené zacílení na platformu ARM Linux|

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a>Uživatelsky definovaná prostředí

Volitelně můžete použít `environments` vlastnost k definování sad proměnných v *CppProperties. JSON* buď globálně, nebo podle konfigurace. Tyto proměnné se chovají podobně jako proměnné prostředí v kontextu projektu otevřené složky a jsou k němu přistupované pomocí $ {env.\< Proměnná>} syntax z *Tasks. vs. JSON* a *Launch. vs. JSON* po jejich definování. Nicméně nejsou nutně nastaveny jako skutečné proměnné prostředí v jakémkoli příkazovém řádku, který aplikace Visual Studio používá interně.

**Visual Studio 2019 verze 16,4 a novější:** Proměnné specifické pro konfiguraci, které jsou definovány v souboru *CppProperties. JSON* , jsou automaticky vyzvednuty cíli ladění a úkoly `inheritEnvironments`bez nutnosti nastavování. Cíle ladění se spustí automaticky s prostředím, které zadáte v *CppProperties. JSON*.

**Visual Studio 2019 verze 16,3 a starší:** Když využijete prostředí, musíte ho zadat ve `inheritsEnvironments` vlastnosti i v případě, že je prostředí definované jako součást stejné konfigurace. `environment` vlastnost určuje název prostředí. Následující příklad ukazuje ukázkovou konfiguraci pro povolení IntelliSense pro RSZ v instalaci MSYS2. Všimněte si, jak konfigurace definuje a dědí `mingw_64` prostředí a jak má `includePath` vlastnost přístup k `INCLUDE` proměnné.

```json
"configurations": [
    {

      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath ,": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**",
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR};",
          "environment": "mingw_64"
        }
      ]
    }
  ]
```

Při definování vlastnosti **prostředí** v rámci konfigurace přepíše všechny globální proměnné se stejným názvem.

## <a name="built-in-macros"></a>Vestavěná makra

V *CppProperties. JSON*máte přístup k následujícím vestavěným makrům:

|||
|-|-|
|`${workspaceRoot}`| Úplná cesta ke složce pracovního prostoru|
|`${projectRoot}`| Úplná cesta ke složce, ve které je umístěn *CppProperties. JSON*|
|`${env.vsInstallDir}`| Úplná cesta ke složce, ve které je nainstalovaná spuštěná instance sady Visual Studio|

### <a name="example"></a>Příklad

Pokud má váš projekt složku zahrnutí a obsahuje také *Windows. h* a další běžné hlavičky z Windows SDK, může být vhodné aktualizovat konfigurační soubor *CppProperties. JSON* pomocí následujících součástí:

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\ucrt",
        "${env.NETFXSDKDir}\include\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\shared",
        "${env.VCToolsInstallDir}\include"
      ]
    }
  ]
}
```

> [!Note]
> `%WindowsSdkDir%`a `%VCToolsInstallDir%` nejsou nastaveny jako globální proměnné prostředí, takže se ujistěte, že spustíte devenv. exe z Developer Command Prompt, který definuje tyto proměnné. (Zadejte "Developer" v nabídce Windows Start.)

## <a name="troubleshoot-intellisense-errors"></a>Řešení chyb IntelliSense

Pokud se vám technologie IntelliSense, kterou**Text Editor** > **C/C++** > jste očekávali, nezobrazuje, můžete řešit problémy tak, že v **nabídce nástroje** > zvolíte**možnost** > **Upřesnit** a nastavení **Povolit protokolování** na **hodnotu true**. Pokud chcete začít, zkuste nastavit **úroveň protokolování** na 5 a **filtry protokolování** na 8.

![Protokolování diagnostiky](media/diagnostic-logging.png)

Výstup je připojen do **okno výstup** a zobrazí se, když vyberete možnost **Zobrazit výstup z: Visual C++ protokol**. Výstup obsahuje mimo jiné seznam skutečných cest, které IntelliSense pokouší použít. Pokud cesty se neshodují s těmi v *CppProperties. JSON*, zkuste zavřít složku a odstranit podsložku *. vs* , která obsahuje data procházení v mezipaměti.

Chcete-li vyřešit chyby technologie IntelliSense způsobené chybějícími cestami, otevřete **Seznam chyb** a filtrujte jeho výstup na "pouze IntelliSense" a kód chyby E1696 "nemůže otevřít zdrojový soubor...".
