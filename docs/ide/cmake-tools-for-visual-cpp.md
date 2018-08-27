---
title: Projekty CMake v jazyce Visual C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/28/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0e7852ad3fbd88b815aea8266bafc2879494d8a
ms.sourcegitcommit: f923f667065cd6c4203d10ca9520600ee40e5f84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900664"
---
# <a name="cmake-projects-in-visual-c"></a>Projekty CMake v jazyce Visual C++

Tento článek předpokládá, že máte zkušenosti s CMake, různé platformy, open source nástroj pro definování procesů sestavení, které běží na různých platformách.

V sadě Visual Studio 2015, Visual Studio uživatelé můžou použít [generátoru CMake](https://cmake.org/cmake/help/v3.9/manual/cmake-generators.7.html) a vygenerujte soubory projektu MSBuild, které prostředí IDE potom využívá pro technologii IntelliSense, procházení a kompilace. 

Spouští se v sadě Visual Studio 2017 **nástroje Visual C++ pro CMake** komponenta používá **otevřít složku** funkce umožňuje rozhraní IDE využívat CMake soubory projektu (například soubor CMakeLists.txt) přímo pro účely technologie IntelliSense a procházení. Pokud používáte Visual Studio generátor, dočasný projekt souboru se vygeneruje a předat msbuild.exe, ale je nikdy načtena pro IntelliSense nebo prohlížením účely. 

**Visual Studio 2017 verze 15.3**: podpora se poskytuje pro generátory Ninja a sady Visual Studio.

**Visual Studio 2017 verze 15.4**: byla přidána podpora CMake v Linuxu. Další informace najdete v tématu [konfigurace projektu Linux CMake](../linux/cmake-linux-project.md).

**Visual Studio 2017 verze 15.5**: Přidání podpory pro import existujících mezipaměť CMake. Visual Studio automaticky vybere vlastní proměnné a vytvoří předvyplněný souboru CMakeSettings.json.

**Visual Studio 2017 verze 15.7**: byla přidána podpora zakázání mezipaměť automatické generování zobrazení cílů v **Průzkumníka řešení**a kompilaci jednoho souboru.

## <a name="installation"></a>Instalace

**Nástroje Visual C++ pro CMake** je ve výchozím nastavení nainstalován jako součást **vývoj desktopových aplikací pomocí C++** pracovního vytížení.

![Komponenta CMake v C++ Desktop](media/cmake-install.png)
 
## <a name="ide-integration"></a>Integrace integrovaného vývojového prostředí

Pokud zvolíte **soubor | Otevřít | Složka** otevřete složku obsahující soubor CMakeLists.txt, se stane následujících věcí:

- Visual Studio přidá **CMake** položky nabídky do hlavní nabídky, s příkazy pro prohlížení a úpravy skriptů CMake.
- **Průzkumník řešení** zobrazí strukturu složek a souborů.
- Visual Studio spustí CMake.exe a generuje mezipaměť CMake pro výchozí *konfigurace*, což je x86 ladění. CMake příkazového řádku se zobrazí v **okno výstup**, společně s další výstup z CMake.  **Visual Studio 2017 verze 15.7 nebo novější**: mezipaměť automatické generování můžete zakázat na **nástroje | Možnosti | CMake | Obecné** dialogového okna.
- Na pozadí spustí aplikace Visual Studio k indexování zdrojové soubory, které chcete povolit technologii IntelliSense, informací o procházení, refaktoring a tak dále. Při práci, Visual Studio sleduje změny v editoru a taky na disku pro synchronizaci jeho indexů se zdroji.
 
Můžete otevřít složek, které neobsahují libovolný počet projekty CMake. Visual Studio zjistí a nakonfiguruje všechny soubory "root" soubor CMakeLists.txt ve vašem pracovním prostoru. Operace CMake (konfigurovat, vytvářet, ladit) stejně jako C++ IntelliSense a procházení jsou k dispozici pro všechny projekty CMake v pracovním prostoru.

![Projekt CMake s více kořenových adresářů](media/cmake-multiple-roots.png)  

**Visual Studio 2017 verze 15.7 nebo novější**: můžete také zobrazit projekty logicky uspořádané podle cíle. Zvolte **cílí na zobrazení** z rozevíracího seznamu v **Průzkumníka řešení** nástrojů:

![Tlačítko pro zobrazení cílů CMake](media/cmake-targets-view.png)

## <a name="import-an-existing-cache"></a>Importovat stávající mezipaměti

Při importu stávajícího souboru CMakeCache.txt Visual Studio automaticky extrahuje vlastní proměnné a předem naplněných souboru CMakeSettings.json na jejich základě vytvoří. Původní mezipaměti není žádným způsobem upravit a je stále možné z příkazového řádku nebo pomocí libovolné nástrojů nebo integrovaného vývojového prostředí byla použita k jeho vygenerování. Nový soubor CMakeSettings.json je umístěn společně s projektu kořenový soubor CMakeLists.txt. Visual Studio vygeneruje nové mezipaměti na základě souboru nastavení.  


**Visual Studio 2017 verze 15.7 nebo novější**: mezipaměť automatické generování v můžete přepsat **nástroje | Možnosti | CMake | Obecné** dialogového okna.

Ne vše, co v mezipaměti je importován.  Vlastnosti, jako je generátor kódu a umístění kompilátory jsou nahrazeny výchozích hodnot, které se ví, že dobře fungují s integrovaného vývojového prostředí.

### <a name="to-import-an-existing-cache"></a>Chcete-li importovat existující mezipaměti

1. V hlavní nabídce zvolte **soubor | Otevřít | CMake**:

   ![Otevřete CMake](media/cmake-file-open.png "souboru, otevřít, CMake") 

   Tím se zobrazí **Import CMake z mezipaměti** průvodce. 
   
2. Přejděte k souboru CMakeCache.txt, který chcete importovat a potom klikněte na tlačítko **OK**. **Importem projektu CMake z mezipaměti** průvodce se zobrazí:

   ![Importovat mezipaměť CMake](media/cmake-import-wizard.png "otevřete Průvodce importem mezipaměti CMake") 

   Po dokončení průvodce se zobrazí nový soubor CMakeCache.txt v **Průzkumníka řešení** vedle kořenový soubor CMakeLists.txt ve vašem projektu.


## <a name="building-cmake-projects"></a>Vytváření projektů CMake

Pokud chcete vytvořit projekt CMake, máte tyto možnosti:

1. Vyberte cíl **ladění** rozevírací seznam a stiskněte klávesu **F5**, nebo klikněte na tlačítko **spustit** tlačítko (zeleným trojúhelníkem). Automaticky sestavení projektu nejprve, stejně jako řešení sady Visual Studio.
1. Klikněte pravým tlačítkem na soubor CMakeLists.txt a vyberte **sestavení** v místní nabídce. Pokud máte více cílů ve struktuře složek, můžete k vytvoření všech nebo jenom jeden konkrétní cíl, nebo
1. V hlavní nabídce vyberte **sestavení | Vytvoření řešení** (**F7** nebo **Ctrl + Shift + B**). Ujistěte se, že cíl CMake je už vybraná ve **položku při spuštění** rozevírací seznam v **Obecné** nástrojů.

![Vytvoření příkazu nabídky CMake](media/cmake-build-menu.png "CMake vytvoření příkazu nabídky") 

Při výběru sady Visual Studio generátor pro aktivní konfiguraci, je vyvolána MSBuild.exe s `-m -v:minimal` argumenty. Přizpůsobení sestavení v souboru CMakeSettings.json, můžete zadat další argumenty příkazového řádku mají být předány prostřednictvím systému sestavení `buildCommandArgs` vlastnost:

```json
"buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
```

Jak by jste očekávali, výsledky sestavení jsou uvedeny v **okno výstup** a **seznam chyb**.
 
![Chyby sestavení CMake](media/cmake-build-errors.png "chyby sestavení CMake")

Ve složce s více cílů pro sestavení, můžete použít **sestavení** položku **CMake** nabídky nebo **CMakeLists.txt** kontextovou nabídku k určení, které se zaměřují CMake k sestavení. Stisknutím klávesy **Ctrl + Shift + B** ve CMake projekt se sestaví aktuálně aktivní dokument.

## <a name="debug-the-project"></a>Ladění projektu

Chcete-li ladit projekt CMake, vyberte požadované konfigurace a stiskněte klávesu **F5**, nebo stisknutím klávesy **spustit** tlačítko na panelu nástrojů. Pokud **spustit** tlačítku zobrazeno "Vybrat položku při spuštění", vyberte šipku rozevíracího seznamu a vyberte cíl, který chcete spustit. (V projektu CMake, "aktuální dokument" možnost je platná pouze pro soubory .cpp.) 

![Spuštění CMake tlačítko](media/cmake-run-button.png "CMake spustit tlačítko")

**Spustit** nebo **F5** příkazy nejprve sestavte projekt, pokud se změnily od předchozího sestavení.

## <a name="configure-cmake-debugging-sessions"></a>Konfigurace CMake ladicími relacemi

Všechny spustitelné cílů CMake jsou uvedeny v **položku při spuštění** rozevírací seznam v **Obecné** nástrojů. Spuštění ladicí relace, vyberte jeden a spuštění ladicího programu.

![Rozevírací seznam položky po spuštění CMake](media/cmake-startup-item-dropdown.png "CMake spouštěcí položka rozevíracího seznamu")


Můžete také spustit relaci ladění z nabídky CMake.

Chcete-li přizpůsobit nastavení ladicího programu pro libovolný spustitelný cíl CMake ve vašem projektu, klikněte pravým tlačítkem na konkrétní soubor CMakeLists.txt a vyberte **nastavení ladění a spouštění**. Když vyberete cíl CMake v podnabídce, se vytvoří soubor s názvem souboru launch.vs.json. Tento soubor se předem načtou informace o cílové CMake, které jste vybrali a můžete zadat další parametry jako argumenty programu nebo typ ladicího programu. Chcete-li odkazovat všechny klíče v souboru CMakeSettings.json, adresa s "CMake." v souboru launch.vs.json. Následující příklad ukazuje jednoduchý launch.vs.json soubor, který získává v hodnotě "remoteCopySources" klíč v souboru CMakeSettings.json pro aktuálně vybranou konfiguraci:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
   {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

Po uložení souboru launch.vs.json, bude vytvořena položka ve **položku při spuštění** rozevírací seznam s novým názvem. Pomocí úpravy souboru launch.vs.json, můžete vytvořit podle mnoha konfiguraci ladění, kolik potřebujete pro libovolný počet cílů CMake.

**Visual Studio 2017 verze 15.4**: Launch.vs.json podporuje proměnné, které jsou deklarovány v souboru CMakeSettings.json (viz níže) a, která se vztahují na aktuálně vybrané konfigurace. Obsahuje také klíč s názvem "currentDir", který nastaví aktuální adresář spouštění aplikace:


```json
{
"type": "default",
"project": "CMakeLists.txt",
"projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Při spuštění aplikace, hodnota `currentDir` je podobný

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```

## <a name="editing-cmakeliststxt-files"></a>Úprava souborů CMakeLists.txt

Chcete-li upravit soubor CMakeLists.txt, klikněte pravým tlačítkem myši na soubor v **Průzkumníka řešení** a zvolte **otevřít**. Pokud provedete změny do souboru, se zobrazí žlutá stavový řádek a vás informuje, že technologie IntelliSense se aktualizuje a vám dává možnost zrušit operaci aktualizace. Informace o soubor CMakeLists.txt, najdete v článku [CMake dokumentaci](https://cmake.org/documentation/).

   ![Úpravy souboru CMakeLists.txt](media/cmake-cmakelists.png "úpravy souboru CMakeLists.txt")


Jakmile soubor uložíte, krok konfigurace automaticky znovu spustí a zobrazí informace v **výstup** okna. Chyby a upozornění se zobrazují v **seznam chyb** nebo **výstup** okna. Poklikejte na chybu **seznam chyb** přejděte k problémovému řádku v soubor CMakeLists.txt.

   ![Chyby soubor CMakeLists.txt](media/cmake-cmakelists-error.png "chyby souboru CMakeLists.txt")

## <a name="cmake_settings"></a> Vlastní konfigurace a nastavení CMake

Ve výchozím nastavení Visual Studio poskytuje šest výchozí konfigurace CMake ("x86-Debug", "x86 verze", "x64-Debug", "x64 – verze", "Linux-Debug" a "Linux-Release"). Tyto konfigurace definovat, jak je CMake.exe vyvolá pro vytvoření mezipaměti CMake pro daný projekt. Chcete-li upravit tyto konfigurace nebo vytvořit novou vlastní konfiguraci, zvolte **CMake | Změnit nastavení CMake**a klikněte na tlačítko, které bude nastavení platit pro soubor CMakeLists.txt. **Změnit nastavení CMake** příkaz je také k dispozici na místní nabídky souboru v **Průzkumníka řešení**. Tento příkaz vytvoří soubor CMakeSettings.json ve složce projektu. Tento soubor slouží k vytvoření souboru mezipaměti CMake znovu například po **Vyčistit** operace. 

   ![Příkaz hlavní nabídky CMake pro změnu nastavení](media/cmake-change-settings.png)

Technologie IntelliSense JSON umožňuje úpravy souboru CMakeSettings.json:

   ![Technologie IntelliSense CMake JSON](media/cmake-json-intellisense.png "CMake JSON technologii IntelliSense")

Následující příklad ukazuje ukázkové konfiguraci, která slouží jako výchozí bod, chcete-li vytvořit vlastní aplikaci v souboru CMakeSettings.json:

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

1. **název**: název, který se zobrazí v rozevírací nabídce konfigurace C++. Hodnota této vlastnosti může také sloužit jako makra, `${name}`, zadat jiné hodnoty vlastností. Příklad najdete v tématu **buildRoot** definice v souboru CMakeSettings.json.
1. **Generátor**: mapuje **- G** přepnutí a určuje generátor, který se má použít. Tato vlastnost slouží také jako makra, `${generator}`, a tím pomáhá určit jiné hodnoty vlastností. Visual Studio v současné době podporuje následující generátorů CMake:

    - "Ninja"
    - "Visual Studio 14 2015"
    - "Visual Studio 14 2015 ARM"
    - "Visual Studio 14 2015 Win64"
    - "Visual Studio 15 2017"
    - "Visual Studio 15 2017 ARM"
    - "Visual Studio 15 2017 Win64"

Protože Ninja je určená pro rychlé sestavení rychlosti místo flexibilitu a funkce, je nastavit jako výchozí. Některé projekty CMake, ale možná nebudete moct správně programujte Ninja. Pokud k tomu dojde, můžete dát pokyn CMake pro generování projektu sady Visual Studio místo.

Chcete-li zadat generátoru Visual Studio, otevřete CMakeSettings.json v hlavní nabídce výběrem **CMake | Změnit nastavení CMake**. Odstraňte "Ninja" a zadejte "V". Tím se aktivuje technologii IntelliSense, která vám umožní vybrat generátor, který chcete.

1. **buildRoot**: mapuje **-DCMAKE_BINARY_DIR** přepnutí a určuje, kde se vytvoří mezipaměť CMake. Pokud složka neexistuje, vytvoří se.
1. **proměnné**: obsahuje dvojice název hodnota proměnné CMake, které budou získat předány jako **-D**_název_**=**_hodnotu_ do programu CMake. Pokyny k sestavení projektu CMake zadání přidání všech proměnných přímo do souboru mezipaměti CMake, se doporučuje jste je přidali tady místo.
1. **cmakeCommandArgs**: Určuje žádné další přepínače, které chcete předat CMake.exe.
1. **výběru typu konfigurace**: definuje typ konfigurace sestavení pro vybraný generátor. Aktuálně podporované hodnoty jsou "Debug", "MinSizeRel", "Verze" a "RelWithDebInfo".
1. **ctestCommandArgs**: Určuje další přepínače, které mají být předány do programu CTest při spouštění testů.
1. **buildCommandArgs**: Určuje další přepínače k předání do základního sestavovací systém. Například předávání - v, při použití generátor Ninja vynutí Ninja výstup příkazové řádky.

### <a name="environment-variables"></a>Proměnné prostředí

CMakeSettings.json také podporuje používání proměnných prostředí v některém z vlastností uvedených výše. Syntaxe pro použití `${env.FOO}` rozšíření prostředí % variable % FOO.
Máte také přístup k předdefinované makra v tomto souboru:

- `${workspaceRoot}` – poskytuje úplnou cestu složky pracovního prostoru
- `${workspaceHash}` – Hodnota hash umístění pracovního prostoru. užitečné pro vytváření jedinečný identifikátor pro aktuální pracovní prostor (například pro použití v cesty ke složkám)
- `${projectFile}` – Úplná cesta kořenového souboru CMakeLists.txt
- `${projectDir}` – Úplná cesta ke složce kořenového souboru CMakeLists.txt
- `${thisFile}` – úplnou cestu souboru CMakeSettings.json
- `${name}` – Název konfigurace
- `${generator}` – Název generátoru CMake použít v této konfiguraci

### <a name="ninja-command-line-arguments"></a>Argumenty příkazového řádku ninja

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
|   -n      | suší spuštění (nemusíte spouštět příkazy, ale fungovala tak, jako jsou proběhlo úspěšně)|
|   -v       | Zobrazit všechny příkazových řádků během sestavování|
|   -d režimu  | povolte ladění (použití -d režimy seznamu)|
|   t – nástroj  | Spusťte subtool (použijte -t seznamu podřízených nástrojích). Ukončí toplevel možnosti; Další příznaky jsou předány do nástroje| 
|   -w příznak  | Upravte upozornění (použijte -w seznamu upozornění)|

### <a name="inherited-environments-visual-studio-2017-version-155"></a>Zděděných prostředí (Visual Studio 2017 verze 15.5)
CMakeSettings.json teď podporuje zděděných prostředí. Tato funkce umožňuje (1) dědit výchozí prostředí a (2) vytvořte vlastní proměnné prostředí, které se předá CMake.exe při spuštění.

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

Výše uvedený příklad je stejný jako spuštění **Developer Command Prompt for VS 2017** s **-arch = amd64 – host_arch = amd64** argumenty.

V následující tabulce jsou uvedeny výchozí hodnoty a jejich ekvivalenty příkazového řádku:

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
V souboru CMakeSettings.json, můžete definovat vlastní proměnné prostředí globálně nebo podle konfigurace v **prostředí** vlastnost. Následující příklad definuje jeden globální proměnné, **BuildDir**, dědí se v konfiguracích ladění x86 i x64 ladění. Každá konfigurace používá zadat hodnotu pro proměnnou **buildRoot** vlastnosti pro tuto konfiguraci. Všimněte si také, jak jednotlivé konfigurace používá **inheritEnvironments** vlastnosti a určit proměnnou, která se vztahuje pouze na tuto konfiguraci.

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

V následujícím příkladu definuje konfiguraci ladění x86 jeho vlastní hodnotě. pro **BuildDir** vlastnost a tato hodnota přepíše hodnoty nastavené v globální **BuildDir** vlastnost tak, aby  **BuildRoot** vyhodnotí jako `D:\custom-builddir\x86-Debug`.

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

## <a name="cmake-configure-step"></a>Krok konfigurace CMake

Při významných změn souboru CMakeSettings.json nebo soubory soubor CMakeLists.txt, Visual Studio automaticky krok konfigurace CMake opakování. Krok konfigurace dokončí bez chyb, informace, které jsou shromažďovány, je k dispozici v C++ IntelliSense a jazykových služeb a také v sestavení a ladění operace.

Když více projektů CMake použijte stejný název konfigurace CMake (například x86-Debug), všechny z nich jsou konfigurovány a integrovanou (vlastní sestavení do kořenové složky) při výběru této konfigurace. Můžete ladit cíle ze všech projektů CMake, které jsou součástí konfigurace CMake.

   ![CMake vytvářet pouze položky nabídky](media/cmake-build-only.png "CMake vytvářet pouze položky nabídky")

Omezit sestavení a ladění relace dílčích projektů v pracovním prostoru, vytvořte novou konfiguraci jedinečný název v souboru CMakeSettings.json a použijte ji na těchto projektech pouze. Pokud je vybraná tato konfigurace, technologie IntelliSense a sestavení a ladění příkazy jsou povoleny pouze pro zadané projekty.

## <a name="troubleshooting-cmake-cache-errors"></a>Řešení potíží s chybami mezipaměti CMake

Pokud potřebujete další informace o stavu mezipaměti CMake k diagnostice problému, otevřete **CMake** hlavní nabídky nebo **CMakeLists.txt** kontextové nabídky **Průzkumníka řešení**na některou z těchto příkazů:

- **Zobrazení mezipaměti** otevře soubor CMakeCache.txt z kořenové složky sestavení v editoru. (Veškeré úpravy provedené tady CMakeCache.txt jsou dojde k vymazání Pokud vyčištění mezipaměti. Pokud chcete provést změny, které se zachovávají po vyčištění mezipaměti, naleznete v tématu [CMake nastavení a vlastní konfigurace](#cmake_settings) dříve v tomto článku.)
- **Otevřít složku mezipaměti** se otevře okno Průzkumníka ke kořenové složce sestavení.  
- **Vyčištění mezipaměti** odstraní kořenové složce sestavení tak, aby krok začíná od čistá mezipaměť konfigurace další CMake.
- **Vygenerovat mezipaměť** vynutí generovat kroku spustit i v případě, že aplikace Visual Studio považuje aktuální prostředí.
 
**Visual Studio 2017 verze 15.7 nebo novější**: mezipaměť automatické generování můžete zakázat na **nástroje | Možnosti | CMake | Obecné** dialogového okna.

## <a name="single-file-compilation"></a>Kompilace jednoho souboru

**Visual Studio 2017 verze 15.7 nebo novější**: Pokud chcete vytvořit jeden soubor projektu CMake, klikněte pravým tlačítkem na soubor v **Průzkumníku řešení** a zvolte **kompilaci**. Můžete také vytvořit soubor, který je právě otevřen v editoru pomocí hlavní nabídky CMake:

![Kompilace jednoho souboru CMake](media/cmake-single-file-compile.png)