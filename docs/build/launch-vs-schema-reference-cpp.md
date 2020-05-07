---
title: reference ke schématu Launch. vs. JSON (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: ff4713642ab95a9bbc31f1a06236de459e53f9c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323057"
---
# <a name="launchvsjson-schema-reference-c"></a>reference ke schématu Launch. vs. JSON (C++)

K nakonfigurování parametrů ladění použijte soubor *Launch. vs. JSON* . Pro vytvoření souboru. pravým tlačítkem myši klikněte na spustitelný soubor v **Průzkumník řešení** a vyberte **nastavení ladění a spouštění**. Zvolte možnost, která nejlépe odpovídá vašemu projektu, a pak podle potřeby upravte konfiguraci pomocí následujících vlastností. Další informace o ladění projektů CMake najdete v tématu [Konfigurace relací ladění cmake](/cpp/build/configure-cmake-debugging-sessions).

## <a name="default-properties"></a>Výchozí vlastnosti

||||
|-|-|-|
|**Vlastnost**|**Typ**|**Popis**|
|`name`|řetězec|Určuje název položky v rozevíracím seznamu cíl ladění.|
|`type`|řetězec|Určuje, zda se jedná o projekt, nebo soubor. exe (ve výchozím nastavení je to. exe).|
|`project`|řetězec|Určuje relativní cestu k souboru projektu.|
|`projectTarget`|řetězec|Určuje nepovinný cíl vyvolaný `project`při sestavování. Tento `projectTarget` prvek musí existovat a odpovídat názvu v rozevíracím seznamu **cíl ladění** .|
|`debugType`|řetězec|Určuje režim ladění podle typu kódu (nativní, spravovaná nebo smíšená). Tato akce bude automaticky zjištěna, pokud tento parametr není nastaven. Povolené hodnoty: "nativní", "spravovaná", "smíšená".|
|`inheritEnvironments`|pole|Určuje sadu proměnných prostředí děděných z více zdrojů. Můžete definovat některé proměnné v souborech, jako je *CMakeSettings. JSON* nebo *CppProperties. JSON* , a zpřístupnit je pro ladění kontextu.  **Visual Studio 16,4:**: zadejte proměnné prostředí na základě jednotlivých cílů pomocí `env.VARIABLE_NAME` syntaxe. Chcete-li proměnnou zrušit, nastavte ji na hodnotu null.|
|`args`|pole|Určuje argumenty příkazového řádku předané spuštěnému programu.|
|`currentDir`|řetězec|Určuje úplnou cestu k adresáři pro cíl sestavení. Tato akce bude automaticky zjištěna, pokud tento parametr není nastaven.|
|`noDebug`|Boolean|Určuje, zda se má ladit spuštěný program. Výchozí hodnota pro tento parametr je `false` , pokud není zadána.|
|`stopOnEntry`|Boolean|Určuje, zda se má při spuštění procesu, a připojení ladicího programu k chvíli přerušit. Výchozí hodnota pro tento parametr je `false`.|
|`remoteMachine`|řetězec|Určuje název vzdáleného počítače, ve kterém je program spuštěn.|
|`env`|pole| Určuje seznam klíčových hodnot vlastních proměnných prostředí. ENV: {"myEnv": "myVal"}.|
|`portName`|řetězec|Určuje název portu při připojování ke spuštěnému procesu.|
|`buildConfigurations`|pole| Pár klíč-hodnota, který určuje název režimu sestavení pro použití konfigurací. Například `Debug` nebo `Release` a konfigurace, které mají být použity v závislosti na vybraném režimu sestavení.

## <a name="c-linux-properties"></a>Vlastnosti C++ Linux

||||
|-|-|-|
|**Vlastnost**|**Typ**|**Popis**|
|`program`|řetězec|Úplná cesta ke spustitelnému souboru programu na vzdáleném počítači. Při použití CMake je možné makro `${debugInfo.fullTargetPath}` použít jako hodnotu tohoto pole.|
|`processId`|celé číslo|Volitelné ID procesu, ke kterému se má ladicí program připojit.|
|`sourceFileMap`|objekt|Volitelné mapování zdrojových souborů předané do ladicího stroje. Formát: `{ "\<Compiler source location>": "\<Editor source location>" }` nebo `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`. Příklad: `{ "/home/user/foo": "C:\\foo" }` nebo `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Viz [Možnosti mapování zdrojového souboru](#source_file_map_options).|
|`additionalProperties`|řetězec|Jedna z sourceFileMapOptions. (Viz níže)|
|`MIMode`|řetězec|Určuje typ ladicího programu pro konzolu s podporou MI, ke kterému se MIDebugEngine připojí. Povolené hodnoty jsou "GDB", "lldb".|
|`args`|pole|Argumenty příkazového řádku předané programu|
|`environment`|pole|Proměnné prostředí, které se mají přidat do prostředí pro program Příklad: [{"Name": "Squid"; "value": "zapro"}].|
|`targetArchitecture`|řetězec|Architektura laděného procesu Tato akce bude automaticky zjištěna, pokud tento parametr není nastaven. Povolené hodnoty jsou x86, ARM, arm64, MIPS, x64, AMD64, x86_64.|
|`visualizerFile`|řetězec|soubor. Natvis, který se použije při ladění tohoto procesu. Tato možnost není kompatibilní s tiskem GDB s poměrně. Pokud se toto nastavení používá, podívejte se na "showDisplayString".|
|`showDisplayString`|Boolean|Když je zadán visualizerFile, showDisplayString umožní zobrazit řetězec. Zapnutí této možnosti může způsobit pomalejší výkon během ladění.|
|`remoteMachineName`|řetězec|Vzdálený počítač se systémem Linux hostující GDB a program, který se má ladit. Pomocí Správce připojení přidejte nové počítače se systémem Linux. Při použití CMake je možné makro `${debugInfo.remoteMachineName}` použít jako hodnotu tohoto pole.|
|`cwd`|řetězec|Pracovní adresář cíle na vzdáleném počítači. Při použití CMake je možné makro `${debugInfo.defaultWorkingDirectory}` použít jako hodnotu tohoto pole. Výchozí hodnota je kořenový adresář vzdáleného pracovního prostoru, pokud není přepsán v souboru *CMakeLists. txt* .|
|`miDebuggerPath`|řetězec|Cesta k ladicímu programu s podporou MI (například GDB). Je-li tento parametr zadán, bude nejprve hledána cesta ladicího programu.|
|`miDebuggerServerAddress`|řetězec|Síťová adresa serveru ladicího programu s podporou MI, ke kterému se má připojit. Příklad: localhost: 1234.|
|`setupCommands`|pole|Jeden nebo více příkazů GDB/LLDB, které mají být provedeny, aby bylo možné nastavit základní ladicí program. Příklad: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Viz [spustit instalační příkazy](#launch_setup_commands).|
|`customLaunchSetupCommands`|pole|Pokud je tato hodnota zadaná, nahradí výchozí příkazy, které se použijí ke spuštění cíle, s některými jinými příkazy. To může být například "-Target-Attach", aby bylo možné se připojit k cílovému procesu. Prázdný seznam příkazů nahrazuje příkazy pro spuštění bez Nothing, což může být užitečné v případě, že ladicí program poskytuje možnosti spuštění jako možnosti příkazového řádku. Příklad: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|řetězec|Příkaz, který má být spuštěn po úplném nastavení ladicího programu, aby způsobil spuštění cílového procesu. Povolené hodnoty jsou "EXEC-Run", "EXEC-Continue", "none". Výchozí hodnota je "EXEC-Run".|
|`debugServerPath`|řetězec|Volitelná úplná cesta k ladicímu serveru, který se má spustit. Výchozí hodnota je null.|
|`debugServerArgs`|řetězec|Volitelné argumenty ladicího serveru. Výchozí hodnota je null.|
|`filterStderr`|Boolean|Vyhledejte Stream stderr pro vzor spuštěný na serveru a Zaprotokolujte stderr, abyste mohli ladit výstup. Výchozí hodnota `false`je.|
|`coreDumpPath`|řetězec|Volitelná úplná cesta k základnímu souboru s výpisem paměti pro zadaný program Výchozí hodnota je null.|
externalConsole|Boolean|Pokud je nastaveno na true, spustí se pro laděného procesu konzola. Pokud `false`se nespustí žádná konzola. Výchozí hodnota `false`je. Poznámka: Tato možnost se v některých případech v technických důvodech ignoruje.|
|`pipeTransport`|řetězec|Pokud je k dispozici, říká ladicímu programu, aby se připojil ke vzdálenému počítači pomocí jiného spustitelného souboru jako kanálu, který bude přenášet standardní vstup/výstup mezi Visual Studio a ladicím programem s podporou MI (například GDB). Povolené hodnoty: jedna nebo více [možností přenosu kanálu](#pipe_transport_options).|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a>Spustit instalační příkazy

Používá se s `setupCommands` vlastností:

||||
|-|-|-|
|`text`|řetězec|Příkaz ladicího programu, který se má provést.|
|`description`|řetězec|Volitelný popis příkazu|
|`ignoreFailures`|Boolean|Je-li nastavena hodnota true, chyby z příkazu by měly být ignorovány. Výchozí hodnota `false`je.|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a>Možnosti přenosu kanálu

Používá se s `pipeTransport` vlastností:

||||
|-|-|-|
|`pipeCwd`|řetězec|Plně kvalifikovaná cesta k pracovnímu adresáři pro program kanálu.|
|`pipeProgram`|řetězec|Plně kvalifikovaný příkaz kanálu, který se má provést.|
|`pipeArgs`|pole|Argumenty příkazového řádku předané programu kanálu ke konfiguraci připojení.|
|`debuggerPath`|řetězec|Úplná cesta k ladicímu programu na cílovém počítači, například/usr/bin/GDB|
|`pipeEnv`|objekt|Proměnné prostředí předané do programu kanálu.|
|`quoteArgs`|Boolean|Pokud jednotlivé argumenty obsahují znaky (například mezery nebo tabulátory), měly by být v uvozovkách? Pokud `false`se příkaz ladicího programu už nebude automaticky uvádět v uvozovkách. Výchozí je `true`.|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a>Možnosti mapování zdrojového souboru

Použít s `sourceFileMap` vlastností:

||||
|-|-|-|
|`editorPath`|řetězec|Umístění zdrojového kódu pro Editor, který se má najít.|
|`useForBreakpoints`|Boolean|Při nastavování zarážek by se mělo použít toto mapování zdroje. Pokud `false`se pro nastavení zarážek používá pouze název souboru a číslo řádku. Pokud `true`se nastaví zarážky s úplnou cestou k souboru a číslu řádku pouze v případě, že je použito toto mapování zdroje. Jinak se při nastavování zarážek použije jenom název souboru a číslo řádku. Výchozí je `true`.|
