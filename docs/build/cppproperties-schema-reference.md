---
title: CppProperties.json odkaz
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
# <a name="cpppropertiesjson-reference"></a>CppProperties.json odkaz

Otevřít projekty složek, které nepoužívají CMake, můžete uložit nastavení konfigurace projektu pro IntelliSense do souboru *CppProperties.json.* (CMake projekty používají soubor [CMakeSettings.json.)](customize-cmake-settings.md) Konfigurace se skládá z dvojice název/hodnota a definuje #include cesty, přepínače kompilátoru a další parametry. Další informace o přidání konfigurací v projektu Otevřít složku naleznete v tématu [Open Folder projects for C++.](open-folder-projects-cpp.md) Následující části shrnují různá nastavení. Úplný popis schématu naleznete na *CppProperties_schema.json*, jehož úplná cesta je uvedena v horní části editoru kódu při otevření *souboru CppProperties.json.*

## <a name="configuration-properties"></a>Vlastnosti konfigurace

Konfigurace může mít některou z následujících vlastností:

|||
|-|-|
|`inheritEnvironments`| Určuje, která prostředí se vztahují k této konfiguraci.|
|`name`|Název konfigurace, který se zobrazí v rozevíracím souboru konfigurace jazyka C++|
|`includePath`|Seznam složek oddělených čárkami, který by měl být zadán v cestě zahrnutí (mapuje na /I pro většinu kompilátorů)|
|`defines`|Seznam maker, která by měla být definována (mapuje na /D pro většinu kompilátorů)|
|`compilerSwitches`|Jeden nebo více dalších přepínačů, které mohou ovlivnit chování technologie IntelliSense|
|`forcedInclude`|Hlavička, která má být automaticky zahrnuta do každé kompilační jednotky (mapuje na /FI pro MSVC nebo -include pro clang)|
|`undefines`|Seznam maker, která mají být nedefinována (mapuje na /U pro MSVC)|
|`intelliSenseMode`|Použitý modul IntelliSense. Můžete zadat jednu z předdefinovaných variant specifických pro architekturu pro MSVC, gcc nebo Clang.|
|`environments`|Uživatelem definované sady proměnných, které se chovají jako proměnné prostředí v příkazovém\< řádku a jsou přístupné pomocí ${env. PROMĚNNÁ>}.|

### <a name="intellisensemode-values"></a>hodnoty intelliSenseMode

Editor kódu zobrazuje dostupné možnosti, když začnete psát:

![Otevřít složku IntelliSense](media/open-folder-intellisense-mode.png "Otevřít složku IntelliSense")

Jedná se o podporované hodnoty:

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
- linux-gcc-paže

Poznámka: Hodnoty `msvc-x86` `msvc-x64` a jsou podporovány pouze ze starších důvodů. Místo `windows-msvc-*` toho použijte varianty.

## <a name="pre-defined-environments"></a>Předdefinovaná prostředí

Visual Studio poskytuje následující předdefinovaná prostředí pro Microsoft C++, která se mapují na odpovídající příkazový řádek pro vývojáře. Pokud zdědíte jedno z těchto prostředí, můžete odkazovat na libovolnou proměnnou prostředí pomocí globální vlastnosti `env` s touto syntaxí makra: ${env.\< PROMĚNNÁ>}.

|Název proměnné|Popis|
|-----------|-----------------|
|vsdev|Výchozí prostředí sady Visual Studio|
|msvc_x86|Kompilace pro x86 pomocí nástrojů x86|
|msvc_x64|Kompilace pro AMD64 pomocí 64bitových nástrojů|
|msvc_arm|Kompilace pro ARM pomocí nástrojů x86|
|msvc_arm64|Kompilace pro ARM64 pomocí nástrojů x86|
|msvc_x86_x64|Kompilace pro AMD64 pomocí nástrojů x86|
|msvc_arm_x64|Kompilace pro ARM pomocí 64bitových nástrojů|
|msvc_arm64_x64|Kompilace pro ARM64 pomocí 64bitových nástrojů|

Při instalaci úlohy Linuxu jsou k dispozici následující prostředí pro vzdálené cílení na Linux a WSL:

