---
title: reference schématu launch.vs.json (C++)
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
# <a name="launchvsjson-schema-reference-c"></a>reference schématu launch.vs.json (C++)

Ke konfiguraci parametrů ladění použijte soubor *launch.vs.json.* Chcete-li vytvořit soubor. Klikněte pravým tlačítkem myši na spustitelný soubor v **Průzkumníku řešení** a zvolte **Nastavení ladění a spuštění**. Zvolte možnost, která nejvíce odpovídá projektu a pak použijte následující vlastnosti upravit konfiguraci podle potřeby. Další informace o ladění projektů CMake naleznete v [tématu Konfigurace relací ladění CMake](/cpp/build/configure-cmake-debugging-sessions).

## <a name="default-properties"></a>Výchozí vlastnosti

||||
|-|-|-|
|**Vlastnost**|**Typ**|**Popis**|
|`name`|řetězec|Určuje název položky v rozevíracím seznamu Ladění cíle.|
|`type`|řetězec|Určuje, zda je projekt dll nebo .exe (Výchozí hodnota .exe)|
|`project`|řetězec|Určuje relativní cestu k souboru projektu.|
|`projectTarget`|řetězec|Určuje volitelný cíl vyvolaný při vytváření `project`. To `projectTarget` musí existovat již a odpovídat názvu v **rozevíracím** souboru Ladění cíle.|
|`debugType`|řetězec|Určuje režim ladění podle typu kódu (nativní, spravované nebo smíšené). Tato možnost bude automaticky rozpoznána, pokud není tento parametr nastaven. Povolené hodnoty: "nativní", "spravované", "smíšené".|
|`inheritEnvironments`|pole|Určuje sadu proměnných prostředí zděděných z více zdrojů. Můžete definovat některé proměnné v souborech, jako je *CMakeSettings.json* nebo *CppProperties.json* a zpřístupnit je k ladění kontextu.  **Visual Studio 16.4:**: Zadejte proměnné prostředí na `env.VARIABLE_NAME` základě cíle pomocí syntaxe. Chcete-li zrušit nastavení proměnné, nastavte ji na hodnotu "null".|
|`args`|pole|Určuje argumenty příkazového řádku předané spuštěnému programu.|
|`currentDir`|řetězec|Určuje úplnou cestu k cíli sestavení. Tato možnost bude automaticky rozpoznána, pokud není tento parametr nastaven.|
|`noDebug`|Boolean|Určuje, zda má být spuštěný program ladit. Výchozí hodnota pro tento `false` parametr je, pokud není zadán.|
|`stopOnEntry`|Boolean|Určuje, zda má být proces přerušit, jakmile je proces spuštěn a ladicí program se připojí. Výchozí hodnota pro tento `false`parametr je .|
|`remoteMachine`|řetězec|Určuje název vzdáleného počítače, ve kterém je program spuštěn.|
|`env`|pole| Určuje seznam vlastních proměnných prostředí mezi klíči a hodnotami. env:{"myEnv":"myVal"}.|
|`portName`|řetězec|Určuje název portu při připojování ke spuštěnému procesu.|
|`buildConfigurations`|pole| Dvojice klíč hodnota, která určuje název režimu sestavení použít konfigurace. Například `Debug` nebo `Release` a konfigurace, které mají být používány podle vybraného režimu sestavení.

## <a name="c-linux-properties"></a>Vlastnosti C++ Linuxu

