---
title: Vlastní nastavení sestavení CMake v sadě Visual Studio
ms.date: 03/05/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: aa840dd41ee6843afae80343e42ba62741bbcd80
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822995"
---
# <a name="customize-cmake-build-settings"></a>Vlastní nastavení sestavení CMake

Visual Studio obsahuje několik konfigurací CMake, které definují, jak je CMake.exe vyvolá pro vytvoření mezipaměti CMake pro daný projekt. Chcete-li přidat novou konfiguraci, klikněte na konfigurace rozevíracího seznamu na panelu nástrojů a zvolte **spravovat konfigurace**:

   ![Správa konfigurací CMake](media/cmake-manage-configurations.png)

Můžete vybrat ze seznamu předdefinovaných konfigurací:

   ![Konfigurace předdefinovaných CMake](media/cmake-configurations.png)

Při prvním vyberte konfiguraci, vytvoří Visual Studio `CMakeSettings.json` soubor v kořenové složce vašeho projektu. Tento soubor slouží k vytvoření souboru mezipaměti CMake znovu například po **Vyčistit** operace. 

Chcete-li přidat další konfiguraci, klikněte pravým tlačítkem myši klikněte na tlačítko `CMakeSettings.json` a zvolte **Přidat konfiguraci**. 

   ![Přidat CMake konfiguraci](media/cmake-add-configuration.png "CMake Přidat konfiguraci")

Technologie IntelliSense JSON umožňuje upravit `CMakeSettings.json` souboru:

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

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

- **název**: název, který se zobrazí v rozevírací nabídce konfigurace C++. `${name}` – Makro vám umožní použít tuto hodnotu při vytváření dalších hodnot vlastností, jako je například cesty. Příklad najdete v tématu **buildRoot** definice v `CMakeSettings.json`.

- **Generátor**: mapuje na CMake **- G** přepnutí a určuje generátor, který se má použít. Tato vlastnost slouží také jako makra, `${generator}`, při vytváření dalších hodnot vlastností. Visual Studio v současné době podporuje následující generátorů CMake:

    - "Ninja"
    - "Visual Studio 14 2015"
    - "Visual Studio 14 2015 ARM"
    - "Visual Studio 14 2015 Win64"
    - "Visual Studio 15 2017"
    - "Visual Studio 15 2017 ARM"
    - "Visual Studio 15 2017 Win64"

    Protože Ninja je určená pro rychlé sestavení rychlosti místo flexibilitu a funkce, je nastavit jako výchozí. Některé projekty CMake, ale možná nebudete moct správně programujte Ninja. Pokud k tomu dojde, můžete dát pokyn CMake pro generování projektu sady Visual Studio místo.

    Chcete-li zadat generátoru Visual Studio, otevřete `CMakeSettings.json` v hlavní nabídce výběrem **CMake | Změnit nastavení CMake**. Odstraňte "Ninja" a zadejte "V". Tím se aktivuje technologii IntelliSense, která vám umožní vybrat generátor, který chcete.

    Pokud aktivní konfigurace určuje generátoru Visual Studio, ve výchozím nastavení je MSBuild.exe volána s `-m -v:minimal` argumenty. Přizpůsobení sestavení, uvnitř `CMakeSettings.json` souboru, můžete zadat další [argumenty příkazového řádku MSBuild](../build/msbuild-visual-cpp-overview.md) mají být předány prostřednictvím systému sestavení `buildCommandArgs` vlastnost:
    
    ```json
    "buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
    ```

- **buildRoot**: mapuje **-DCMAKE_BINARY_DIR** přepnutí a určuje, kde se vytvoří mezipaměť CMake. Pokud složka neexistuje, vytvoří se.

- **proměnné**: obsahuje dvojice název hodnota proměnné CMake, které budou získat předány jako **-D** *_název_=_hodnotu_* do programu CMake. Pokyny k sestavení projektu CMake zadání přidání všech proměnných přímo do souboru mezipaměti CMake, se doporučuje jste je přidali tady místo. Následující příklad ukazuje, jak určit dvojice název hodnota pro 14.14.26428 MSVC sady nástrojů:

