---
title: CMake projektů v jazyce Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2017
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
ms.openlocfilehash: f3a65ae6cc58f649fee5f47b33a146263a3b6c55
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337428"
---
# <a name="cmake-projects-in-visual-c"></a>CMake projektů v jazyce Visual C++

Tento článek předpokládá, že jste obeznámeni s CMake, nástroj napříč platformami, open source pro definování sestavení procesy, které běží na více platforem.

Dokud nedávno uživatelé sady Visual Studio může používat CMake pro vygenerování souborů projektu nástroje MSBuild, které integrovaného vývojového prostředí poté využité pro technologii IntelliSense, procházení a kompilace. Od verze Visual Studio 2017 **nástroje sady Visual C++ pro CMake** součást používá **otevřít složku** funkce povolit IDE využívat CMake soubory projektu (například CMakeLists.txt) přímo pro účely IntelliSense a procházení. Pokud používáte Visual Studio generátor, soubor dočasný projekt se vygeneruje a předaný msbuild.exe, ale to se nikdy pro IntelliSense nebo procházení pro účely načtená. 

**Visual Studio 2017 verze 15.3**: podpora je k dispozici pro generátory expertem a Visual Studio.

**Visual Studio 2017 verzi 15.4**: byla přidána podpora CMake v systému Linux. Další informace najdete v tématu [konfigurace projektu CMake Linux](../linux/cmake-linux-project.md).

**Visual Studio 2017 verze 15,5**: je přidána podpora pro import existující CMake mezipaměti. Visual Studio automaticky extrahuje vlastní proměnné a vytvoří soubor předem vyplněná CMakeSettings.json.


## <a name="installation"></a>Instalace

**Nástroje sady Visual C++ pro CMake** je ve výchozím nastavení nainstalovaná jako součást **vývoj aplikací s jazykem C++** zatížení.

![CMake součástí zatížení plochy C++](media/cmake-install.png)
 
## <a name="ide-integration"></a>Integrace rozhraní IDE

Pokud vyberete **souboru | Otevřete | Složka** otevřete složku obsahující soubor CMakeLists.txt, dojít v následujících akcí:

- Visual Studio. přidá **CMake** položku nabídky do hlavní nabídky, pomocí příkazů pro prohlížení a úpravy CMake skripty.
- **Průzkumník řešení** zobrazí struktura složek a souborů.
- Visual Studio spustí CMake.exe a generuje CMake mezipaměti pro výchozí *konfigurace*, což je x86 ladění. CMake příkazového řádku se zobrazí v **výstup – okno**, společně s další výstup z CMake.
- Visual Studio na pozadí, začne index zdrojové soubory pro povolení technologie IntelliSense, informace o procházení, refaktoring a tak dále. Při práci, Visual Studio sleduje změny v editoru a také na disku pro synchronizujte její index s zdroje.
 
Můžete otevřít složky obsahující libovolný počet CMake projekty. Visual Studio zjistí a nakonfiguruje všechny soubory CMakeLists.txt "root" v pracovním prostoru. Operace CMake (konfigurace, vytvářet, ladit) a také C++ IntelliSense a procházení, které jsou k dispozici pro všechny projekty CMake v pracovním prostoru.

![CMake projektu s více kořenových certifikačních autorit](media/cmake-multiple-roots.png) 

## <a name="import-an-existing-cache"></a>Importovat stávající mezipaměti

Při importu existujícího souboru CMakeCache.txt Visual Studio automaticky extrahuje vlastní proměnné a vytvoří soubor předem vyplněná CMakeSettings.json na jejich základě. Původní mezipaměti není nijak změněny a je stále možné z příkazového řádku nebo s jakoukoli nástroj IDE použila nebo jej vygenerovat. Nový soubor CMakeSettings.json je umístěn společně projektu kořenové CMakeLists.txt. Visual Studio vytvoří novou mezipaměti na základě soubor s nastaveními. Vše, v mezipaměti je naimportována.  Vlastnosti, například generátor a umístění kompilátory jsou nahrazeny výchozí hodnoty, které jsou známé funkce fungují dobře u rozhraní IDE.

### <a name="to-import-an-existing-cache"></a>Chcete-li importovat existující mezipaměti

1. Z hlavní nabídky zvolte **souboru | Otevřete | CMake**:

   ![Otevřete CMake](media/cmake-file-open.png "souboru, otevřít, CMake") 

   Po výběru této možnosti **CMake Import z mezipaměti** průvodce. 
   
