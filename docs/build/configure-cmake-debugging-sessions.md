---
title: Konfigurace relací ladění CMake v sadě Visual Studio
description: Popisuje, jak pomocí sady Visual Studio nakonfigurovat nastavení ladicího programu CMake.
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 8364e5b3dd3316a4ed7e754a104a14373040aa6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328807"
---
# <a name="configure-cmake-debugging-sessions"></a>Konfigurace ladicích relací CMake

::: moniker range="vs-2015"

Nativní podpora CMake je dostupná ve Visual Studiu 2017 a novějším. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end

::: moniker range=">=vs-2017"

Všechny spustitelné cíle CMake jsou zobrazeny v rozevíracím **seznamu Položka po spuštění** na panelu nástrojů **Obecné.** Vyberte jednu pro spuštění relace ladění a spusťte ladicí program.

![Rozevírací seznam položky po spuštění CMake](media/cmake-startup-item-dropdown.png "Rozevírací seznam položky po spuštění CMake")

Relaci ladění můžete také spustit z Průzkumníka řešení. Nejprve přepněte na **zobrazení cílů CMake** v okně **Průzkumník řešení.**

![Tlačítko zobrazení cílů CMake](media/cmake-targets-view.png  "CMake Cíle Zobrazit položku nabídky")

Potom klikněte pravým tlačítkem myši na spustitelný soubor a vyberte **možnost Ladění**. Tento příkaz automaticky spustí ladění vybraného cíle na základě aktivní konfigurace.

## <a name="customize-debugger-settings"></a>Přizpůsobení nastavení ladicího programu

Můžete přizpůsobit nastavení ladicího programu pro libovolný spustitelný cíl CMake v projektu. Nacházejí se v konfiguračním souboru s názvem *launch.vs.json*, který se nachází ve *`.vs`* složce v kořenovém adresáři projektu. Spouštěcí konfigurační soubor je užitečný ve většině scénářů ladění, protože můžete nakonfigurovat a uložit podrobnosti o nastavení ladění. Do tohoto souboru jsou tři vstupní body:

- **Nabídka ladění:** V hlavní nabídce vyberte **možnost Ladění > ladění a nastavení spuštění pro ${activeDebugTarget}** a přizpůsobte konfiguraci ladění specifickou pro aktivní cíl ladění. Pokud nemáte vybraný ladicí cíl, je tato možnost zobrazena šedě.

![Záznam nabídky ladění](media/cmake-debug-menu.png "Záznam nabídky ladění")

- **Zobrazení cílů:** Přejděte do **zobrazení cílů** v Průzkumníku řešení. Potom klikněte pravým tlačítkem myši na ladicí cíl a vyberte **přidat konfiguraci ladění** a přizpůsobte konfiguraci ladění specifickou pro vybraný cíl.

![Cíly pohled vstupní bod](media/cmake-targets-add-debug-configuration.png "Cíly pohled vstupní bod")

- **Kořen cmakelists.txt:** Klikněte pravým tlačítkem myši na kořenový *soubor CMakeLists.txt* a výběrem **možnosti Přidat konfiguraci ladění** otevřete dialogové okno **Vybrat ladicí program.** Dialogové okno umožňuje přidat *libovolný* typ konfigurace ladění, ale je nutné ručně zadat `projectTarget` cíl CMake vyvolat prostřednictvím vlastnosti.

![Výběr dialogového okna ladicího programu](media/cmake-select-a-debugger.png "Výběr dialogového okna ladicího programu")

Soubor *launch.vs.json* můžete upravit a vytvořit tak konfigurace ladění pro libovolný počet cílů CMake. Při uložení souboru visual studio vytvoří položku pro každou novou konfiguraci v rozevíracím **seznamu Položka po spuštění.**

## <a name="reference-keys-in-cmakesettingsjson"></a>Referenční klávesy v souboru CMakeSettings.json

Chcete-li odkazovat na libovolný klíč v souboru `cmake.` *CMakeSettings.json,* předchlazte jej v *launch.vs.json*. Následující příklad ukazuje jednoduchý soubor *launch.vs.json,* který získává `remoteCopySources` hodnotu klíče v souboru *CMakeSettings.json* pro aktuálně vybranou konfiguraci:

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

