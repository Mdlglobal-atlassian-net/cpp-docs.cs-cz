---
title: Konfigurace relací ladění CMake v sadě Visual Studio
description: Popisuje, jak použít sadu Visual Studio ke konfiguraci nastavení ladicího programu CMake.
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: f860d1ae78d401a9e5079e79684a053220deaa6c
ms.sourcegitcommit: 3f91111c0350c0237fddb82766c290307f20e659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83630526"
---
# <a name="configure-cmake-debugging-sessions"></a>Konfigurace ladicích relací CMake

::: moniker range="vs-2015"

Nativní podpora CMake je k dispozici v sadě Visual Studio 2017 a novějších. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor **verzí** sady Visual Studio pro tento článek na sadu visual Studio 2017 nebo visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end

::: moniker range=">=vs-2017"

Všechny spustitelné cíle CMake se zobrazí v rozevíracím seznamu **spouštěcí položka** na panelu nástrojů **Obecné** . Vyberte jednu pro spuštění ladicí relace a spusťte ladicí program.

![Rozevírací seznam pro položku po spuštění CMake](media/cmake-startup-item-dropdown.png "Rozevírací seznam pro položku po spuštění CMake")

Můžete také spustit relaci ladění z Průzkumník řešení. Nejprve přepněte na **zobrazení cíle cmake** v okně **Průzkumník řešení** .

![Tlačítko zobrazení cílů CMake](media/cmake-targets-view.png  "Položka nabídky zobrazení cílů CMake")

Potom klikněte pravým tlačítkem na spustitelný soubor a vyberte **ladit**. Tento příkaz automaticky spustí ladění vybraného cíle na základě aktivní konfigurace.

## <a name="customize-debugger-settings"></a>Přizpůsobení nastavení ladicího programu

Nastavení ladicího programu můžete přizpůsobit pro libovolný spustitelný cíl CMake v projektu. Nacházejí se v konfiguračním souboru s názvem *Launch. vs. JSON*, který se nachází ve *`.vs`* složce v kořenu projektu. Konfigurační soubor spuštění je užitečný ve většině scénářů ladění, protože můžete nakonfigurovat a uložit podrobnosti nastavení ladění. Tento soubor obsahuje tři vstupní body:

- **Nabídka ladění:** Vyberte **ladit > nastavení ladění a spouštění pro $ {activeDebugTarget}** z hlavní nabídky pro přizpůsobení konfigurace ladění specifické pro váš aktivní ladění. Pokud nemáte vybraný cíl ladění, je tato možnost šedá.

![Vstupní bod nabídky ladění](media/cmake-debug-menu.png "Vstupní bod nabídky ladění")

- **Zobrazení cílů:** Přejděte do **zobrazení cíle** v Průzkumník řešení. Potom klikněte pravým tlačítkem na cíl ladění a vyberte **Přidat konfiguraci ladění** , abyste mohli přizpůsobit konfiguraci ladění specifickou pro vybraný cíl.

![Vstupní bod zobrazení cílů](media/cmake-targets-add-debug-configuration.png "Vstupní bod zobrazení cílů")

- **Kořenový CMakeLists. txt:** Klikněte pravým tlačítkem na kořen *CMakeLists. txt* a vyberte **Přidat konfiguraci ladění** . tím otevřete dialogové okno **Vybrat ladicí program** . V dialogovém okně můžete přidat *jakýkoli* typ konfigurace ladění, ale musíte ručně zadat cíl cmake, který se má vyvolat prostřednictvím `projectTarget` Vlastnosti.

![Dialogové okno pro výběr ladicího programu](media/cmake-select-a-debugger.png "Dialogové okno pro výběr ladicího programu")

Soubor *Launch. vs. JSON* můžete upravit tak, aby se vytvořily konfigurace ladění pro libovolný počet cílů cmake. Když soubor uložíte, Visual Studio vytvoří položku pro každou novou konfiguraci v rozevíracím seznamu **položky po spuštění** .

## <a name="reference-keys-in-cmakesettingsjson"></a>Referenční klíče v CMakeSettings. JSON

Chcete-li odkazovat na libovolný klíč v souboru *CMakeSettings. JSON* , `cmake.` Přihlaste se k němu v souboru *Launch. vs. JSON*. Následující příklad ukazuje jednoduchý soubor *Launch. vs. JSON* , který se načte do hodnoty `remoteCopySources` klíče v souboru *CMakeSettings. JSON* pro aktuálně vybranou konfiguraci:

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

**Proměnné prostředí** definované v *CMakeSettings. JSON* lze také použít v příkazu Launch. vs. JSON pomocí syntaxe `${env.VARIABLE_NAME}` . V aplikaci Visual Studio 2019 verze 16,4 a novější se cíle ladění automaticky spustí pomocí prostředí, které zadáte v *CMakeSettings. JSON*. Proměnnou prostředí lze zrušit nastavením na **hodnotu null**.

