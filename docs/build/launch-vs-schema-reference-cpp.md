---
title: Launch. vs. JSON – Referenční dokumentaceC++schématu ()
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: 5d8f657dda58d581ccc3441a777fdf31470ef25f
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518228"
---
# <a name="launchvsjson-schema-reference-c"></a>Launch. vs. JSON – Referenční dokumentaceC++schématu ()

K nakonfigurování parametrů ladění použijte soubor *Launch. vs. JSON* . Pro vytvoření souboru. pravým tlačítkem myši klikněte na spustitelný soubor v **Průzkumník řešení** a vyberte **nastavení ladění a spouštění**. Zvolte možnost, která nejlépe odpovídá vašemu projektu, a pak podle potřeby upravte konfiguraci pomocí následujících vlastností. Další informace o ladění projektů CMake najdete v tématu [Konfigurace relací ladění cmake](/cpp/build/configure-cmake-debugging-sessions).

## <a name="default-properties"></a>Výchozí vlastnosti

||||
|-|-|-|
|**Vlastnost**|**Typ**|**Popis**|
|`name`|odkazy řetězců|Určuje název položky v rozevíracím seznamu cíl ladění.|
|`type`|odkazy řetězců|Určuje, zda se jedná o projekt, nebo soubor. exe (ve výchozím nastavení je to. exe).|
|`project`|odkazy řetězců|Určuje relativní cestu k souboru projektu.|
|`projectTarget`|odkazy řetězců|Určuje nepovinný cíl vyvolaný při sestavování `project`. Tato `projectTarget` musí existovat a odpovídat názvu v rozevíracím seznamu **cíl ladění** .|
|`debugType`|odkazy řetězců|Určuje režim ladění podle typu kódu (nativní, spravovaná nebo smíšená). Tato akce bude automaticky zjištěna, pokud tento parametr není nastaven. Povolené hodnoty: "nativní", "spravovaná", "smíšená".|
|`inheritEnvironments`|pole|Určuje sadu proměnných prostředí děděných z více zdrojů. Můžete definovat některé proměnné v souborech, jako je *CMakeSettings. JSON* nebo *CppProperties. JSON* , a zpřístupnit je pro ladění kontextu.  **Visual Studio 16,4:** : zadejte proměnné prostředí pro jednotlivé cíle pomocí syntaxe `env.VARIABLE_NAME`. Chcete-li proměnnou zrušit, nastavte ji na hodnotu null.|
|`args`|pole|Určuje argumenty příkazového řádku předané spuštěnému programu.|
|`currentDir`|odkazy řetězců|Určuje úplnou cestu k adresáři pro cíl sestavení. Tato akce bude automaticky zjištěna, pokud tento parametr není nastaven.|
|`noDebug`|Logická hodnota|Určuje, zda se má ladit spuštěný program. Výchozí hodnota pro tento parametr je `false`, pokud není zadána.|
|`stopOnEntry`|Logická hodnota|Určuje, zda se má při spuštění procesu, a připojení ladicího programu k chvíli přerušit. Výchozí hodnota pro tento parametr je `false`.|
|`remoteMachine`|odkazy řetězců|Určuje název vzdáleného počítače, ve kterém je program spuštěn.|
|`env`|pole| Určuje seznam klíčových hodnot vlastních proměnných prostředí. ENV: {"myEnv": "myVal"}.|
|`portName`|odkazy řetězců|Určuje název portu při připojování ke spuštěnému procesu.|
|`buildConfigurations`|pole| Pár klíč-hodnota, který určuje název režimu sestavení pro použití konfigurací. Například `Debug` nebo `Release` a konfigurace, které se mají použít v závislosti na vybraném režimu sestavení.

## <a name="c-linux-properties"></a>C++Vlastnosti systému Linux

