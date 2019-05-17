---
title: CppProperties.json schéma – referenční informace
ms.date: 05/16/2019
helpviewer_keywords:
- CMake in Visual Studio
ms.openlocfilehash: e80f4e8a189510a9a3e8860609d74121b7cbb0ef
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837039"
---
# <a name="cpppropertiesjson-schema-reference"></a>CppProperties.json schéma – referenční informace

Otevřít složku projekty, které nepoužívají CMake můžete uložit nastavení konfigurace projektu v `CppProperties.json` souboru. (Použití projekty CMake [CMakeSettings.json](customize-cmake-settings.md) souboru.) Integrované vývojové prostředí sady Visual Studio používá `CppProperties.json` pro technologii IntelliSense a navigace v kódu. Konfigurace se skládá z dvojice název/hodnota a definuje #include cesty, přepínače kompilátoru a další parametry. 


## <a name="default-configurations"></a>Výchozí konfigurace

Visual Studio poskytuje předdefinované konfigurace pro x86 a x64 pro ladění a vydání. Ve výchozím nastavení, váš projekt, má konfiguraci x86 ladění `CppProperties.json`. Chcete-li přidat novou konfiguraci, klikněte pravým tlačítkem na `CppProperties.json` ve **Průzkumníka řešení** a zvolte **Přidat konfiguraci**:

![Otevřít složku přidat konfiguraci](media/open-folder-add-config.png "otevřít složku přidat novou konfiguraci")