## <a name="launchvsjson-reference"></a>Odkaz Launch. vs. JSON

Pro podporu všech scénářů ladění existuje mnoho vlastností *Launch. vs. JSON* . Následující vlastnosti jsou společné pro všechny konfigurace ladění, vzdálené i místní:

- `projectTarget`: Určuje cíl CMake, který se má vyvolat při sestavování projektu. Sada Visual Studio automaticky vyplní tuto vlastnost, pokud zadáte *Launch. vs. JSON* z **nabídky ladění** nebo **zobrazení cílů**. Tato hodnota se musí shodovat s názvem existujícího cíle ladění, který je uvedený v rozevírací nabídce **položky po spuštění** .

- `env`: Další proměnné prostředí, které se mají přidat pomocí syntaxe:

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`: Argumenty příkazového řádku předané programu k ladění.

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>Odkaz Launch. vs. JSON pro vzdálené projekty a WSL

V aplikaci Visual Studio 2019 verze 16,6 jsme přidali novou konfiguraci ladění `type: cppgdb` pro zjednodušení ladění na vzdálených systémech a WSL. Staré konfigurace ladění pro `type: cppdbg` jsou stále podporovány.

### <a name="configuration-type-cppgdb"></a>Typ konfigurace`cppgdb`

- `name`: Popisný název, který identifikuje konfiguraci v rozevírací nabídce **položky po spuštění** .
- `project`: Určuje relativní cestu k souboru projektu. Obvykle není nutné měnit tuto cestu při ladění projektu CMake.
- `projectTarget`: Určuje cíl CMake, který se má vyvolat při sestavování projektu. Sada Visual Studio automaticky vyplní tuto vlastnost, pokud zadáte *Launch. vs. JSON* z **nabídky ladění** nebo **zobrazení cílů**. Tato cílová hodnota se musí shodovat s názvem existujícího cíle ladění, který je uvedený v rozevíracím seznamu **položky po spuštění** .
- `debuggerConfiguration`: Určuje, která sada výchozích hodnot ladění má být použita. V aplikaci Visual Studio 2019 verze 16,6 je jedinou platnou možností `gdb` . Visual Studio 2019 verze 16,7 nebo novější také podporuje `gdbserver` .
- `args`: Argumenty příkazového řádku předané při spuštění do laděného programu.
- `env`: Další proměnné prostředí předané programu, který se právě ladí. Například, `{"DISPLAY": "0.0"}`.
- `processID`: ID procesu Linux, ke kterému se má připojit. Používá se pouze při připojení ke vzdálenému procesu. Další informace najdete v tématu [řešení potíží s připojením k procesům pomocí GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

#### <a name="additional-options-for-the-gdb-configuration"></a>Další možnosti `gdb` Konfigurace

- `program`: Výchozí hodnota `"${debugInfo.fullTargetPath}"` . Cesta systému UNIX k aplikaci, která se má ladit Požadováno pouze v případě, že se liší od cílového spustitelného souboru v umístění Build nebo Deploy.
- `remoteMachineName`: Výchozí hodnota `"${debugInfo.remoteMachineName}"` . Název vzdáleného systému, který je hostitelem programu k ladění. Vyžaduje se pouze v případě, že se liší od sestavovacího systému. Musí mít existující položku ve [Správci připojení](../linux/connect-to-your-remote-linux-computer.md). Stisknutím **kombinace kláves CTRL + MEZERNÍK** zobrazíte seznam všech existujících vzdálených připojení.
- `cwd`: Výchozí hodnota `"${debugInfo.defaultWorkingDirectory}"` . Cesta systému UNIX k adresáři na vzdáleném systému, kde `program` je spuštěn. Adresář musí existovat.
- `gdbpath`: Výchozí hodnota `/usr/bin/gdb` . Úplná cesta k systému UNIX, která se má `gdb` použít k ladění. Vyžaduje se jenom v případě, že používáte vlastní verzi `gdb` .
- `preDebugCommand`: Příkaz pro Linux, který se spustí hned před vyvoláním `gdb` . `gdb`nespustí se, dokud se příkaz nedokončí. Tuto možnost můžete použít ke spuštění skriptu před spuštěním `gdb` .

#### <a name="additional-options-allowed-with-the-gdbserver-configuration-167-or-later"></a>Další možnosti povolené s `gdbserver` konfigurací (16,7 nebo novější)

- `program`: Výchozí hodnota `"${debugInfo.fullTargetPath}"` . Cesta systému UNIX k aplikaci, která se má ladit Požadováno pouze v případě, že se liší od cílového spustitelného souboru v umístění Build nebo Deploy.
- `remoteMachineName`: Výchozí hodnota `"${debugInfo.remoteMachineName}"` . Název vzdáleného systému, který je hostitelem programu k ladění. Vyžaduje se pouze v případě, že se liší od sestavovacího systému. Musí mít existující položku ve [Správci připojení](../linux/connect-to-your-remote-linux-computer.md). Stisknutím **kombinace kláves CTRL + MEZERNÍK** zobrazíte seznam všech existujících vzdálených připojení.
- `cwd`: Výchozí hodnota `"${debugInfo.defaultWorkingDirectory}"` . Úplná cesta systému UNIX k adresáři ve vzdáleném systému, ve kterém `program` je spuštěný. Adresář musí existovat.
- `gdbPath`: Výchozí hodnota `${debugInfo.vsInstalledGdb}` . Úplná cesta k systému Windows, která se má `gdb` použít k ladění. Ve výchozím nastavení se `gdb` instaluje s úlohou vývoj pro Linux s využitím úlohy C/C++.
- `gdbserverPath`: Výchozí hodnota `usr/bin/gdbserver` . Úplná cesta k systému UNIX, která se má `gdbserver` použít k ladění.
- `preDebugCommand`: Příkaz pro Linux, který se spustí hned před spuštěním `gdbserver` . `gdbserver`nespustí se, dokud se příkaz nedokončí.

#### <a name="deployment-options"></a>Možnosti nasazení

Použijte následující možnosti pro oddělení sestavovacího počítače (definovaného ve CMakeSettings. JSON) z počítače vzdáleného ladění.

- `remoteMachineName`: Vzdálený ladicí počítač. Vyžadováno pouze v případě, že se liší od sestavení počítače. Musí mít existující položku ve [Správci připojení](../linux/connect-to-your-remote-linux-computer.md). Stisknutím **kombinace kláves CTRL + MEZERNÍK** zobrazíte seznam všech existujících vzdálených připojení.
- `disableDeploy`: Výchozí hodnota `false` . Určuje, zda oddělení sestavení/ladění je zakázáno. Když `false` Tato možnost umožňuje sestavení a ladění, které se mají provádět na dvou samostatných počítačích.
- `deployDirectory`: Úplná cesta systému UNIX k adresáři `remoteMachineName` , na kterém se spustitelný soubor zkopíruje.
- `deploy`: Pole pokročilých nastavení nasazení. Tato nastavení je potřeba nakonfigurovat jenom v případě, že chcete mít přesnější kontrolu nad procesem nasazení. Ve výchozím nastavení jsou do vzdáleného ladicího počítače nasazeny pouze soubory, které jsou nezbytné pro proces ladění.
  - `sourceMachine`: Počítač, ze kterého se má zkopírovat soubor nebo adresář. Stisknutím **kombinace kláves CTRL + MEZERNÍK** zobrazíte seznam všech vzdálených připojení uložených ve Správci připojení. Při nativním sestavování na WSL je tato možnost ignorována.
  - `targetMachine`: Počítač, ke kterému se soubor nebo adresář kopíruje. Stisknutím **kombinace kláves CTRL + MEZERNÍK** zobrazíte seznam všech vzdálených připojení uložených ve Správci připojení.
  - `sourcePath`: Umístění souboru nebo adresáře na `sourceMachine` .
  - `targetPath`: Umístění souboru nebo adresáře na `targetMachine` .
  - `deploymentType`: Popis typu nasazení. `LocalRemote`a `RemoteRemote` jsou podporované. `LocalRemote`znamená kopírování z místního systému souborů do vzdáleného systému určeného `remoteMachineName` v souboru *Launch. vs. JSON*. `RemoteRemote`znamená kopírování ze vzdáleného sestavovacího systému zadaného v *CMakeSettings. JSON* do jiného vzdáleného systému zadaného v *Launch. vs. JSON*.
  - `executable`: Určuje, zda je nasazený soubor spustitelný.

### <a name="execute-custom-gdb-commands"></a>Spustit vlastní `gdb` příkazy

Visual Studio podporuje provádění vlastních `gdb` příkazů k interakci s podkladovým ladicím programem přímo. Další informace najdete v tématu [spouštění vlastních `gdb` příkazů lldb](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands).

### <a name="enable-logging"></a>Povolit protokolování

Povolením protokolování MIEngine zjistíte, které příkazy se odesílají do `gdb` , jaký výstup `gdb` vrátí a jak dlouho každý příkaz trvá. [Další informace](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>Typ konfigurace`cppdbg`

Následující možnosti lze použít při ladění na vzdáleném systému nebo WSL pomocí `cppdbg` typu konfigurace. V aplikaci Visual Studio 2019 verze 16,6 nebo novější se doporučuje typ konfigurace `cppgdb` .

- `name`: Popisný název, který identifikuje konfiguraci v rozevírací nabídce **položky po spuštění** .

- `project`: Určuje relativní cestu k souboru projektu. Za normálních okolností nemusíte při ladění projektu CMake tuto hodnotu měnit.

- `projectTarget`: Určuje cíl CMake, který se má vyvolat při sestavování projektu. Sada Visual Studio automaticky vyplní tuto vlastnost, pokud zadáte *Launch. vs. JSON* z **nabídky ladění** nebo **zobrazení cílů**. Tato hodnota se musí shodovat s názvem existujícího cíle ladění, který je uvedený v rozevírací nabídce **položky po spuštění** .

- `args`: Argumenty příkazového řádku předané při spuštění do laděného programu.

- `processID`: ID procesu Linux, ke kterému se má připojit. Používá se pouze při připojení ke vzdálenému procesu. Další informace najdete v tématu [řešení potíží s připojením k procesům pomocí GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

- `program`: Výchozí hodnota `"${debugInfo.fullTargetPath}"` . Cesta systému UNIX k aplikaci, která se má ladit Požadováno pouze v případě, že se liší od cílového spustitelného souboru v umístění Build nebo Deploy.

- `remoteMachineName`: Výchozí hodnota `"${debugInfo.remoteMachineName}"` . Název vzdáleného systému, který je hostitelem programu k ladění. Vyžaduje se pouze v případě, že se liší od sestavovacího systému. Musí mít existující položku ve [Správci připojení](../linux/connect-to-your-remote-linux-computer.md). Stisknutím **kombinace kláves CTRL + MEZERNÍK** zobrazíte seznam všech existujících vzdálených připojení.

- `cwd`: Výchozí hodnota `"${debugInfo.defaultWorkingDirectory}"` . Úplná cesta systému UNIX k adresáři ve vzdáleném systému, ve kterém `program` je spuštěný. Adresář musí existovat.

- `environment`: Další proměnné prostředí předané programu, který se právě ladí. Třeba

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

- `pipeArgs`: Pole argumentů příkazového řádku předané do programu kanálu ke konfiguraci připojení. Program kanálu slouží k přenosu standardního vstupu/výstupu mezi Visual Studio a `gdb` . Většinu tohoto pole **nemusíte** při ladění projektů cmake upravovat. Výjimkou je, že se `${debuggerCommand}` spouští `gdb` ve vzdáleném systému. Dá se upravit na:

  - Exportujte hodnotu zobrazení proměnné prostředí v systému Linux. V následujícím příkladu je tato hodnota `:1` .

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

  - Spusťte skript před spuštěním nástroje `gdb` . Ujistěte se, že jsou ve vašem skriptu nastavená oprávnění ke spuštění.

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

- `stopOnEntry`: Logická hodnota, která určuje, zda se má přerušit po spuštění procesu. Výchozí hodnotou je hodnota false.

- `visualizerFile`: [Soubor. Natvis](/visualstudio/debugger/create-custom-views-of-native-objects) , který se použije při ladění tohoto procesu. Tato možnost není kompatibilní s `gdb` poměrně tiskem. Nastaví `showDisplayString` se také při nastavení této vlastnosti.

- `showDisplayString`: Logická hodnota, která umožňuje zobrazovanému řetězci při `visualizerFile` zadání. Nastavení této možnosti na `true` může způsobit pomalejší výkon během ladění.

- `setupCommands`: Jeden nebo více `gdb` příkazů, které se mají provést, chcete-li nastavit základní ladicí program.

- `miDebuggerPath`: Úplná cesta k `gdb` . Je-li tento parametr zadán, aplikace Visual Studio nejprve vyhledá cestu k ladicímu programu.

- Nakonec lze použít také všechny možnosti nasazení definované pro `cppgdb` typ konfigurace `cppdbg` .

### <a name="debug-using-gdbserver"></a>Ladit pomocí`gdbserver`

Konfiguraci můžete nakonfigurovat tak, aby se mohla `cppdbg` ladit pomocí `gdbserver` . Další podrobnosti a ukázku konfigurace spuštění najdete v blogu týmu Microsoft C++ [ladění projektů `gdbserver` Linux cmake ](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Viz také

[Projekty CMake v sadě Visual Studio](cmake-projects-in-visual-studio.md)\
[Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)\
[Připojení ke vzdálenému počítači se systémem Linux](../linux/connect-to-your-remote-linux-computer.md)\
[Přizpůsobení nastavení sestavení CMake](customize-cmake-settings.md)\
[Konfigurace relací ladění CMake](configure-cmake-debugging-sessions.md)\
[Nasazení, spuštění a ladění projektu pro Linux](../linux/deploy-run-and-debug-your-linux-project.md)\
[Odkaz na předdefinovaný konfigurační odkaz CMake](cmake-predefined-configuration-reference.md)

::: moniker-end