|Název proměnné|Popis|
|-----------|-----------------|
|linux_x86|Cíl x86 Linux na dálku|
|linux_x64|Cíl x64 Linux na dálku|
|linux_arm|Cíl ARM Linux na dálku|

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a>Uživatelsky definovaná prostředí

Volitelně `environments` můžete použít vlastnost k definování sad proměnných v *CppProperties.json* globálně nebo na konfiguraci. Tyto proměnné se chovají jako proměnné prostředí v kontextu projektu otevřít složku a lze přistupovat pomocí ${env.\< VARIABLE>} syntaxe z *tasks.vs.json* a *launch.vs.json* poté, co jsou zde definovány. Však nejsou nutně nastaveny jako skutečné proměnné prostředí v libovolném příkazovém řádku, který Visual Studio používá interně.

**Visual Studio 2019 verze 16.4 a novější:** Proměnné specifické pro konfiguraci definované v *souboru CppProperties.json* jsou automaticky zachyceny ladicími cíli a úkoly bez nutnosti nastavení `inheritEnvironments`. Ladění cílů se spouštějí automaticky s prostředím, které zadáte v *souboru CppProperties.json*.

**Visual Studio 2019 verze 16.3 a starší:** Když spotřebováváte prostředí, pak je nutné `inheritsEnvironments` zadat ve vlastnosti i v případě, že prostředí je definováno jako součást stejné konfigurace; `environment` vlastnost určuje název prostředí. Následující příklad ukazuje ukázkovou konfiguraci pro povolení technologie IntelliSense for GCC v instalaci msys2. Všimněte si, jak konfigurace definuje `mingw_64` a dědí `includePath` prostředí a `INCLUDE` jak vlastnost může přistupovat k proměnné.

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

Když definujete vlastnost **prostředí** uvnitř konfigurace, přepíše všechny globální proměnné se stejným názvem.

## <a name="built-in-macros"></a>Vestavěná makra

Máte přístup k následujícím integrovaným makrům uvnitř *souboru CppProperties.json*:

|||
|-|-|
|`${workspaceRoot}`| Úplná cesta ke složce pracovního prostoru|
|`${projectRoot}`| Úplná cesta ke složce, do které je umístěn soubor *CppProperties.json*|
|`${env.vsInstallDir}`| Úplná cesta ke složce, ve které je nainstalována spuštěná instance sady Visual Studio|

### <a name="example"></a>Příklad

Pokud má projekt složku include a obsahuje také *soubor Windows.h* a další běžná záhlaví sady Windows SDK, můžete aktualizovat konfigurační soubor *CppProperties.json* pomocí následujících:

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
> `%WindowsSdkDir%`a `%VCToolsInstallDir%` nejsou nastaveny jako globální proměnné prostředí, takže se ujistěte, že spustíte devenv.exe z příkazového řádku pro vývojáře, který definuje tyto proměnné. (V nabídce Start systému Windows zadejte "developer".)

## <a name="troubleshoot-intellisense-errors"></a>Poradce při potížích s chybami technologie IntelliSense

Pokud nevidíte intelliSense, které očekáváte, můžete řešit problémy s **textem nástroje** > **Options** > **Editor** > **C/C++** > **Upřesnit** a nastavení **Povolit protokolování** na **true**. Chcete-li začít, zkuste nastavit **úroveň protokolování** na 5 a **filtry protokolování** na 8.

![Protokolování diagnostiky](media/diagnostic-logging.png)

Výstup je odpočat do **výstupního okna** a je viditelný, když zvolíte **Zobrazit výstup z: Visual C++ Log**. Výstup obsahuje mimo jiné seznam skutečných cest zahrnutí, které se intelliSense pokouší použít. Pokud cesty neodpovídají cestám v *souboru CppProperties.json*, zkuste složku zavřít a odstranit podsložku *.vs,* která obsahuje data procházení uložené v mezipaměti.

Chcete-li odstranit chyby Technologie IntelliSense způsobené chybějícími, otevřete **seznam chyb** a filtrujte jeho výstup na "Pouze Technologie IntelliSense" a kód chyby E1696 "nelze otevřít zdrojový soubor ...".
