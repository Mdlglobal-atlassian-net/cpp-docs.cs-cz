---
title: Nasazení, spuštění a ladění projektu pro C++ Linux v aplikaci Visual Studio
description: Popisuje, jak zkompilovat, spustit a ladit kód na vzdáleném cíli v rámci projektu Linux C++ v aplikaci Visual Studio.
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: e68feab3a71cd5bb3f6b88eee52f0872ef4bb213
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077827"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Nasazení, spuštění a ladění projektu Linux

::: moniker range="vs-2015"

Podpora pro Linux je k dispozici v systému Visual Studio 2017 nebo novějším.

::: moniker-end

Po vytvoření projektu pro Linux C++ v aplikaci Visual Studio a připojení k projektu pomocí [Správce připojení pro Linux](connect-to-your-remote-linux-computer.md)můžete spustit a ladit projekt. Zkompilujete, spustíte a ladíte kód na vzdáleném cíli.

::: moniker range="vs-2019"

**Visual Studio 2019 verze 16,1** Pro ladění a sestavování můžete cílit na různé systémy Linux. Například můžete křížově kompilovat na platformě x64 a nasazovat je do zařízení ARM při cílení na scénáře IoT. Další informace najdete v tématu [určení různých počítačů pro sestavování a ladění](#separate_build_debug) dále v tomto článku.

::: moniker-end

Existuje několik způsobů, jak pracovat s projektem pro Linux a ladit ho.

- Proveďte ladění pomocí tradičních funkcí sady Visual Studio, jako jsou například zarážky, Sledujte okna a najeďte myší na proměnnou. Pomocí těchto metod se můžete ladit jako obvykle pro jiné typy projektů.

- Zobrazit výstup z cílového počítače v okně konzoly Linux. Můžete také použít konzolu k odeslání vstupu do cílového počítače.

## <a name="debug-your-linux-project"></a>Ladění projektu pro Linux

1. Na stránce vlastností **ladění** vyberte režim ladění.

   ::: moniker range="vs-2019"

   GDB se používá pro ladění aplikací běžících na Linux. Při ladění na vzdáleném systému (ne WSL) GDB může běžet ve dvou různých režimech, které lze vybrat z možnosti **režim ladění** na stránce vlastností **ladění** projektu:

   ![GDB možnosti](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB se používá pro ladění aplikací běžících na Linux. GDB lze spustit ve dvou různých režimech, které lze vybrat z možnosti **režim ladění** na stránce vlastností **ladění** projektu:

   ![GDB možnosti](media/vs2017-debugger-settings.png)

   ::: moniker-end

   - V režimu **gdbserver** se GDB spouští místně, který se připojuje k gdbserver na vzdáleném systému.  Všimněte si, že toto je jediný režim, který podporuje okno konzoly Linux.

   - V režimu **GDB** se na vzdáleném systému GDB ladicí program sady Visual Studio. Tato možnost je lepší, pokud místní verze GDB není kompatibilní s verzí nainstalovanou na cílovém počítači. |

   > [!NOTE]
   > Pokud nemůžete v režimu ladění gdbserver vysáhnout zarážky, vyzkoušejte režim GDB. GDB se musí nejdřív [nainstalovat](download-install-and-setup-the-linux-development-workload.md) na vzdálený cíl.

1. Vyberte vzdálený cíl pomocí panelu nástrojů Standardní **ladění** v sadě Visual Studio.

   Když je vzdálený cíl k dispozici, zobrazí se seznam podle názvu nebo IP adresy.

   ![Vzdálený cíl](media/remote_target.png)

   Pokud jste se ještě nepřipojili ke vzdálenému cíli, zobrazí se výzva k připojení ke vzdálenému cíli pomocí [Správce připojení pro Linux](connect-to-your-remote-linux-computer.md) .

   ![Vzdálená architektura](media/architecture.png)

1. Nastavte zarážku kliknutím na levé hřbety kódu, který se spustí.

   Na řádku kódu, kde jste nastavili zarážku, se zobrazí červená tečka.

1. Stisknutím klávesy **F5** (nebo **laděním > Spustit ladění**) spusťte ladění.

   Při spuštění ladění je aplikace kompilována na vzdáleném cíli před spuštěním. V okně **Seznam chyb** se zobrazí všechny chyby kompilace.

   Pokud nedojde k žádným chybám, aplikace se spustí a ladicí program se zastaví na zarážce.

   ![Stiskněte zarážku](media/hit_breakpoint.png)

   Nyní můžete s aplikací pracovat v jejím aktuálním stavu, zobrazit proměnné a krokovat kód stisknutím klávesových zkratek, jako je například **F10** nebo **F11**.

1. Pokud chcete používat konzolu Linux k interakci s vaší aplikací, vyberte **ladit > Linux Console**.

   ![Nabídka konzoly Linux](media/consolemenu.png)

   V této konzole se zobrazí všechny výstupy konzoly z cílového počítače a jejich převzetí vstupu a odeslání do cílového počítače.

   ![Okno konzoly pro Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-based-projects"></a>Konfigurace dalších možností ladění (projekty založené na MSBuild)

- Argumenty příkazového řádku lze předat spustitelnému souboru pomocí položky **argumenty programu** na stránce vlastností **ladění** projektu.

   ![Argumenty programu](media/settings_programarguments.png)

- Konkrétní možnosti ladicího programu lze předat do GDB pomocí položky **Další příkazy ladicího programu** .  Například můžete chtít ignorovat signály SIGILL (neplatné instrukce).  K tomuto účelu můžete použít příkaz **Handle** , a to tak, že do **dalšího příkazu ladicího programu** přidáte následující položku, jak je uvedeno výše:

   `handle SIGILL nostop noprint`

## <a name="configure-other-debugging-options-cmake-projects"></a>Konfigurace dalších možností ladění (projekty CMake)

V souboru Launch. vs. JSON můžete zadat další argumenty příkazového řádku pro projekt CMake. Další informace najdete v tématu [ladění projektu cmake](cmake-linux-project.md#debug_cmake_project)

## <a name="debug-with-attach-to-process"></a>Ladit pomocí příkazu připojit k procesu

Stránka vlastností [ladění](prop-pages/debugging-linux.md) pro projekty sady Visual Studio a nastavení **Launch. vs. JSON** pro projekty cmake má nastavení, které vám umožní připojit se k běžícímu procesu. Pokud požadujete další kontrolu nad rámec toho, co jsou v těchto nastaveních k dispozici, můžete soubor s názvem `Microsoft.MIEngine.Options.xml` umístit do kořenového adresáře vašeho řešení nebo pracovního prostoru. Tady je jednoduchý příklad:

```xml
<?xml version="1.0" encoding="utf-8"?>
<SupplementalLaunchOptions>
    <AttachOptions>
      <AttachOptionsForConnection AdditionalSOLibSearchPath="/home/user/solibs">
        <ServerOptions MIDebuggerPath="C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\Common7\IDE\VC\Linux\bin\gdb\7.9\x86_64-linux-gnu-gdb.exe"
ExePath="C:\temp\ConsoleApplication17\ConsoleApplication17\bin\x64\Debug\ConsoleApplication17.out"/>
        <SetupCommands>
          <Command IgnoreFailures="true">-enable-pretty-printing</Command>
        </SetupCommands>
      </AttachOptionsForConnection>
    </AttachOptions>
</SupplementalLaunchOptions>
```

**AttachOptionsForConnection** má většinu atributů, které možná budete potřebovat. Výše uvedený příklad ukazuje, jak určit umístění pro hledání dalších. knihovny. **ServerOptions** podřízených elementů umožňuje připojení ke vzdálenému procesu pomocí gdbserver místo toho. K tomu je potřeba zadat místního klienta GDB (ten, který je součástí sady Visual Studio 2017), a místní kopii binárního souboru se symboly. Element **SetupCommands** umožňuje předat příkazy přímo do GDB. Můžete najít všechny možnosti, které jsou k dispozici ve [schématu LaunchOptions. xsd](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) na GitHubu.

::: moniker range="vs-2019"

## <a name="specify-different-machines-for-building-and-debugging"></a><a name="separate_build_debug"></a>Určení různých počítačů pro sestavování a ladění

V sadě Visual Studio 2019 verze 16,1 můžete oddělit svůj vzdálený sestavovací počítač od vzdáleného ladicího počítače pro projekty Linux založené na MSBuild i pro projekty CMake, které cílí na vzdálený počítač se systémem Linux. Například můžete provést křížovou kompilaci na platformě x64 a nasadit ji do zařízení ARM při cílení na scénáře IoT.

### <a name="msbuild-based-projects"></a>Projekty založené na MSBuildu

Ve výchozím nastavení je vzdálený ladicí počítač stejný jako vzdálený sestavovací počítač (**konfigurační vlastnosti** > **Obecné** > **počítači vzdáleného sestavení**). Chcete-li určit nový vzdálený ladicí počítač, klikněte pravým tlačítkem myši na projekt v **Průzkumník řešení** a přejděte do části **Vlastnosti konfigurace** > **ladění** > **vzdáleném počítači ladění**.  

![Linux Remote Debug Machine](media/linux-remote-debug-machine.png)

Rozevírací nabídka pro **vzdálený ladicí počítač** se naplní všemi zavedenými vzdálenými připojeními. Chcete-li přidat nové vzdálené připojení, přejděte do části **nástroje** > **Možnosti** > pro **různé platformy** > **Správce připojení** nebo vyhledejte "Správce připojení" v části **Snadné spuštění**. Můžete také zadat nový adresář vzdáleného nasazení na stránkách vlastností projektu (**konfigurační vlastnosti** > **Obecné** > **adresáře vzdáleného nasazení**).

Ve výchozím nastavení budou do vzdáleného ladicího počítače nasazeny pouze soubory, které jsou nezbytné pro ladění procesu. Pomocí **Průzkumník řešení** můžete nakonfigurovat, které zdrojové soubory budou nasazeny do vzdáleného ladicího počítače. Po kliknutí na zdrojový soubor se zobrazí náhled vlastností souboru přímo pod Průzkumník řešení.

![Nasaditelné soubory pro Linux](media/linux-deployable-content.png)

Vlastnost **Content** určuje, zda bude soubor nasazen do vzdáleného ladicího počítače. Nasazení můžete zcela vypnout tak, že přejdete na **stránky vlastností** > **Configuration Manager** a zrušíte kontrolu **nasazení** pro požadovanou konfiguraci.

V některých případech můžete vyžadovat větší kontrolu nad nasazením projektu. Například některé soubory, které chcete nasadit, mohou být mimo vaše řešení nebo chcete přizpůsobit adresář vzdáleného nasazení na soubor ordirectory. V těchto případech přidejte následující bloky kódu do souboru. vcxproj a nahraďte "example. cpp" skutečnými názvy souborů:

```xml

<ItemGroup>
   <RemoteDeploy Include="__example.cpp">
<!-- This is the source Linux machine, can be empty if DeploymentType is LocalRemote -->
      <SourceMachine>$(RemoteTarget)</SourceMachine>
      <TargetMachine>$(RemoteDebuggingTarget)</TargetMachine>
      <SourcePath>~/example.cpp</SourcePath>
      <TargetPath>~/example.cpp</TargetPath>
<!-- DeploymentType can be LocalRemote, in which case SourceMachine will be empty and SourcePath is a local file on Windows -->
      <DeploymentType>RemoteRemote</DeploymentType>
<!-- Indicates whether the deployment contains executables -->
      <Executable>true</Executable>
   </RemoteDeploy>
</ItemGroup>
```

### <a name="cmake-projects"></a>Projekty CMake

U projektů CMake, které cílí na vzdálený počítač se systémem Linux, můžete zadat nový vzdálený ladicí počítač v programu Launch. vs. JSON. Ve výchozím nastavení je hodnota "remoteMachineName" synchronizována s vlastností "remoteMachineName" v CMakeSettings. JSON, která odpovídá vašemu vzdálenému sestavení počítače. Tyto vlastnosti již nemusí odpovídat a hodnota "remoteMachineName" v příkazu Launch. vs. JSON určí, který vzdálený počítač bude použit pro nasazení a ladění.

![Vzdálený ladicí počítač CMake](media/cmake-remote-debug-machine.png)

Technologie IntelliSense navrhne všechny navázané vzdálené připojení. Nové vzdálené připojení můžete přidat tak, že přejdete na **nástroje** > **Možnosti** > pro **různé platformy** > **Správce připojení** nebo ve **snadném spuštění**vyhledáte "Správce připojení".

Pokud chcete mít úplnou kontrolu nad vaším nasazením, můžete do souboru Launch. vs. JSON připojit následující bloky kódu. Nezapomeňte nahradit hodnoty zástupných symbolů skutečnými hodnotami:

```json

"disableDeploy": false,
"deployDirectory": "~\foo",
"deploy" : [
   {
      "sourceMachine": "127.0.0.1 (username=example1, port=22, authentication=Password)",
      "targetMachine": "192.0.0.1 (username=example2, port=22, authentication=Password)",
      "sourcePath": "~/example.cpp",
      "targetPath": "~/example.cpp",
      "executable": "false"
   }
]

```

::: moniker-end

## <a name="next-steps"></a>Další kroky

- Pokud chcete ladit zařízení ARM v systému Linux, přečtěte si tento Blogový příspěvek: [ladění vloženého zařízení ARM v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/).

## <a name="see-also"></a>Viz také

[C++Vlastnosti ladění (Linux C++)](prop-pages/debugging-linux.md)