Výchozí konfigurace se tady zobrazí:

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    },
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Release",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "NDEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```
Pro vlastnosti, které obsahují sadu povolených hodnot editor kódu zobrazuje dostupné možnosti, když začnete psát:

![Open Folder IntelliSense](media/open-folder-intellisense-mode.png "Open Folder IntelliSense")



## <a name="configuration-properties"></a>Vlastnosti konfigurace

Konfigurace může mít některou z následujících vlastností:

|||
|-|-|
|`name`|Název konfigurace, který se zobrazí v rozevírací nabídce konfigurace C++|
|`includePath`|Seznam složek, které musí být zadán v cesty zahrnutí (mapuje /I pro většina kompilátorů)|
|`defines`|seznam maker, která by měla být definována (mapuje /D pro většina kompilátorů)|
|`compilerSwitches`|jeden nebo více dalších přepínačů, které mohou mít vliv na chování technologie IntelliSense|
|`forcedInclude`|hlavičky, které mají být automaticky zahrnuty ve všech jednotkách kompilace (/FI mapuje pro MSVC nebo – zahrnout pro clang)|
|`undefines`|seznam maker na nedefinované (mapuje /U pro MSVC)|
|`intelliSenseMode`|modul IntelliSense, který se má použít. Můžete zadat konkrétní varianty architektury pro MSVC a gcc, Clang:<br/><br/>- windows-msvc-x86 (default)<br/>- windows-msvc-x64<br/>- msvc-arm<br/>- windows-clang-x86<br/>- windows-clang-x64<br/>-windows-clang-arm<br/>- Linux-x64<br/>- Linux-x86<br/>-Linux-arm<br/>-gccarm|

Poznámka: Hodnoty `msvc-x86` a `msvc-x64` podporují pouze starším verzím. Použijte prosím `windows-msvc*` variant.

## <a name="custom-configurations"></a>Vlastní konfigurace


Můžete přizpůsobit kteroukoliv z výchozí konfigurace ve `CppProperties.json`, nebo vytvořit nové konfigurace. Každý se zobrazí v rozevírací nabídce konfigurace:

```json
{
  "configurations": [
    {
      "name": "Windows",
      ...
    },
    {
      "name": "with EXTERNAL_CODECS",
      ...
    }
  ]
}
```

## <a name="system-environment-variables"></a>Proměnné prostředí systému 

 `CppProperties.json` podporuje systém rozšíření proměnné prostředí pro zahrnout cesty a dalších hodnot vlastností. Syntaxe je `${env.FOODIR}` rozbalit proměnné prostředí `%FOODIR%`. Podporují se také následující proměnných definovaných systémem:

|Název proměnné|Popis|
|-----------|-----------------|
|vsdev|Výchozí prostředí sady Visual Studio|
|msvc_x86|Sestavit x86 x86 pomocí nástroje|
|msvc_arm|Kompilování pro ARM pomocí x86 nástroje|
|msvc_arm64|Použitou ke kompilaci pro ARM64 x86 nástroje|
|msvc_x86_x64|Kompilace z důvodu AMD64 x86 pomocí nástroje|
|msvc_x64_x64|Kompilace z důvodu AMD64 použití 64bitových nástrojů|
|msvc_arm_x64|Kompilace pro použití 64bitových nástrojů ARM|
|msvc_arm64_x64|Kompilace pro ARM64 použití 64bitových nástrojů|

Když je nainstalovaná úloha Linux, jsou k dispozici pro systémy Linux a WSL vzdáleným cílením následujících prostředích:

|Název proměnné|Popis|
|-----------|-----------------|
|linux_x86|Cíl x86 Linux vzdáleně|
|linux_x64|Cíl x64 Linux vzdáleně|
|linux_arm|Vzdáleně určené pro ARM Linux|

## <a name="custom-environment-variables"></a>Vlastní proměnné prostředí

Můžete definovat vlastní proměnné prostředí v `CppProperties.json` buď globálně nebo podle konfigurace. Následující příklad ukazuje, jak výchozí a vlastní proměnné prostředí může být deklarovaný a používá. Globální **prostředí** vlastnost deklaruje proměnnou s názvem **zahrnout** , který mohou využívat všechny konfigurace:

```json
{
  // The "environments" property is an array of key value pairs of the form
  // { "EnvVar1": "Value1", "EnvVar2": "Value2" }
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
    }
  ],

  "configurations": [
    {
      "inheritEnvironments": [
        // Inherit the MSVC 32-bit environment and toolchain.
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "inheritEnvironments": [
        // Inherit the MSVC 64-bit environment and toolchain.
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined above.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```
## <a name="per-configuration-environment-variables"></a>Proměnné prostředí podle konfigurace

Můžete také definujte **prostředí** uvnitř konfiguraci tak, že platí pouze pro tuto konfiguraci a přepíše všechny globální proměnné se stejným názvem vlastnosti. V následujícím příkladu x64 konfigurace definuje místní **zahrnout** proměnné, která přepíše globální hodnotu:

```json
{
  "environments": [
    {
      "INCLUDE": "${workspaceRoot}\src\includes"
    }
  ],

  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x86"
      ],
      "name": "x86",
      "includePath": [
        // Use the include path defined in the global environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x86"
    },
    {
      "environments": [
        {
          // Append 64-bit specific include path to env.INCLUDE.
          "INCLUDE": "${env.INCLUDE};${workspaceRoot}\src\includes64"
        }
      ],

      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64",
      "includePath": [
        // Use the include path defined in the local environments property.
        "${env.INCLUDE}"
      ],
      "defines": [ "WIN32", "_DEBUG", "UNICODE", "_UNICODE" ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```

Všechny vlastní a jsou dostupné v proměnné prostředí výchozí `tasks.vs.json` a `launch.vs.json`.

#### <a name="build-in-macros"></a>Makra sestavení v

Máte přístup k následující předdefinované makra v `CppProperties.json`:

|||
|-|-|
|`${workspaceRoot}`| Úplná cesta ke složce pracovního prostoru|
|`${projectRoot}`| Úplná cesta ke složce kde `CppProperties.json` nachází|
|`${vsInstallDir}`| Úplná cesta ke složce, kde je nainstalována spuštěné instance sady Visual Studio|

Například pokud váš projekt má zahrnout složku a také zahrnuje windows.h a dalších běžných hlaviček ze sady Windows SDK, můžete k aktualizaci vašeho `CppProperties.json` konfigurační soubor s těmito zahrnuje:

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
> `%WindowsSdkDir%` a `%VCToolsInstallDir%` nejsou nastaveny jako globálních proměnných prostředí proto ujistěte se, že začnete devenv.exe z příkazový řádek vývojáře, který definuje tyto proměnné. (Zadejte "pro vývojáře" v nabídce Windows Start.)

## <a name="troubleshoot-intellisense-errors"></a>Řešení potíží technologie IntelliSense

Řešení potíží s IntelliSense chyby způsobené chybějící vkládaným, otevřete **seznam chyb** a filtrovat výstup "Pouze technologie IntelliSense" a kódem chyby E1696 "nelze otevřít zdrojový soubor...".