**Proměnné prostředí** definované v *souboru CMakeSettings.json* lze také použít v souboru launch.vs.json pomocí syntaxe `${env.VARIABLE_NAME}`. Ve Visual Studiu 2019 verze 16.4 a novější ladění cíle jsou automaticky spuštěny pomocí prostředí, které zadáte v *CMakeSettings.json*. Proměnnou prostředí můžete zrušit nastavením na **hodnotu null**.

## <a name="launchvsjson-reference"></a>Odkaz launch.vs.json

Existuje mnoho vlastností *launch.vs.json* pro podporu všech scénářů ladění. Následující vlastnosti jsou společné pro všechny konfigurace ladění, vzdálené i místní:

- `projectTarget`: Určuje cíl CMake, který má být vyvolán při vytváření projektu. Visual Studio automaticky naplní tuto vlastnost, pokud zadáte *launch.vs.json* z **nabídky ladění** nebo **cíle zobrazení**. Tato hodnota se musí shodovat s názvem existujícího cíle ladění uvedeného v rozevíracím seznamu **Položka po spuštění.**

- `env`: Další proměnné prostředí, které chcete přidat pomocí syntaxe:

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`: Argumenty příkazového řádku předané programu k ladění.

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>Reference Launch.vs.json pro vzdálené projekty a WSL

Ve Visual Studiu 2019 verze 16.6 jsme přidali novou konfiguraci ladění `type: cppgdb` pro zjednodušení ladění ve vzdálených systémech a WSL. Staré konfigurace ladění `type: cppdbg` jsou stále podporovány.

### <a name="configuration-type-cppgdb"></a>Typ konfigurace`cppgdb`

- `name`: Popisný název pro identifikaci konfigurace v rozevíracím seznamu **Položka po spuštění.**
- `project`: Určuje relativní cestu k souboru projektu. Za normálních okolností není nutné změnit tuto cestu při ladění projektu CMake.
- `projectTarget`: Určuje cíl CMake, který má být vyvolán při vytváření projektu. Visual Studio automaticky naplní tuto vlastnost, pokud zadáte *launch.vs.json* z **nabídky ladění** nebo **cíle zobrazení**. Tato cílová hodnota se musí shodovat s názvem existujícího cíle ladění uvedeného v rozevíracím seznamu **Položka po spuštění.**
- `debuggerConfiguration`: Označuje, která sada ladění výchozích hodnot použít. Ve Visual Studiu 2019 verze 16.6 `gdb`je jedinou platnou možností . Podporují také dřívější `gdbserver`verze .
- `args`: Argumenty příkazového řádku předané při spuštění laděné programu.
- `env`: Další proměnné prostředí předané laděné programu. Například, `{"DISPLAY": "0.0"}`.
- `processID`: Linux process ID připojit. Používá se pouze při připojování ke vzdálenému procesu. Další informace naleznete [v tématu Poradce při potížích s připojením k procesům pomocí gdb](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

#### <a name="additional-options-for-the-gdb-configuration"></a>Další možnosti `gdb` konfigurace

- `program`: Výchozí `"${debugInfo.fullTargetPath}"`nastavení je . Unixová cesta k aplikaci k ladění. Povinné pouze v případě, že se liší od cílového spustitelného souboru v umístění sestavení nebo nasazení.
- `remoteMachineName`: Výchozí `"${debugInfo.remoteMachineName}"`nastavení je . Název vzdáleného systému, který je hostitelem programu ladění. Vyžadováno pouze v případě, že se liší od systému sestavení. Musí mít existující položku ve Správci [připojení](../linux/connect-to-your-remote-linux-computer.md). Stisknutím **kombinace kláves Ctrl+Mezera** zobrazíte seznam všech existujících vzdálených připojení.
- `cwd`: Výchozí `"${debugInfo.defaultWorkingDirectory}"`nastavení je . Unixová cesta k adresáři ve `program` vzdáleném systému, kde je spuštěn. Adresář musí existovat.
- `gdbpath`: Výchozí `/usr/bin/gdb`nastavení je . Úplná unixová `gdb` cesta k použitému ladění. Povinné pouze v případě, `gdb`že používáte vlastní verzi aplikace .
- `preDebugCommand`: Linux příkaz ke spuštění bezprostředně `gdb`před vyvolání . `gdb`nespustí, dokud příkaz nedokončí. Tuto možnost můžete použít ke spuštění skriptu před spuštěním služby `gdb`.

#### <a name="deployment-options"></a>Možnosti nasazení

Pomocí následujících možností oddělte počítač sestavení (definovaný v souboru CMakeSettings.json) od vzdáleného ladicího počítače.

- `remoteMachineName`: Vzdálený ladicí stroj. Vyžadováno pouze v případě, že se liší od sestavení počítače. Musí mít existující položku ve Správci [připojení](../linux/connect-to-your-remote-linux-computer.md). Stisknutím **kombinace kláves Ctrl+Mezera** zobrazíte seznam všech existujících vzdálených připojení.
- `disableDeploy`: Výchozí `false`nastavení je . Označuje, zda je zakázáno oddělení sestavení nebo ladění. Když `false`tato možnost umožňuje sestavení a ladění dojít na dvou samostatných počítačích.
- `deployDirectory`: Úplná unixová `remoteMachineName` cesta do adresáře, do kterého se spustitelný soubor zkopíruje.
- `deploy`: Pole pokročilých nastavení nasazení. Tato nastavení je třeba nakonfigurovat pouze v případě, že chcete podrobnější kontrolu nad procesem nasazení. Ve výchozím nastavení se do vzdáleného ladicího počítače nasazují pouze soubory nezbytné k ladění procesu.
  - `sourceMachine`: Počítač, ze kterého je soubor nebo adresář zkopírován. Stisknutím **kombinace kláves Ctrl+Mezera** zobrazíte seznam všech vzdálených připojení uložených ve Správci připojení. Při vytváření nativně na WSL, tato možnost je ignorována.
  - `targetMachine`: Počítač, do kterého je soubor nebo adresář zkopírován. Stisknutím **kombinace kláves Ctrl+Mezera** zobrazíte seznam všech vzdálených připojení uložených ve Správci připojení.
  - `sourcePath`: Umístění souboru `sourceMachine`nebo adresáře na .
  - `targetPath`: Umístění souboru `targetMachine`nebo adresáře na .
  - `deploymentType`: Popis typu nasazení. `LocalRemote`a `RemoteRemote` jsou podporovány. `LocalRemote`znamená kopírování z místního systému souborů `remoteMachineName` do vzdáleného systému určeného v *launch.vs.json*. `RemoteRemote`znamená kopírování ze vzdáleného systému sestavení určeného v *souboru CMakeSettings.json* do jiného vzdáleného systému určeného v *souboru launch.vs.json*.
  - `executable`: Označuje, zda je nasazený soubor spustitelný soubor.

### <a name="execute-custom-gdb-commands"></a>Spuštění `gdb` vlastních příkazů

Visual Studio podporuje `gdb` provádění vlastních příkazů pro přímou interakci s základním ladicím programem. Další informace naleznete [v `gdb` tématu Provádění vlastních příkazů lldb](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands).

### <a name="enable-logging"></a>Povolit protokolování

Povolte protokolování MIEngine, abyste `gdb`zjistili, `gdb` jaké příkazy jsou odesílány , jaký výstup se vrací a jak dlouho trvá každý příkaz. [Další informace](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>Typ konfigurace`cppdbg`

Následující možnosti lze použít při ladění ve vzdáleném systému `cppdbg` nebo WSL pomocí typu konfigurace. Ve Visual Studiu 2019 verze 16.6 `cppgdb` nebo novější typ konfigurace se doporučuje.

- `name`: Popisný název pro identifikaci konfigurace v rozevíracím seznamu **Položka po spuštění.**

- `project`: Určuje relativní cestu k souboru projektu. Za normálních okolností není nutné změnit tuto hodnotu při ladění projektu CMake.

- `projectTarget`: Určuje cíl CMake, který má být vyvolán při vytváření projektu. Visual Studio automaticky naplní tuto vlastnost, pokud zadáte *launch.vs.json* z **nabídky ladění** nebo **cíle zobrazení**. Tato hodnota se musí shodovat s názvem existujícího cíle ladění uvedeného v rozevíracím seznamu **Položka po spuštění.**

- `args`: Argumenty příkazového řádku předané při spuštění laděné programu.

- `processID`: Linux process ID připojit. Používá se pouze při připojování ke vzdálenému procesu. Další informace naleznete [v tématu Poradce při potížích s připojením k procesům pomocí gdb](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

- `program`: Výchozí `"${debugInfo.fullTargetPath}"`nastavení je . Unixová cesta k aplikaci k ladění. Povinné pouze v případě, že se liší od cílového spustitelného souboru v umístění sestavení nebo nasazení.

- `remoteMachineName`: Výchozí `"${debugInfo.remoteMachineName}"`nastavení je . Název vzdáleného systému, který je hostitelem programu ladění. Vyžadováno pouze v případě, že se liší od systému sestavení. Musí mít existující položku ve Správci [připojení](../linux/connect-to-your-remote-linux-computer.md). Stisknutím **kombinace kláves Ctrl+Mezera** zobrazíte seznam všech existujících vzdálených připojení.

- `cwd`: Výchozí `"${debugInfo.defaultWorkingDirectory}"`nastavení je . Úplná unixová cesta do adresáře ve vzdáleném systému, kde `program` je spuštěn. Adresář musí existovat.

- `environment`: Další proměnné prostředí předané laděné programu. Například:

  ```json
    "environment": [
        {
          "name": "ENV1",
          "value": "envvalue1"
        },
        {
          "name": "ENV2",
          "value": "envvalue2"
        }
      ]
  ```

- `pipeArgs`: Pole argumentů příkazového řádku předaných programem kanálu pro konfiguraci připojení. Program kanálu se používá k přenosu standardního `gdb`vstupu a výstupu mezi visual studio a . Většina tohoto pole **není nutné přizpůsobit** při ladění projektů CMake. Výjimkou je `${debuggerCommand}`, která `gdb` se spustí ve vzdáleném systému. Může být upraven tak, aby:

  - Exportujte hodnotu proměnné prostředí DISPLAY do systému Linux. V následujícím příkladu je `:1`tato hodnota .

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "export DISPLAY=:1;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

  - Spusťte skript před `gdb`spuštěním služby . Ujistěte se, že jsou ve skriptu nastavena oprávnění ke spuštění.

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "/path/to/script.sh;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

- `stopOnEntry`: Logická hodnota, která určuje, zda má být proces po spuštění spuštěn. Výchozí hodnotou je hodnota false.

- `visualizerFile`: Soubor [Natvis,](/visualstudio/debugger/create-custom-views-of-native-objects) který se má použít při ladění tohoto procesu. Tato možnost je `gdb` nekompatibilní s pěkným tiskem. Nastavte `showDisplayString` také při nastavení této vlastnosti.

- `showDisplayString`: Logická hodnota, která umožňuje `visualizerFile` řetězec zobrazení, pokud je zadán. Nastavení této `true` možnosti může způsobit pomalejší výkon během ladění.

- `setupCommands`: Jeden `gdb` nebo více příkazů ke spuštění, nastavení základníladicí program.

- `miDebuggerPath`: Úplná `gdb`cesta k . Pokud není zadán, Visual Studio hledá cestu nejprve pro ladicí program.

- Nakonec všechny možnosti nasazení definované `cppgdb` pro typ konfigurace `cppdbg` lze použít také typ konfigurace.

### <a name="debug-using-gdbserver"></a>Ladění pomocí`gdbserver`

Konfiguraci `cppdbg` můžete nakonfigurovat tak, aby byla ladit pomocí `gdbserver`aplikace . Další podrobnosti a ukázkovou konfiguraci spuštění najdete v příspěvku blogu Microsoft C++ Team Blog [ladění linuxových projektů CMake s `gdbserver` ](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Viz také

[CMake projekty v sadě Visual Studio](cmake-projects-in-visual-studio.md)\
[Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)\
[Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)\
[Přizpůsobení nastavení sestavení CMake](customize-cmake-settings.md)\
[Konfigurace relací ladění CMake](configure-cmake-debugging-sessions.md)\
[Nasazení, spuštění a ladění projektu Linuxu](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake předdefinovaný odkaz na konfiguraci](cmake-predefined-configuration-reference.md)

::: moniker-end