2. Přejděte k souboru CMakeCache.txt, který chcete importovat a pak klikněte na **OK**. **Importovat projekt CMake z mezipaměti** zobrazí se průvodce:

   ![Import mezipaměti CMake](media/cmake-import-wizard.png "otevřete Průvodce importem mezipaměti CMake") 

   Po dokončení průvodce se zobrazí nový soubor CMakeCache.txt v **Průzkumníku řešení** vedle v kořenovém souboru CMakeLists.txt ve vašem projektu.


## <a name="building-cmake-projects"></a>Vytváření CMake projekty

Pro vytvoření projektu CMake, máte tyto možnosti:

1. Vyberte cíl v **ladění** rozevíracího seznamu a stiskněte klávesu **F5**, nebo klikněte na tlačítko **spustit** tlačítko (zeleným trojúhelníkem). Automaticky sestavení projektu nejprve, stejně jako řešení sady Visual Studio.
1. Klikněte pravým tlačítkem na CMakeLists.txt a vyberte **sestavení** v místní nabídce. Pokud máte více cílů struktury složky, můžete vytvořit všechny nebo pouze jeden konkrétní cíl, nebo
1. V hlavní nabídce vyberte **sestavení | Vytvoření řešení** (**F7** nebo **Ctrl + Shift + B**). Ujistěte se, že cíl CMake je již vybrána v **položku při spuštění** rozevírací seznam v **Obecné** panelu nástrojů.

![CMake sestavení příkazu v nabídce](media/cmake-build-menu.png "Cmake sestavení příkaz nabídky") 

Pokud generátor Visual Studio je vybraná pro aktivní konfigurace, MSBuild.exe vyvolání `-m -v:minimal` argumenty. Chcete-li přizpůsobit sestavení v souboru CMakeSettings.json, můžete zadat další argumenty příkazového řádku mají být předány sestavení systému prostřednictvím `buildCommandArgs` vlastnost:

```json
"buildCommandArgs": "-m:8 -v:minimal -p:PreferredToolArchitecture=x64"
```

Jak jste zvyklí, výsledky sestavení jsou zobrazeny v **výstup – okno** a **seznam chyb**.
 
![Chyby sestavení CMake](media/cmake-build-errors.png "CMake chyby sestavení")

Ve složce s více cílů sestavení, můžete **sestavení** položku **CMake** nabídky nebo **CMakeLists.txt** kontextovou nabídku k určení, které cíle CMake sestavení. Stisknutím **Ctrl + Shift + B** v CMake sestavení projektů aktuální aktivní dokument.

## <a name="debug-the-project"></a>Ladění projektu

K ladění projektu pro CMake, vyberte požadované konfigurace a stiskněte klávesu **F5**, nebo stiskněte klávesu **spustit** tlačítka na panelu nástrojů. Pokud **spustit** tlačítko říká "Vyberte položku při spuštění", vyberte na šipku rozevíracího seznamu a vyberte cíl, který chcete spustit. (V projektu CMake "aktuální dokument" možnost je platná pouze pro soubory sada.) 

![Tlačítko Spustit CMake](media/cmake-run-button.png "Cmake spustit tlačítko")


**Spustit** nebo **F5** příkazy nejprve sestavení projektu, pokud byly provedeny změny od předchozího sestavení.

## <a name="configure-cmake-debugging-sessions"></a>Konfigurace CMake ladění relací

Všechny cíle spustitelné CMake se zobrazují v **položku při spuštění** rozevírací seznam v **Obecné** panelu nástrojů. Chcete-li spustit relaci ladění, vyberte jeden a spuštění ladicího programu.

![Rozevírací seznam položky spuštění CMake](media/cmake-startup-item-dropdown.png "CMake spuštění položky rozevíracího seznamu")


Z nabídky CMake můžete spustit také na relaci ladění.

Chcete-li přizpůsobit nastavení ladicího programu pro všechny spustitelné cíl CMake ve vašem projektu, klikněte pravým tlačítkem na konkrétní CMakeLists.txt soubor a vyberte **ladění a spusťte nastavení**. Když vyberete cíl CMake v nabídce dílčí, vytvoří se soubor s názvem launch.vs.json. Tento soubor je předem vyplnit s informacemi o CMake cíl, který jste zvolili a umožňuje vám určit další parametry, třeba typ ladicí program nebo program argumenty. Chcete-li jakékoli klíč v souboru CMakeSettings.json, adresa s "cmake." v launch.vs.json. Následující příklad ukazuje jednoduchý launch.vs.json soubor, který žádá o v hodnotě "remoteCopySources" klíč v souboru CMakeSettings.json pro aktuálně vybrané konfigurace:

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

