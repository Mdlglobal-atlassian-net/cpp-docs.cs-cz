---
title: Odkaz na CppProperties. JSON
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: d59fca412a26d08f88ccbda20a2c0444cf33b1cb
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856810"
---
# <a name="cpppropertiesjson-reference"></a>Odkaz na CppProperties. JSON

Projekty otevřené složky, které nepoužívají CMake, mohou ukládat nastavení konfigurace projektu pro technologii IntelliSense v souboru *CppProperties. JSON* . (Projekty CMake používají soubor [CMakeSettings. JSON](customize-cmake-settings.md) .) Konfigurace se skládá z dvojice název/hodnota a definuje #include cesty, přepínače kompilátoru a další parametry. Další informace o tom, jak přidat konfigurace v projektu otevřené složky, najdete v tématu [Otevřít složku projekty C++ ](open-folder-projects-cpp.md) . V následujících částech najdete souhrn různých nastavení. Úplný popis schématu získáte tak, že přejdete na *CppProperties_schema. JSON*, jehož úplná cesta je uvedena v horní části editoru kódu, když je *CppProperties. JSON* otevřený.

## <a name="configuration-properties"></a>Vlastnosti konfigurace

Konfigurace může mít některou z následujících vlastností:

|||
|-|-|
|`inheritEnvironments`| Určuje, která prostředí se vztahují na tuto konfiguraci.|
|`name`|Název konfigurace, který se zobrazí v rozevírací C++ nabídce konfigurace|
|`includePath`|Seznam složek oddělených čárkami, které se mají zadat v cestě include (mapuje se na/I pro většinu kompilátorů)|
|`defines`|Seznam maker, která se mají definovat (mapuje na/D pro většinu kompilátorů)|
|`compilerSwitches`|Jeden nebo více dalších přepínačů, které mohou ovlivnit chování technologie IntelliSense|
|`forcedInclude`|Hlavička, která má být automaticky zahrnuta v každé kompilační jednotce (mapuje se na/FI pro MSVC nebo-include for Clang)|
|`undefines`|Seznam maker, která se mají nedefinovat (mapuje se na/U pro MSVC)|
|`intelliSenseMode`|Modul IntelliSense, který se má použít. Můžete zadat jednu z předdefinovaných variant specifických pro architekturu pro MSVC, RSZ nebo Clang.|
|`environments`|Uživatelsky definované sady proměnných, které se chovají jako proměnné prostředí v příkazovém řádku a jsou dostupné pomocí $ {env.<VARIABLE>} podokně.|

### <a name="intellisensemode-values"></a>hodnoty režim intellisensemode

Editor kódu zobrazuje dostupné možnosti, když začnete psát:

![Otevřít složku IntelliSense](media/open-folder-intellisense-mode.png "Otevřít složku IntelliSense")

Podporovány jsou následující hodnoty:

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
- Linux – RSZ – ARM

Poznámka: hodnoty `msvc-x86` a `msvc-x64` se podporují jenom z původních důvodů. Místo toho použijte `windows-msvc-*` varianty.

## <a name="pre-defined-environments"></a>Předem definovaná prostředí

Visual Studio poskytuje následující předdefinovaná prostředí pro Microsoft C++ , která se mapují na odpovídající Developer Command Prompt. Při dědění jednoho z těchto prostředí můžete na libovolnou z proměnných prostředí odkazovat pomocí `env` globálních vlastností s touto syntaxí makra: $ {env.\<VARIABLE >}.

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

## <a name="user_defined_environments"></a>Uživatelsky definovaná prostředí

Volitelně můžete použít vlastnost `environments` k definování sad proměnných v *CppProperties. JSON* buď globálně, nebo podle konfigurace. Tyto proměnné se chovají podobně jako proměnné prostředí v kontextu projektu otevřené složky a jsou k němu přistupované pomocí syntaxe $ {env.\<VARIABLE >} z *Tasks. vs. JSON* a *Launch. vs. JSON* po jejich definování. Nicméně nejsou nutně nastaveny jako skutečné proměnné prostředí v jakémkoli příkazovém řádku, který aplikace Visual Studio používá interně.

**Visual Studio 2019 verze 16,4 a novější:** Proměnné specifické pro konfiguraci, které jsou definovány v souboru *CppProperties. JSON* , jsou automaticky vyzvednuty cíli ladění a úkoly, aniž by bylo nutné nastavovat `inheritEnvironments`. Cíle ladění se spustí automaticky s prostředím, které zadáte v *CppProperties. JSON*.

**Visual Studio 2019 verze 16,3 a starší:** Když spotřebováváte prostředí, musíte ho zadat ve vlastnosti `inheritsEnvironments`, i když je prostředí definované jako součást stejné konfigurace. vlastnost `environment` Určuje název prostředí. Následující příklad ukazuje ukázkovou konfiguraci pro povolení IntelliSense pro RSZ v instalaci MSYS2. Všimněte si, jak konfigurace definuje a dědí `mingw_64` prostředí a jak má vlastnost `includePath` přístup k proměnné `INCLUDE`.

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
> `%WindowsSdkDir%` a `%VCToolsInstallDir%` nejsou nastaveny jako globální proměnné prostředí, takže je třeba spustit soubor Devenv. exe z Developer Command Prompt definujícího tyto proměnné. (Zadejte "Developer" v nabídce Windows Start.)

## <a name="troubleshoot-intellisense-errors"></a>Řešení chyb IntelliSense

Pokud nevidíte očekávanou technologii IntelliSense, můžete řešit problémy tak, že v části **nástroje** > **Možnosti** > **textový editor** > **C/C++**  > **Rozšířené** a nastavení **Povolit protokolování** na **hodnotu true**. Pokud chcete začít, zkuste nastavit **úroveň protokolování** na 5 a **filtry protokolování** na 8.

![Protokolování diagnostiky](media/diagnostic-logging.png)

Výstup je připojen do **okno výstup** a zobrazí se, když zvolíte možnost **Zobrazit výstup z: vizuálního C++ protokolu**. Výstup obsahuje mimo jiné seznam skutečných cest, které IntelliSense pokouší použít. Pokud cesty se neshodují s těmi v *CppProperties. JSON*, zkuste zavřít složku a odstranit podsložku *. vs* , která obsahuje data procházení v mezipaměti.

Chcete-li vyřešit chyby technologie IntelliSense způsobené chybějícími cestami, otevřete **Seznam chyb** a filtrujte jeho výstup na "pouze IntelliSense" a kód chyby E1696 "nemůže otevřít zdrojový soubor...".
