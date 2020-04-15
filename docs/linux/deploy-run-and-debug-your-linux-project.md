---
title: Nasazení, spuštění a ladění projektu C++ Linux v sadě Visual Studio
description: Popisuje, jak zkompilovat, spustit a ladit kód na vzdálený cíl z uvnitř projektu Linux C++ v sadě Visual Studio.
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: e68feab3a71cd5bb3f6b88eee52f0872ef4bb213
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "80077827"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Nasazení, spuštění a ladění projektu Linux

::: moniker range="vs-2015"

Podpora Linuxu je dostupná ve Visual Studiu 2017 a novějším.

::: moniker-end

Jakmile jste vytvořili linuxový c++ projekt v sadě Visual Studio a připojili jste se k projektu pomocí [Správce připojení k Linuxu](connect-to-your-remote-linux-computer.md), můžete spustit a ladit projekt. Zkompilovat, spustit a ladit kód na vzdálený cíl.

::: moniker range="vs-2019"

**Visual Studio 2019 verze 16.1** Můžete cílit na různé linuxové systémy pro ladění a vytváření. Můžete například křížově zkompilovat na x64 a nasadit na zařízení ARM při cílení na scénáře IoT. Další informace naleznete [v tématu Určení různých počítačů pro vytváření a ladění](#separate_build_debug) dále v tomto článku.

::: moniker-end

Existuje několik způsobů, jak pracovat s projektem Linuxu a ladit je.

- Ladění pomocí tradičních funkcí sady Visual Studio, jako jsou zarážky, okna sledování a najetím ukazatele na proměnnou. Pomocí těchto metod můžete ladit jako obvykle pro jiné typy projektů.

- Zobrazení výstupu z cílového počítače v okně konzoly Linux. Konzolu můžete také použít k odeslání vstupu do cílového počítače.

## <a name="debug-your-linux-project"></a>Ladění projektu Linux

1. Na stránce vlastností **Ladění** vyberte režim ladění.

   ::: moniker range="vs-2019"

   GDB se používá k ladění aplikací běžících na Linuxu. Při ladění na vzdáleném systému (ne WSL) GDB lze spustit ve dvou různých režimech, které lze vybrat z **možnosti režimladění** na stránce **vlastnosti ladění** projektu:

   ![Možnosti GDB](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB se používá k ladění aplikací běžících na Linuxu. GDB lze spustit ve dvou různých režimech, které lze vybrat z **možnosti režimladění** na stránce **vlastnosti ladění** projektu:

   ![Možnosti GDB](media/vs2017-debugger-settings.png)

   ::: moniker-end

   - V režimu **gdbserver** je GDB spuštěn lokálně, který se připojuje ke gdbserveru ve vzdáleném systému.  Všimněte si, že se jedná o jediný režim, který podporuje okno konzoly Linux.

   - V režimu **gdb** ladicí program sady Visual Studio řídí GDB ve vzdáleném systému. To je lepší možnost, pokud místní verze GDB není kompatibilní s verzí nainstalovanou v cílovém počítači. |

   > [!NOTE]
   > Pokud se vám nedaří schytat zarážky v režimu ladění gdbserver, zkuste režim gdb. gdb musí být [nejprve nainstalován](download-install-and-setup-the-linux-development-workload.md) na vzdáleném cíli.

1. Vyberte vzdálený cíl pomocí standardního **panelu** nástrojů ladění v sadě Visual Studio.

   Když je vzdálený cíl k dispozici, zobrazí se v seznamu s názvem nebo IP adresou.

   ![Vzdálený cíl](media/remote_target.png)

   Pokud jste se ještě nepřipojili ke vzdálenému cíli, zobrazí se pokyn k připojení ke vzdálenému cíli pomocí [Správce připojení k Linuxu.](connect-to-your-remote-linux-computer.md)

   ![Vzdálená architektura](media/architecture.png)

1. Nastavte zarážku kliknutím v levém kanálu některého kódu, o kterém víte, že se spustí.

   Na řádku kódu, kde nastavíte zarážku, se zobrazí červená tečka.

1. Stisknutím **klávesy F5** (nebo **ladění > spuštění ladění**) spusťte ladění.

   Když začnete ladění, aplikace je zkompilován na vzdálený cíl před jeho spuštěním. Všechny chyby kompilace se zobrazí v okně **Seznam chyb.**

   Pokud nejsou žádné chyby, aplikace se spustí a ladicí program se pozastaví na zarážky.

   ![Zásah do zarážky](media/hit_breakpoint.png)

   Nyní můžete pracovat s aplikací v aktuálním stavu, zobrazit proměnné a krokovat kód stisknutím příkazových kláves, jako je **F10** nebo **F11**.

1. Pokud chcete používat konzolu Linux k interakci s vaší aplikací, vyberte **Ladění > Linux Console**.

   ![Nabídka konzoly Linux](media/consolemenu.png)

   Tato konzola zobrazí veškerý výstup konzoly z cílového počítače, stejně jako vstup a odešle jej do cílového počítače.

   ![Okno konzoly Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-based-projects"></a>Konfigurace dalších možností ladění (projekty založené na msbuildu)

- Argumenty příkazového řádku lze předat spustitelnému souboru pomocí **položky Argumenty programu** na stránce **vlastností Ladění** projektu.

   ![Argumenty programu](media/settings_programarguments.png)

- Konkrétní možnosti ladicího programu lze předat GDB pomocí **položky Další příkazy ladicího programu.**  Můžete například chtít ignorovat signály SIGILL (nelegální instrukce).  Příkaz **popisovač** můžete použít k dosažení tohoto cíle přidáním následující položky další **debugger příkazy,** jak je znázorněno výše:

   `handle SIGILL nostop noprint`

## <a name="configure-other-debugging-options-cmake-projects"></a>Konfigurace dalších možností ladění (projekty CMake)

V souboru launch.vs.json můžete zadat další argumenty příkazového řádku pro projekt CMake. Další informace naleznete [v tématu Ladění projektu CMake](cmake-linux-project.md#debug_cmake_project)

## <a name="debug-with-attach-to-process"></a>Ladění s připojit k procesu

Stránka [vlastností Ladění](prop-pages/debugging-linux.md) pro projekty sady Visual Studio a nastavení **Launch.vs.json** pro projekty CMake mají nastavení, která umožňují připojení ke spuštěnému procesu. Pokud požadujete další kontrolu nad rámec toho, co je `Microsoft.MIEngine.Options.xml` k dispozici v těchto nastaveních, můžete umístit soubor pojmenovaný do kořenového adresáře řešení nebo pracovního prostoru. Zde je jednoduchý příklad:

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

**AttachOptionsForConnection** má většinu atributů, které může potřebovat. Výše uvedený příklad ukazuje, jak určit umístění pro vyhledávání dalších knihoven .so. Podřízený prvek **ServerOptions** umožňuje připojení ke vzdálenému procesu s gdbserver místo. Chcete-li to provést, musíte zadat místní hoddb klienta (ten dodaný v sadě Visual Studio 2017 je uveden výše) a místní kopii binárního souboru se symboly. Element **SetupCommands** umožňuje předávat příkazy přímo do gdb. Všechny možnosti, které jsou k dispozici ve [schématu LaunchOptions.xsd](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) na GitHubu.

::: moniker range="vs-2019"

## <a name="specify-different-machines-for-building-and-debugging"></a><a name="separate_build_debug"></a>Určení různých počítačů pro vytváření a ladění

Ve Visual Studiu 2019 verze 16.1 můžete oddělit vzdálený počítač sestavení od vzdáleného ladicího počítače pro projekty Linux založené na MSBuild a CMake, které cílí na vzdálený počítač s Linuxem. Například nyní můžete křížovou kompilaci na x64 a nasadit na zařízení ARM při cílení scénáře IoT.

### <a name="msbuild-based-projects"></a>Projekty založené na msbuildu

Ve výchozím nastavení je vzdálený ladicí počítač stejný jako vzdálený počítač sestavení **(Konfigurační vlastnosti** > **obecného** > **vzdáleného počítače).** Chcete-li určit nový vzdálený ladicí počítač, klepněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a přejděte na**položku** > Ladění **vlastností** > konfigurace**vzdáleného ladicího stroje**.  

![Vzdálený ladicí stroj linuxu](media/linux-remote-debug-machine.png)

Rozevírací nabídka pro **vzdálený ladicí stroj** je naplněna všemi zavedenými vzdálenými připojeními. Chcete-li přidat nové vzdálené připojení, přejděte do**nástroje** **Možnosti** > **Options** > **křížové platformy** > Connection Manager nebo vyhledejte "Connection Manager" v **panelu Snadné spuštění**. Můžete také zadat nový vzdálený adresář nasazení v objektových stránkách projektu **(Vlastnosti** > konfigurace **– obecný** > **vzdálený adresář nasazení).**

Ve výchozím nastavení budou do vzdáleného ladicího počítače nasazeny pouze soubory nezbytné pro proces ladění. **Průzkumník řešení** můžete použít ke konfiguraci, které zdrojové soubory budou nasazeny do vzdáleného ladicího počítače. Když kliknete na zdrojový soubor, zobrazí se náhled jeho vlastností souboru přímo pod Průzkumníkem řešení.

![Linux nasaditelné soubory](media/linux-deployable-content.png)

Vlastnost **Content** určuje, zda bude soubor nasazen do vzdáleného ladicího počítače. Nasazení můžete zakázat zcela přechodem do > **správce konfigurace** **stránek vlastností**a zrušením zaškrtnutí **políčka Nasazení** pro požadovanou konfiguraci.

V některých případech může vyžadovat větší kontrolu nad nasazením projektu. Některé soubory, které chcete nasadit, mohou být například mimo vaše řešení nebo chcete přizpůsobit vzdálený adresář nasazení podle souboru nebo adresáře. V těchto případech přidejte k souboru .vcxproj následující blok kódu a nahraďte "example.cpp" skutečnými názvy souborů:

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

Pro projekty CMake, které cílí na vzdálený počítač s Linuxem, můžete zadat nový vzdálený ladicí počítač v launch.vs.json. Ve výchozím nastavení je hodnota "remoteMachineName" synchronizována s vlastností "remoteMachineName" v souboru CMakeSettings.json, která odpovídá vzdálenému počítači sestavení. Tyto vlastnosti již není nutné odpovídat a hodnota "remoteMachineName" v launch.vs.json bude určovat, který vzdálený počítač se používá pro nasazení a ladění.

![CMake vzdálený ladicí stroj](media/cmake-remote-debug-machine.png)

Technologie IntelliSense navrhne všechny seznamy všech nastoje vzdálených připojení. Nové vzdálené připojení můžete přidat tak, že přejdete do nástroje > **Možnosti** > **cross Platform** > **Connection Manager** nebo vyhledáte "Connection Manager" v **programu Snadné spuštění**. **Tools**

Pokud chcete úplnou kontrolu nad nasazením, můžete připojit následující bloky kódu k souboru launch.vs.json. Nezapomeňte nahradit zástupné hodnoty skutečnými hodnotami:

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

- Chcete-li ladit zařízení ARM v systému Linux, podívejte se na tento příspěvek blogu: [Ladění vloženého zařízení ARM v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/).

## <a name="see-also"></a>Viz také

[Vlastnosti ladění jazyka C++ (Linux C++)](prop-pages/debugging-linux.md)