||||
|-|-|-|
|**Vlastnost**|**Typ**|**Popis**|
|`program`|odkazy řetězců|Úplná cesta ke spustitelnému souboru programu na vzdáleném počítači. Při použití CMake je možné makro `${debugInfo.fullTargetPath}` použít jako hodnotu tohoto pole.|
|`processId`|integer|Volitelné ID procesu, ke kterému se má ladicí program připojit.|
|`sourceFileMap`|Objekt nástroje|Volitelné mapování zdrojových souborů předané do ladicího stroje. Formát: `{ "\<Compiler source location>": "\<Editor source location>" }` nebo `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`. Příklad: `{ "/home/user/foo": "C:\\foo" }` nebo `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Viz [Možnosti mapování zdrojového souboru](#source_file_map_options).|
|`additionalProperties`|odkazy řetězců|Jedna z sourceFileMapOptions. (Viz níže)|
|`MIMode`|odkazy řetězců|Určuje typ ladicího programu pro konzolu s podporou MI, ke kterému se MIDebugEngine připojí. Povolené hodnoty jsou "GDB", "lldb".|
|`args`|pole|Argumenty příkazového řádku předané programu|
|`environment`|pole|Proměnné prostředí, které se mají přidat do prostředí pro program Příklad: [{"Name": "Squid"; "value": "zapro"}].|
|`targetArchitecture`|odkazy řetězců|Architektura laděného procesu Tato akce bude automaticky zjištěna, pokud tento parametr není nastaven. Povolené hodnoty jsou x86, ARM, arm64, MIPS, x64, AMD64, x86_64.|
|`visualizerFile`|odkazy řetězců|soubor. Natvis, který se použije při ladění tohoto procesu. Tato možnost není kompatibilní s tiskem GDB s poměrně. Pokud se toto nastavení používá, podívejte se na "showDisplayString".|
|`showDisplayString`|Logická hodnota|Když je zadán visualizerFile, showDisplayString umožní zobrazit řetězec. Zapnutí této možnosti může způsobit pomalejší výkon během ladění.|
|`remoteMachineName`|odkazy řetězců|Vzdálený počítač se systémem Linux hostující GDB a program, který se má ladit. Pomocí Správce připojení přidejte nové počítače se systémem Linux. Při použití CMake je možné makro `${debugInfo.remoteMachineName}` použít jako hodnotu tohoto pole.|
|`cwd`|odkazy řetězců|Pracovní adresář cíle na vzdáleném počítači. Při použití CMake je možné makro `${debugInfo.defaultWorkingDirectory}` použít jako hodnotu tohoto pole. Výchozí hodnota je kořenový adresář vzdáleného pracovního prostoru, pokud není přepsán v souboru *CMakeLists. txt* .|
|`miDebuggerPath`|odkazy řetězců|Cesta k ladicímu programu s podporou MI (například GDB). Je-li tento parametr zadán, bude nejprve hledána cesta ladicího programu.|
|`miDebuggerServerAddress`|odkazy řetězců|Síťová adresa serveru ladicího programu s podporou MI, ke kterému se má připojit. Příklad: localhost: 1234.|
|`setupCommands`|pole|Jeden nebo více příkazů GDB/LLDB, které mají být provedeny, aby bylo možné nastavit základní ladicí program. Příklad: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Viz [spustit instalační příkazy](#launch_setup_commands).|
|`customLaunchSetupCommands`|pole|Pokud je tato hodnota zadaná, nahradí výchozí příkazy, které se použijí ke spuštění cíle, s některými jinými příkazy. To může být například "-Target-Attach", aby bylo možné se připojit k cílovému procesu. Prázdný seznam příkazů nahrazuje příkazy pro spuštění bez Nothing, což může být užitečné v případě, že ladicí program poskytuje možnosti spuštění jako možnosti příkazového řádku. Příklad: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|odkazy řetězců|Příkaz, který má být spuštěn po úplném nastavení ladicího programu, aby způsobil spuštění cílového procesu. Povolené hodnoty jsou "EXEC-Run", "EXEC-Continue", "none". Výchozí hodnota je "EXEC-Run".|
|`debugServerPath`|odkazy řetězců|Volitelná úplná cesta k ladicímu serveru, který se má spustit. Výchozí hodnota je null.|
|`debugServerArgs`|odkazy řetězců|Volitelné argumenty ladicího serveru. Výchozí hodnota je null.|
|`filterStderr`|Logická hodnota|Vyhledejte Stream stderr pro vzor spuštěný na serveru a Zaprotokolujte stderr, abyste mohli ladit výstup. Výchozí hodnota je `false`.|
|`coreDumpPath`|odkazy řetězců|Volitelná úplná cesta k základnímu souboru s výpisem paměti pro zadaný program Výchozí hodnota je null.|
externalConsole|Logická hodnota|Pokud je nastaveno na true, spustí se pro laděného procesu konzola. Pokud `false`, konzola se nespustí. Výchozí hodnota je `false`. Poznámka: Tato možnost se v některých případech v technických důvodech ignoruje.|
|`pipeTransport`|odkazy řetězců|Pokud je k dispozici, říká ladicímu programu, aby se připojil ke vzdálenému počítači pomocí jiného spustitelného souboru jako kanálu, který bude přenášet standardní vstup/výstup mezi Visual Studio a ladicím programem s podporou MI (například GDB). Povolené hodnoty: jedna nebo více [možností přenosu kanálu](#pipe_transport_options).|


## <a name="launch_setup_commands"></a>Spustit instalační příkazy

Používá se s vlastností `setupCommands`:

||||
|-|-|-|
|`text`|odkazy řetězců|Příkaz ladicího programu, který se má provést.|
|`description`|odkazy řetězců|Volitelný popis příkazu|
|`ignoreFailures`|Logická hodnota|Je-li nastavena hodnota true, chyby z příkazu by měly být ignorovány. Výchozí hodnota je `false`.|

## <a name = "pipe_transport_options"></a>Možnosti přenosu kanálu

Používá se s vlastností `pipeTransport`:

||||
|-|-|-|
|`pipeCwd`|odkazy řetězců|Plně kvalifikovaná cesta k pracovnímu adresáři pro program kanálu.|
|`pipeProgram`|odkazy řetězců|Plně kvalifikovaný příkaz kanálu, který se má provést.|
|`pipeArgs`|pole|Argumenty příkazového řádku předané programu kanálu ke konfiguraci připojení.|
|`debuggerPath`|odkazy řetězců|Úplná cesta k ladicímu programu na cílovém počítači, například/usr/bin/GDB|
|`pipeEnv`|Objekt nástroje|Proměnné prostředí předané do programu kanálu.|
|`quoteArgs`|Logická hodnota|Pokud jednotlivé argumenty obsahují znaky (například mezery nebo tabulátory), měly by být v uvozovkách? Pokud `false`, příkaz ladicího programu už nebude automaticky citovaný. Výchozí hodnota je `true`.|

## <a name="source_file_map_options"></a>Možnosti mapování zdrojového souboru

Použijte s vlastností `sourceFileMap`:

||||
|-|-|-|
|`editorPath`|odkazy řetězců|Umístění zdrojového kódu pro Editor, který se má najít.|
|`useForBreakpoints`|Logická hodnota|Při nastavování zarážek by se mělo použít toto mapování zdroje. Pokud `false`, použije se k nastavení zarážek jenom název souboru a číslo řádku. Pokud `true`, zarážky budou nastaveny s úplnou cestou k souboru a číslem řádku pouze v případě, že je použito toto mapování zdroje. Jinak se při nastavování zarážek použije jenom název souboru a číslo řádku. Výchozí hodnota je `true`.|