Jakmile jste uložili soubor launch.vs.json, položka je vytvořena v **položku při spuštění** rozevírací seznam s novým názvem. Úpravou souboru launch.vs.json můžete vytvářet podle potřeby pro libovolný počet cílů CMake mnoho konfigurace ladění.

**Visual Studio 2017 verzi 15.4**: Launch.vs.json podporuje proměnné, které jsou deklarované v CMakeSettings.json (viz níže) a které se vztahují na aktuálně vybrané konfiguraci. Je také klíč s názvem "currentDir", která nastaví aktuální adresář spuštění aplikace:


```json
{
"type": "default",
"project": "CMakeLists.txt",
"projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
"currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Při spuštění aplikace a hodnotu `currentDir` je podobný

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```

## <a name="editing-cmakeliststxt-files"></a>Úprava CMakeLists.txt souborů

Chcete-li upravit soubor CMakeLists.txt, klikněte pravým tlačítkem na soubor v **Průzkumníku řešení** a zvolte **otevřete**. Pokud provedete změny do souboru, se zobrazí žlutý stavového řádku a uvidíte, že bude aktualizovat IntelliSense a vám dává příležitost ke zrušení operace aktualizace. Informace o CMakeLists.txt najdete v tématu [CMake dokumentaci](https://cmake.org/documentation/).

   ![Úpravy souborů CMakeLists.txt](media/cmake-cmakelists.png "CMakeLists.txt úpravy souborů")


Také můžete uložit soubor, konfigurace automaticky spustí znovu a zobrazí informace v **výstup** okno. Chyby a upozornění se zobrazují v **seznam chyb** nebo **výstup** okno. Dvakrát klikněte na chybu v **seznam chyb** přejděte k řádku problematické v CMakeLists.txt.

   ![Chyby souboru CMakeLists.txt](media/cmake-cmakelists-error.png "chyby CMakeLists.txt souboru")

## <a name="cmake_settings"></a> CMake nastavení a vlastní konfigurace

Ve výchozím nastavení Visual Studio poskytuje šesti výchozí konfigurace CMake ("x86-Debug", "X86verze", "x64-Debug", "X64verze", "Linux-Debug" a "Linux-Release"). Tyto konfigurace definovat, jak je CMake.exe vyvolána k vytvoření mezipaměti CMake pro daný projekt. Chcete-li upravit tyto konfigurace nebo vytvořte novou vlastní konfiguraci, zvolte **CMake | Změna nastavení CMake**a potom zvolte soubor CMakeLists.txt, že nastavení platí pro. **Změnit nastavení CMake** je k dispozici na místní nabídky souboru v také **Průzkumníku řešení**. Tento příkaz vytvoří soubor CMakeSettings.json ve složce projektu. Tento soubor se používá k vytvoření souboru mezipaměti CMake znovu například po **Vyčistit** operaci. 

   ![Příkaz CMake hlavní nabídky pro změnu nastavení](media/cmake-change-settings.png)


JSON IntelliSense umožňuje upravovat soubor CMakeSettings.json:

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Následující příklad ukazuje Ukázková konfigurace, který můžete použít jako výchozí bod pro vytvoření vlastní aplikaci v CMakeSettings.json:

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

1. **název**: název, který se zobrazí v rozevírací nabídce C++ konfigurace. Hodnota této vlastnosti lze také jako makra, `${name}`, k určení dalších hodnot vlastností. Příklad, naleznete v části **buildRoot** definice v CMakeSettings.json.
1. **Generátor**: se mapuje **- G** přepínače a určí, generátor, který se má použít. Tato vlastnost slouží také jako makra, `${generator}`, můžete zadat další hodnoty vlastností. Visual Studio teď podporuje následující generátory CMake:


    - "Expertem"
    - "Visual Studio 14 2015"
    - "Sady visual Studio 14 2015 ARM"
    - "Sady visual Studio 14 2015 Win64"
    - "Visual Studio 15 2017"
    - "Sady visual Studio 15 2017 ARM"
    - "Sady visual Studio 15 2017 Win64"

Protože expertem je navržený pro rychlé sestavení rychlosti místo flexibilitu a funkce, je nastaven jako výchozí. Některé projekty CMake však může nelze správně vytvořit pomocí expertem. Pokud k tomu dojde, můžete určit, aby CMake místo generovat projekt sady Visual Studio.

Chcete-li zadat generátor Visual Studio, otevřete CMakeSettings.json z hlavní nabídky výběrem **CMake | Změna nastavení CMake**. Odstraňte "Expertem" a zadejte "V". Tím dojde k aktivaci technologii IntelliSense, která vám umožní vybrat generátor, které chcete.

1. **buildRoot**: mapuje **-DCMAKE_BINARY_DIR** přepínače a určuje, kde bude vytvořen CMake mezipaměti. Pokud složka neexistuje, vytvoří se.
1. **proměnné**: obsahuje dvojice název hodnota CMake proměnných, které budou získat předá jako **-D**_název_**=**_hodnotu_ k CMake. Pokud vaše pokyny pro sestavení projektu CMake zadat přidání všech proměnných přímo do souboru CMake mezipaměti, se doporučuje přidávat zde místo.
1. **cmakeCommandArgs**: Určuje žádné další přepínače, které chcete předat CMake.exe.
1. **configurationType**: definuje typ konfigurace sestavení pro vybrané generátor. Aktuálně podporované hodnoty jsou "Ladění", "MinSizeRel", "Verze" a "RelWithDebInfo".

### <a name="environment-variables"></a>Proměnné prostředí

CMakeSettings.json také podporuje využívání proměnné prostředí v žádném z vlastností uvedených výše. Syntaxe pro použití `${env.FOO}` rozšíření prostředí FOO % variable %.
Máte také přístup k předdefinované makra uvnitř tohoto souboru:

- `${workspaceRoot}` – poskytuje úplnou cestu ke složce pracovního prostoru
- `${workspaceHash}` – Hodnota hash prostoru location; užitečné pro vytváření jedinečný identifikátor pro aktuální pracovní prostor (například pro použití v cestách ke složkám)
- `${projectFile}` – úplnou cestu v kořenovém souboru CMakeLists.txt
- `${projectDir}` – úplnou cestu ke složce v kořenovém souboru CMakeLists.txt
- `${thisFile}` – úplnou cestu k souboru CMakeSettings.json
- `${name}` – Název konfigurace
- `${generator}` – Název generátoru CMake použít v této konfiguraci

### <a name="ninja-command-line-arguments"></a>Argumenty příkazového řádku expertem

Pokud jsou cíle neurčené, sestavení cíl "default" (viz ručně).

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise>ninja -?
ninja: invalid option -- `-?'
usage: ninja [options] [targets...]
```

|Možnost|Popis|
|--------------|------------|
| – verze  | Tisk expertem verze ("1.7.1")|
|   -C DIR   | Změňte DIR před provedením další akce|
|   -f souboru  | Zadejte sestavení vstupní soubor (default=build.ninja)|
|   -j N     | paralelní spuštění úlohy N (výchozí = 14, odvozené z procesorů, které jsou k dispozici)|
|   -k N     | Pokračujte dokud N úloh selže (výchozí = 1)|
|   -l N     | Pokud průměrná hodnota zatížení je větší než N nespouštět nové úlohy|
|   -n      | suší spustit (Nespouštět příkazy ale fungovat jako jejich úspěšné)|
|   -v       | Zobrazit všechny příkazy na příkazových řádcích při sestavování|
|   -d režimu  | povolte ladění (použití -d seznamu režimy)|
|   -t nástroj  | Spusťte subtool (použití -t seznamu podřízených nástrojích). Ukončí možnosti toplevel; Další příznaky jsou předávány nástroj| 
|   -w příznak  | Upravte upozornění (použití -w seznamu upozornění)|

### <a name="inherited-environments-visual-studio-2017-version-155"></a>Zděděné prostředí (Visual Studio 2017 verze 15,5)
CMakeSettings.json teď podporuje zděděné prostředí. Tato funkce umožňuje (1) dědit výchozí prostředí a (2) vytvářet vlastní prostředí proměnné, které se budou předávat CMake.exe při spuštění.

```json
  "inheritEnvironments": [ "msvc_x64_x64" ]
```

V předchozím příkladu je stejný jako spuštěná **příkazový řádek vývojáře pro VS 2017** s **– architektura = amd64-host_arch = amd64** argumenty.

Následující tabulka uvádí výchozí hodnoty a jejich ekvivalenty příkazového řádku:

|Název kontextu|Popis|
|-----------|-----------------|
|vsdev|Výchozí prostředí Visual Studio|
|msvc_x86|Kompilace pro x86 x86 pomocí nástroje|
|msvc_arm| Kompilace pro ARM pomocí x86 nástroje|
|msvc_arm64|Kompilace pro ARM64 x86 pomocí nástroje|
|msvc_x86_x64|Kompilace pro AMD64 x86 pomocí nástroje|
|msvc_x64_x64|Kompilace pro AMD64 pomocí nástrojů 64-bit|
|msvc_arm_x64|Kompilace pro ARM pomocí nástrojů 64-bit|
|msvc_arm64_x64|Kompilace pro ARM64 pomocí nástrojů 64-bit|

### <a name="custom-environment-variables"></a>Vlastní proměnné prostředí
V CMakeSettings.json, můžete definovat vlastní proměnné prostředí globálně nebo na konfiguraci v **prostředí** vlastnost. V následujícím příkladu definuje jednu globální proměnnou **BuildDir**, který zdědí v konfiguracích x86 ladění a x64-Debug. Každá konfigurace používá zadejte hodnotu pro proměnnou **buildRoot** vlastnost pro danou konfiguraci. Všimněte si také, jak každý konfigurace používá **inheritEnvironments** vlastnosti k určení, proměnné, která se vztahuje pouze na danou konfiguraci.

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

V následujícím příkladu definuje konfiguraci ladění x86 vlastní hodnotu pro **BuildDir** vlastnost a tato hodnota přepíše hodnotu nastaven na globální **BuildDir** vlastnost tak, aby  **BuildRoot** vyhodnocuje `D:\custom-builddir\x86-Debug`.

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

## <a name="cmake-configure-step"></a>CMake konfigurace krok

Provedení významných změn CMakeSettings.json nebo CMakeLists.txt soubory, Visual Studio automaticky znovu spustí CMake nakonfigurujte krok. Krok konfigurace se dokončí bez chyb, informace, které jsou shromažďovány, je k dispozici v C++ IntelliSense a jazyk služby a také v sestavení a ladění operace.

Při více projektů CMake používají stejný název konfigurace CMake (například x86-Debug), všechny z nich jsou nakonfigurované a součástí (vlastní sestavení do kořenové složky) Pokud je vybrána tato konfigurace. Můžete ladit cíle ze všech CMake projekty, které jsou součástí této CMake konfigurace.

   ![CMake vytvářet pouze položky nabídky](media/cmake-build-only.png "CMake vytvářet pouze položky nabídky")

Pokud chcete omezit sestavení a ladění relací na podmnožinu projekty v pracovním prostoru, vytvořte novou konfiguraci s jedinečným názvem v souboru CMakeSettings.json a použijte ho pro pouze ty projekty. Pokud je vybraná tato konfigurace, IntelliSense a sestavení a ladění příkazy jsou povolené jenom pro tyto zadané projekty.

## <a name="troubleshooting-cmake-cache-errors"></a>Řešení potíží s chybami CMake mezipaměti

Pokud potřebujete další informace o stavu mezipaměti CMake diagnostikovat problém, otevřete **CMake** hlavní nabídky nebo **CMakeLists.txt** místní nabídky v **Průzkumníku řešení**spustit jeden z těchto příkazů:

- **Zobrazení mezipaměti** otevře soubor CMakeCache.txt z kořenové složky sestavení v editoru. (Všechny úpravy, které provedete zde CMakeCache.txt se vymažou Pokud vyčištění mezipaměti. Chcete-li provést změny, které trvají po vymazána mezipaměť, přečtěte si téma [CMake nastavení a vlastní konfigurace](#cmake_settings) výše v tomto článku.)
- **Otevřete složku mezipaměti** otevře okno Průzkumníka do kořenové složky sestavení.  
- **Vyčištění mezipaměti** odstraní kořenové složky sestavení tak, aby další CMake konfigurace krok spustí z vyčištění mezipaměti.
- **Generování mezipaměti** vynutí generování krok spustit i v případě, že aplikace Visual Studio považuje aktuální prostředí.
