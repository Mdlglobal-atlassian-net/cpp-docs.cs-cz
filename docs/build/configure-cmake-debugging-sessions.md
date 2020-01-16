---
title: Konfigurace relací ladění CMake v sadě Visual Studio
description: Popisuje, jak použít Visual Studio ke konfiguraci nastavení ladicího programu CMake.
ms.date: 01/13/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 5e627f02b5245baede6e92268cedfc43957f3abc
ms.sourcegitcommit: 49e4fb3e0300fe86c814130661f1bf68b16e72e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "76031335"
---
# <a name="configure-cmake-debugging-sessions"></a>Konfigurace ladicích relací CMake

::: moniker range="vs-2015"

Nativní podpora CMake je k dispozici v sadě Visual Studio 2017 a novějších.

::: moniker-end

::: moniker range=">=vs-2017"

Všechny spustitelné cíle CMake se zobrazí v rozevíracím seznamu **spouštěcí položka** na panelu nástrojů **Obecné** . Chcete-li spustit relaci ladění, stačí vybrat jednu a spustit ladicí program.

![Rozevírací seznam pro položku po spuštění CMake](media/cmake-startup-item-dropdown.png "Rozevírací seznam pro položku po spuštění CMake")

Můžete také spustit relaci ladění z Průzkumník řešení. Nejprve přepněte na **zobrazení cíle cmake** v okně **Průzkumník řešení** .

![Tlačítko zobrazení cílů CMake](media/cmake-targets-view.png  "Položka nabídky zobrazení cílů CMake")

Potom klikněte pravým tlačítkem na jakýkoli spustitelný soubor a vyberte **ladit** nebo **ladit a spustit nastavení**. **Ladění** automaticky spustí ladění vybraného cíle na základě aktivní konfigurace. **Nastavení ladění a spouštění** otevře soubor *Launch. vs. JSON* a přidá novou konfiguraci ladění pro vybraný cíl.

## <a name="customize-debugger-settings"></a>Přizpůsobení nastavení ladicího programu

Nastavení ladicího programu můžete přizpůsobit pro libovolný spustitelný cíl CMake v projektu v souboru s názvem *Launch. vs. JSON*. Tento soubor obsahuje tři vstupní body:

- Chcete-li upravit konfiguraci ladění specifickou pro svůj aktivní cíl ladění, vyberte možnost **ladit > nastavení ladění a spouštění pro $ {activeDebugTarget}** v hlavní nabídce. Pokud nemáte vybraný aktivní cíl, tato možnost bude šedá.

- Přejděte do **zobrazení cíle** v Průzkumník řešení. Potom klikněte pravým tlačítkem na cíl ladění a vyberte **nastavení ladění a spouštění** , abyste mohli upravit konfiguraci ladění specifickou pro vybraný cíl.

- Klikněte pravým tlačítkem na kořenový CMakeLists. txt a vyberte **nastavení ladění a spuštění** , aby se otevřelo dialogové okno **Vybrat ladicí program** . V dialogovém okně můžete přidat konfiguraci ladění, ale musíte ručně zadat cíl CMake, který se má vyvolat prostřednictvím vlastnosti `projectTarget`.

Chcete-li odkazovat na libovolný klíč v souboru *CMakeSettings. JSON* , před ním `cmake.` v souboru *Launch. vs. JSON*. Následující příklad ukazuje jednoduchý soubor *Launch. vs. JSON* , který se načte do hodnoty `remoteCopySources` klíč v souboru *CMakeSettings. JSON* pro aktuálně vybranou konfiguraci:

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

Při uložení souboru *Launch. vs. JSON* sada Visual Studio vytvoří v rozevíracím seznamu **spouštěcí položky** položku pro nový název. Soubor *Launch. vs. JSON* můžete upravit tak, aby bylo možné vytvořit více konfigurací ladění pro libovolný počet cílů cmake.

## <a name="launchvsjson-reference"></a>Odkaz Launch. vs. JSON