```json
"variables": [
    {
      "name": "CMAKE_CXX_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe"
    },
    {
      "name": "CMAKE_C_COMPILER",
      "value": "C:/Program Files (x86)/Microsoft Visual Studio/157/Enterprise/VC/Tools/MSVC/14.14.26428/bin/HostX86/x86/cl.exe"
    }
  ]
```

- **cmakeCommandArgs**: Určuje žádné další přepínače, které chcete předat CMake.exe.

- **výběru typu konfigurace**: definuje typ konfigurace sestavení pro vybraný generátor. Aktuálně podporované hodnoty jsou "Debug", "MinSizeRel", "Verze" a "RelWithDebInfo".

- **ctestCommandArgs**: Určuje další přepínače, které mají být předány do programu CTest při spouštění testů.

- **buildCommandArgs**: Určuje další přepínače k předání do základního sestavovací systém. Například předávání - v, při použití generátor Ninja vynutí Ninja výstup příkazové řádky.

Další nastavení jsou k dispozici pro projekty CMake Linux. Zobrazit [konfigurace projektu CMake Linux](../linux/cmake-linux-project.md).

## <a name="environment-variables"></a>Proměnné prostředí

 `CMakeSettings.json` také podporuje používání proměnných prostředí v některém z vlastností uvedených výše. Syntaxe pro použití `${env.FOO}` rozšíření prostředí % variable % FOO.
Máte také přístup k předdefinované makra v tomto souboru:

- `${workspaceRoot}` – poskytuje úplnou cestu složky pracovního prostoru
- `${workspaceHash}` – Hodnota hash umístění pracovního prostoru. užitečné pro vytváření jedinečný identifikátor pro aktuální pracovní prostor (například pro použití v cesty ke složkám)
- `${projectFile}` – Úplná cesta kořenového souboru CMakeLists.txt
- `${projectDir}` – Úplná cesta ke složce kořenového souboru CMakeLists.txt
- `${thisFile}` – Úplná cesta `CMakeSettings.json` souboru
- `${name}` – Název konfigurace
- `${generator}` – Název generátoru CMake použít v této konfiguraci

## <a name="ninja-command-line-arguments"></a>Argumenty příkazového řádku ninja

Pokud nejsou specifikována cíle, vytvoří cíl "default" (v příručce).

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
|   t – nástroj  | Spusťte subtool (použijte -t seznamu podřízených nástrojích). Ukončí toplevel možnosti; Další příznaky jsou předány do nástroje|
|   -w příznak  | Upravte upozornění (použijte -w seznamu upozornění)|

## <a name="inherited-environments"></a>Zděděných prostředí

 `CMakeSettings.json` podporuje dědí prostředí. Tato funkce umožňuje (1) dědit výchozí prostředí a (2) vytvořte vlastní proměnné prostředí, které se předá CMake.exe při spuštění.

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

Výše uvedený příklad je stejný jako spuštění **Developer Command Prompt for VS 2017** s **-arch = amd64 – host_arch = amd64** argumenty.

V následující tabulce jsou uvedeny výchozí hodnoty:

|Název kontextu|Popis|
|-----------|-----------------|
|vsdev|Výchozí prostředí sady Visual Studio|
|msvc_x86|Sestavit x86 x86 pomocí nástroje|
|msvc_arm| Kompilování pro ARM pomocí x86 nástroje|
|msvc_arm64|Použitou ke kompilaci pro ARM64 x86 nástroje|
|msvc_x86_x64|Kompilace z důvodu AMD64 x86 pomocí nástroje|
|msvc_x64_x64|Kompilace z důvodu AMD64 použití 64bitových nástrojů|
|msvc_arm_x64|Kompilace pro použití 64bitových nástrojů ARM|
|msvc_arm64_x64|Kompilace pro ARM64 použití 64bitových nástrojů|

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
          "BuildDir": "D:\\custom-builddir",
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

## <a name="see-also"></a>Viz také

[Projekty CMake v sadě Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)<br/>
[Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md)<br/>
[Nasazení, spuštění a ladění projektu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referenční dokumentace ke konfiguraci CMake předdefinované](cmake-predefined-configuration-reference.md)<br/>