||||
|-|-|-|
|**Vlastnost**|**Typ**|**Popis**|
|`program`|řetězec|Úplná cesta ke spuštění programu ve vzdáleném počítači. Při použití CMake `${debugInfo.fullTargetPath}` lze makro použít jako hodnotu tohoto pole.|
|`processId`|celé číslo|Volitelné ID procesu pro připojení ladicího programu.|
|`sourceFileMap`|objekt|Volitelné mapování zdrojových souborů předáno ladicímu modulu. Formát: `{ "\<Compiler source location>": "\<Editor source location>" }` `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`nebo . Příklad: `{ "/home/user/foo": "C:\\foo" }` nebo `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Viz [Možnosti mapy zdrojového souboru](#source_file_map_options).|
|`additionalProperties`|řetězec|Jeden ze sourceFileMapOptions. (Viz níže.)|
|`MIMode`|řetězec|Označuje typ ladicího programu konzoly s podporou MI, ke kterému se připojí modul MIDebugEngine. Povolené hodnoty jsou "gdb", "lldb".|
|`args`|pole|Argumenty příkazového řádku předány programu.|
|`environment`|pole|Proměnné prostředí, které chcete přidat do prostředí pro program. Příklad: [ { "name": "squid", "value": "škeble" } ].|
|`targetArchitecture`|řetězec|Architektura ladění. Tato možnost bude automaticky rozpoznána, pokud není tento parametr nastaven. Povolené hodnoty jsou x86, arm, arm64, mips, x64, amd64, x86_64.|
|`visualizerFile`|řetězec|.natvis soubor, který má být použit při ladění tohoto procesu. Tato možnost není kompatibilní s GDB pěkný tisk. Viz "showDisplayString" při použití tohoto nastavení.|
|`showDisplayString`|Boolean|Když je zadán visualizerFile, showDisplayString povolí řetězec zobrazení. Zapnutí této možnosti může způsobit pomalejší výkon během ladění.|
|`remoteMachineName`|řetězec|Vzdálený počítač s Linuxem, který hostuje gdb a program pro ladění. Pro přidání nových počítačů s Linuxem použijte Správce připojení. Při použití CMake `${debugInfo.remoteMachineName}` lze makro použít jako hodnotu tohoto pole.|
|`cwd`|řetězec|Pracovní adresář cíle ve vzdáleném počítači. Při použití CMake `${debugInfo.defaultWorkingDirectory}` lze makro použít jako hodnotu tohoto pole. Výchozí hodnota je kořenový adresář vzdáleného pracovního prostoru, pokud není v souboru *CMakeLists.txt* přepsán.|
|`miDebuggerPath`|řetězec|Cesta k ladicímu programu s podporou MI (například gdb). Pokud není zadán, bude hledat PATH nejprve ladicí program.|
|`miDebuggerServerAddress`|řetězec|Síťová adresa ladicího serveru s podporou MI, ke kterému se chcete připojit. Příklad: localhost:1234.|
|`setupCommands`|pole|Jeden nebo více příkazů GDB/LLDB, které mají být provedeny za účelem nastavení základního ladicího programu. Příklad: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Viz [Příkazy pro nastavení spuštění](#launch_setup_commands).|
|`customLaunchSetupCommands`|pole|Pokud je k dispozici, nahradí výchozí příkazy používané ke spuštění cíle s některými dalšími příkazy. Například to může být "-target-attach" za účelem připojení k cílovému procesu. Prázdný seznam příkazů nahradí příkazy pro spuštění ničím, což může být užitečné, pokud je ladicímu programu poskytovány možnosti spuštění jako možnosti příkazového řádku. Příklad: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|řetězec|Příkaz, který má být proveden po úplném nastavení ladicího programu, způsobí spuštění cílového procesu. Povolené hodnoty jsou "exec-run", "exec-continue", "None". Výchozí hodnota je "exec-run".|
|`debugServerPath`|řetězec|Volitelná úplná cesta ke spuštění ladicího serveru. Výchozí hodnota je null.|
|`debugServerArgs`|řetězec|Volitelné ladění serveru args. Výchozí hodnota je null.|
|`filterStderr`|Boolean|Hledat stderr stream pro server-začal vzor a protokolu stderr ladit výstup. Výchozí hodnota `false`je na .|
|`coreDumpPath`|řetězec|Volitelná úplná cesta k souboru základního výpisu pro zadaný program. Výchozí hodnota je null.|
externalConsole|Boolean|Pokud true, konzole je spuštěnpro ladicí program. Pokud `false`není spuštěna žádná konzola. Výchozí hodnota `false`je na . Poznámka: Tato možnost je ignorována v některých případech z technických důvodů.|
|`pipeTransport`|řetězec|Pokud je k dispozici, to říká ladicí program pro připojení ke vzdálenému počítači pomocí jiného spustitelného souboru jako kanálu, který bude přenášet standardní vstup a výstup mezi Visual Studio a mi-dát ladicí program (například gdb). Povolené hodnoty: jedna nebo více [možností přenosu potrubí](#pipe_transport_options).|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a>Spustit příkazy nastavení

Používá se `setupCommands` s vlastností:

||||
|-|-|-|
|`text`|řetězec|Příkaz ladicího programu, který má být proveden.|
|`description`|řetězec|Volitelný popis příkazu.|
|`ignoreFailures`|Boolean|Pokud true, chyby z příkazu by měly být ignorovány. Výchozí hodnota `false`je na .|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a>Možnosti přenosu potrubí

Používá se `pipeTransport` s vlastností:

||||
|-|-|-|
|`pipeCwd`|řetězec|Plně kvalifikovaná cesta k pracovnímu adresáři pro program kanálu.|
|`pipeProgram`|řetězec|Plně kvalifikovaný příkaz kanálu k provedení.|
|`pipeArgs`|pole|Argumenty příkazového řádku předané programu kanálu pro konfiguraci připojení.|
|`debuggerPath`|řetězec|Úplná cesta k ladicímu programu v cílovém počítači, například /usr/bin/gdb.|
|`pipeEnv`|objekt|Proměnné prostředí předané programu kanálu.|
|`quoteArgs`|Boolean|Pokud jednotlivé argumenty obsahují znaky (například mezery nebo tabulátory), měly by být citovány? Pokud `false`již nebude automaticky citován příkaz ladicího programu. Výchozí je `true`.|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a>Možnosti mapy zdrojového souboru

Použití s `sourceFileMap` vlastností:

||||
|-|-|-|
|`editorPath`|řetězec|Umístění zdrojového kódu pro editor najít.|
|`useForBreakpoints`|Boolean|Při nastavování zarážek by mělo být použito toto mapování zdrojů. Pokud `false`se pro nastavení zarážek používá pouze název souboru a číslo řádku. Pokud `true`budou zarážky nastaveny s úplnou cestou k souboru a čísle řádku pouze při použití tohoto zdrojového mapování. V opačném případě bude při nastavování zarážek použit pouze název souboru a číslo řádku. Výchozí je `true`.|