Pro podporu všech scénářů ladění existuje mnoho vlastností *Launch. vs. JSON* . Následující vlastnosti jsou společné pro všechny konfigurace ladění, vzdálené i místní:

- `projectTarget`: Určuje cíl CMake, který se má vyvolat při sestavování projektu. Sada Visual Studio automaticky vyplní tuto vlastnost, pokud zadáte *Launch. vs. JSON* z **ladění > nastavení ladění a spuštění pro zobrazení $ {ActiveDebugTarget}** nebo **cíle**.

- `program`: úplná cesta ke spustitelnému souboru programu ve vzdáleném systému. `${debugInfo.fullTargetPath}` sem můžete použít makro.

- `args`: argumenty příkazového řádku předané programu k ladění.

## <a name="launchvsjson-reference-for-remote-linux-projects"></a>Odkaz Launch. vs. JSON pro vzdálené projekty Linux

Následující vlastnosti jsou specifické pro **vzdálené konfigurace ladění**. Můžete také [Spustit vlastní příkazy GDB](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands) k posílání příkazů přímo do podkladového ladicího programu a [Povolit protokolování MIEngine](https://github.com/microsoft/MIEngine/wiki/Logging) pro zobrazení příkazů, které se odesílají do GDB, jaký výstup GDB vrátí a jak dlouho jednotlivé příkazy trvají.

- `cwd`: aktuální pracovní adresář pro hledání závislostí a dalších souborů na vzdáleném počítači. Makro `${debugInfo.defaultWorkingDirectory}` lze použít. Výchozí hodnota je kořenový adresář vzdáleného pracovního prostoru, pokud není přepsán v *CMakeLists. txt*. Tato vlastnost se používá pouze pro vzdálené konfigurace. `currentDir` slouží k nastavení aktuálního adresáře spouštěné aplikace pro místní projekt.

- `environment`: další proměnné prostředí, které se mají přidat do prostředí pro program s touto syntaxí:

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

- `pipeArgs`: argumenty příkazového řádku předané programu kanálu ke konfiguraci připojení. K přenosu standardního vstupu/výstupu mezi Visual Studio a GDB se používá program kanálu. Příkaz `${debuggerCommand}` spustí GDB ve vzdáleném systému a dá se upravit na:

  - Exportujte hodnotu zobrazení proměnné prostředí v systému Linux. V následujícím příkladu je tato hodnota `:1`.

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

  - Před spuštěním GDB spusťte skript. Ujistěte se, že jsou ve vašem skriptu nastavená oprávnění ke spuštění.

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

- `stopOnEntry`: logická hodnota, která určuje, zda se má po spuštění procesu přerušit. Výchozí hodnota je false.

- `visualizerFile`: [soubor. Natvis](/visualstudio/debugger/create-custom-views-of-native-objects) , který se má použít při ladění tohoto procesu. Tato možnost není kompatibilní s tiskem gdb s poměrně. Nastavte také `showDisplayString` při nastavení této vlastnosti.

- `showDisplayString`: logická hodnota, která povoluje řetězec zobrazení, když je zadána `visualizerFile`. Nastavení této možnosti na `true` může způsobit pomalejší výkon během ladění.

- `setupCommands`: jeden nebo více příkazů gdb, které mají být spuštěny, pro nastavení základního ladicího programu.

- `externalConsole`: logická hodnota, která určuje, zda je pro laděného procesu spuštěna konzola.

- `miDebuggerPath`: úplná cesta k GDB. Je-li tento parametr zadán, aplikace Visual Studio nejprve vyhledá cestu k ladicímu programu.

::: moniker-end

::: moniker range="vs-2017"

- `remoteMachineName`: vzdálený systém Linux, který je hostitelem nástroje GDB a programu, který se má ladit.

::: moniker-end

::: moniker range="vs-2019"

Následující vlastnosti lze použít k oddělení **vzdáleného sestavovacího systému** od **vzdáleného ladicího systému**. Další informace najdete v tématu [určení různých počítačů pro sestavování a ladění](../linux/deploy-run-and-debug-your-linux-project.md#cmake-projects).

- `remoteMachineName`: vzdálený systém Linux, který je hostitelem nástroje GDB a programu, který se má ladit. Tato položka nemusí odpovídat vzdálenému systému Linux použitému pro sestavení zadané v *CMakeSettings. JSON*. Stisknutím **kombinace kláves CTRL + MEZERNÍK** zobrazíte seznam všech vzdálených připojení uložených ve [Správci připojení](../linux/connect-to-your-remote-linux-computer.md).

- `disableDeploy`: Určuje, zda je oddělení sestavení/ladění zakázáno. Pokud je tato funkce povolená, umožňuje sestavení a ladění výskytu na dvou samostatných počítačích.

- `deployDirectory`: adresář na vzdáleném ladicím počítači (určeném `remoteMachineName`), do kterého se bude spustitelný soubor zkopírovat.

- `deploy`: pole pokročilých nastavení nasazení. Tato nastavení je potřeba nakonfigurovat jenom v případě, že chcete mít přesnější kontrolu nad procesem nasazení. Ve výchozím nastavení budou do vzdáleného ladicího počítače nasazeny pouze soubory, které jsou nezbytné pro ladění procesu.

  - `sourceMachine`: počítač, ze kterého se bude kopírovat soubor nebo adresář. Stisknutím **kombinace kláves CTRL + MEZERNÍK** zobrazíte seznam všech vzdálených připojení uložených ve Správci připojení.

  - `targetMachine`: počítač, do kterého se má zkopírovat soubor nebo adresář. Stisknutím **kombinace kláves CTRL + MEZERNÍK** zobrazíte seznam všech vzdálených připojení uložených ve Správci připojení.

  - `sourcePath`: umístění souboru nebo adresáře v `sourceMachine`.

  - `targetPath`: umístění souboru nebo adresáře v `targetMachine`.

  - `deploymentType`: popis typu nasazení. jsou podporovány `LocalRemote` a `RemoteRemote`. `LocalRemote` znamená kopírování z místního systému souborů do vzdáleného systému zadaného `remoteMachineName` v souboru *Launch. vs. JSON*. `RemoteRemote` znamená kopírování ze vzdáleného sestavovacího systému zadaného v *CMakeSettings. JSON* do jiného vzdáleného systému zadaného v *Launch. vs. JSON*.

  - `executable`: Určuje, zda je nasazený soubor spustitelný.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="attach-to-a-remote-process"></a>Připojit ke vzdálenému procesu

K procesu spuštěnému v systému Linux se můžete připojit nastavením `processId` k ID procesu, ke kterému se má ladicí program připojit. Další informace najdete v tématu [řešení potíží s připojením k procesům pomocí GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

::: moniker-end

::: moniker range="vs-2019"

## <a name="debug-on-linux-using-gdbserver"></a>Ladění v systému Linux pomocí gdbserver

Visual Studio 2019 verze 16,5 Preview 1 nebo novější podporuje vzdálené ladění projektů CMake pomocí gdbserver. Další informace najdete v tématu [ladění projektů pro Linux cmake pomocí gdbserver](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Viz také:

[Projekty cmake v sadě Visual Studio](cmake-projects-in-visual-studio.md)\
[Konfigurace projektu Linux cmake](../linux/cmake-linux-project.md)\
[Připojte se ke vzdálenému počítači se systémem Linux](../linux/connect-to-your-remote-linux-computer.md)\
[Přizpůsobení nastavení buildu cmake](customize-cmake-settings.md)\
[Konfigurace relací ladění cmake](configure-cmake-debugging-sessions.md)\
[Nasazení, spuštění a ladění projektu pro Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Odkaz na předdefinovaný konfigurační odkaz CMake](cmake-predefined-configuration-reference.md)

::: moniker-end
