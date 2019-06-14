---
title: Nasazení, spuštění a ladění projektu C++ Linux v sadě Visual Studio
description: Popisuje, jak kompilovat, spouštění a ladění kódu na vzdálené cílové z uvnitř projektu Linux C++ v sadě Visual Studio.
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: 70770385bde859d47532b130463a1cc54e32a570
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042761"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Nasazení, spuštění a ladění projektu Linux

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

Po vytvoření projektu Linux C++ v sadě Visual Studio a jste se připojili pomocí projektu [Správce připojení systému Linux](connect-to-your-remote-linux-computer.md), můžete spustit a ladit projekt. Kompilace, spuštění a ladění kódu na vzdálené cílové.

::: moniker range="vs-2019"

**Visual Studio 2019 verze 16.1** je možné cílit na různých systémech Linux pro účely ladění a sestavení. Například můžete křížové kompilace na x64 a nasadit do zařízení s ARM, při cílení na scénáře IoT. Další informace najdete v tématu [určit různé počítače pro sestavování a ladění](#separate_build_debug) dále v tomto článku.

::: moniker-end

Existuje několik způsobů, jak pracovat s a ladění projektu Linux.

- Ladění pomocí tradiční funkce aplikace Visual Studio, jako je například zarážky, oknech kukátka a ukazatele myši nad proměnnou. Použití těchto metod, může ladit běžným způsobem pro ostatní typy projektů.

- Zobrazení výstupu z cílového počítače v okně konzoly systému Linux. Můžete také použít konzolu k odeslání vstupní k cílovému počítači.

## <a name="debug-your-linux-project"></a>Ladění projektu Linux

1. Vyberte režim ladění v **ladění** stránku vlastností.
   
   ::: moniker range="vs-2019"

   GDB slouží k ladění aplikace běžící na Linuxu. Při ladění na vzdáleném systému (ne WSL) můžete spustit GDB ve dvou různých režimech, které můžete vybrat z **režim ladění** možnost v projektu **ladění** stránky vlastností:

   ![Možnosti GDB](media/vs2019-debugger-settings.png)

   ::: moniker-end

   ::: moniker range="vs-2017"

   GDB slouží k ladění aplikace běžící na Linuxu. Můžete spustit GDB ve dvou různých režimech, které můžete vybrat z **režim ladění** možnost v projektu **ladění** stránky vlastností:

   ![Možnosti GDB](media/vs2017-debugger-settings.png)

   ::: moniker-end


   - V **gdbserver** režimu GDB spouštíte místně, která se připojí k gdbserver ve vzdáleném systému.  Všimněte si, že se jedná o jediný režim, který podporuje v okně konzoly systému Linux.

   - V **gdb** režim ladicího programu sady Visual Studio GDB jednotky ve vzdáleném systému. To je lepší volbou, pokud v místní verzi GDB není kompatibilní s verzí nainstalované v cílovém počítači. |

   > [!NOTE]
   > Pokud se nemůžete k dosažení zarážky v ladění režimu gdbserver, zkuste režimu gdb použije. musí být nejprve gdb [nainstalované](download-install-and-setup-the-linux-development-workload.md) na vzdálené cílové.

1. Vyberte vzdálený cíl pomocí standardní **ladění** nástrojů v sadě Visual Studio.

   Při vzdálené cílové je k dispozici, zobrazí se, že je uvedená podle názvu nebo IP adresu.

   ![Vzdálené cílové](media/remote_target.png)

   Pokud jste se ještě nepřipojili na vzdálené cílové, zobrazí se pokyn k použití [Správce připojení systému Linux](connect-to-your-remote-linux-computer.md) pro připojení k vzdálené cílové.

   ![Vzdálené architektury](media/architecture.png)

1. Spustí sadu zarážku kliknutím v levém hřbetu kódu, které znáte.

   Červená tečka se zobrazí na řádku kódu, kde nastavit zarážku.

1. Stisknutím klávesy **F5** (nebo **ladit > Spustit ladění**) pro spuštění ladění.

   Při spuštění ladění bude uložena zkompilovaná aplikace na vzdálené cílové před spuštěním. Chyby při kompilaci se zobrazí v **seznam chyb** okna.

   Pokud nejsou žádné chyby, aplikace se spustí a ladicí program se pozastaví na zarážce.

   ![Na zarážku](media/hit_breakpoint.png)

   Teď můžete pracovat s aplikací v jeho aktuálním stavu, zobrazit proměnné a procházejte kódem po krocích stisknutím klávesy příkaz **F10** nebo **F11**.

1. Pokud chcete použít konzolu pro Linux pro interakci s vaší aplikací, vyberte **ladit > Konzola Linuxu**.

   ![Konzola Linuxu nabídky](media/consolemenu.png)

   Tato konzola zobrazit žádný výstup konzoly z cílového počítače a také trvat vstupní a odeslat do cílového počítače.

   ![Okno konzoly systému Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options-msbuild-based-projects"></a>Nakonfigurovat další možnosti ladění (projekty využívající MSBuild)

- Argumenty příkazového řádku může být předán spustitelného souboru pomocí **argumenty programu** položky v projektu **ladění** stránku vlastností.

   ![Argumenty programu](media/settings_programarguments.png)

- Možnosti ladicího programu pro konkrétní mohou být předány GDB pomocí **další příkazy ladicího programu** položka.  Můžete například chtít ignorovat SIGILL signály (Neplatná instrukce).  Můžete použít **zpracování** dosáhnete přidáním následujícího příkazu **další příkazy ladicího programu** položka, jak je uvedeno výše:

   `handle SIGILL nostop noprint`

## <a name="configure-other-debugging-options-cmake-projects"></a>Nakonfigurovat další možnosti ladění (projekty CMake)

Můžete zadat další argumenty příkazového řádku pro projekt CMake v souboru launch.vs.json. Další informace najdete v tématu [ladit projekt CMake](cmake-linux-project.md#debug_cmake_project)

## <a name="debug-with-attach-to-process"></a>Ladění se připojit k procesu

[Ladění](prop-pages/debugging-linux.md) stránku vlastností pro projekty aplikace Visual Studio a **souboru Launch.vs.json** nastavení pro projekty CMake, mají nastavení, které vám umožní připojit ke spuštěnému procesu. Pokud potřebujete větší kontrolu nad rámec co je součástí těchto nastavení, můžete umístit soubor s názvem `Microsoft.MIEngine.Options.xml` v kořenové složce vašeho řešení nebo pracovního prostoru. Tady je jednoduchý příklad:

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

**AttachOptionsForConnection** s nejvíce atributů může být nutné. Výše uvedený příklad ukazuje, jak zadat umístění pro vyhledávání knihoven Další .so. Podřízený element **ServerOptions** umožňuje připojení ke vzdálenému procesu s gdbserver místo. K tomu budete muset zadat místní gdb klienta (jedna odeslaná v sadě Visual Studio 2017 je popsaný výš) a místní kopii binárního souboru se symboly. **SetupCommands** element umožňuje předat příkazy přímo do gdb. Můžete najít všechny možnosti, které jsou k dispozici v [LaunchOptions.xsd schématu](https://github.com/Microsoft/MIEngine/blob/master/src/MICore/LaunchOptions.xsd) na Githubu.

::: moniker range="vs-2019"

## <a name="separate_build_debug"></a> Zadejte jiný počítačů pro sestavování a ladění

V aplikaci Visual Studio 2019 verze 16.1 můžete oddělit vzdáleného úložiště sestavení počítače z vašeho počítače vzdáleného ladění pro založené na MSBuild Linuxové projekty a projekty CMake, které se zaměřují vzdáleném počítači s Linuxem. Například můžete nyní křížové kompilace na x64 a nasadit do zařízení s ARM, při cílení na scénáře IoT.

### <a name="msbuild-based-projects"></a>Projekty využívající MSBuild

Ve výchozím nastavení, vzdálený ladicí počítač je stejný jako vzdálený sestavující počítač (**vlastnosti konfigurace** > **Obecné** > **vzdálený počítač sestavení**). Pokud chcete zadat nový počítač vzdáleného ladění, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a přejděte na **vlastnosti konfigurace** > **ladění**  >  **Vzdáleného ladění počítače**.  

![Vzdálený ladicí počítač s Linuxem](media/linux-remote-debug-machine.png)

V rozevírací nabídce pro **vzdáleného ladění počítače** se načtou všechny zavedené vzdálená připojení. Chcete-li přidat nové vzdálené připojení, přejděte na **nástroje** > **možnosti** > **různé platformy**  >   **Správce připojení** nebo vyhledejte "Connection Manager" v **Snadné spuštění**. Můžete také určit nasadit nový vzdálený adresář na stránkách vlastností projektu (**vlastnosti konfigurace** > **Obecné** > **vzdálený adresář nasazení** ).

Ve výchozím nastavení se nasadí na vzdálený ladicí počítač pouze soubory nezbytné pro proces pro ladění. Můžete použít **Průzkumníka řešení** nakonfigurovat zdroj, který se nasadí soubory do počítače vzdáleného ladění. Když kliknete na zdrojový soubor, zobrazí se náhled vlastnosti souboru přímo pod v Průzkumníku řešení.

![Nasaditelnými soubory Linuxu](media/linux-deployable-content.png)

**Obsahu** vlastnost určuje, zda se soubor nasadí do počítače vzdáleného ladění. Nasazení můžete zakázat zcela tak, že přejdete do **stránky vlastností** > **nástroje Configuration Manager** a zrušíte zaškrtnutí **nasadit** pro požadovaný konfigurace.

V některých případech mohou vyžadovat větší kontrolu nad nasazením váš projekt. Například může být některé soubory, které chcete nasadit mimo vašeho řešení nebo chcete přizpůsobit vzdáleného úložiště nasadit adresář za ordirectory souboru. V těchto případech připojit následujících bloků kódu do souboru .vcxproj a nahraďte názvy skutečný soubor "example.cpp":

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

Pro projekty CMake, které se zaměřují vzdáleném počítači s Linuxem můžete zadat nový počítač vzdáleného ladění v souboru launch.vs.json. Ve výchozím nastavení je hodnota "název_vzdáleného_počítače" synchronizován s vlastnost "název_vzdáleného_počítače" v souboru CMakeSettings.json, který odpovídá vzdálený sestavující počítač. Tyto vlastnosti se už nemusí odpovídat, a hodnota "název_vzdáleného_počítače" v souboru launch.vs.json bude určovat, které vzdálený počítač se používá pro nasazení a ladění.

![CMake vzdálený ladicí počítač](media/cmake-remote-debug-machine.png)

Technologie IntelliSense nabídne všem seznam všech vytvořených vzdáleného připojení. Můžete přidat nové připojení ke vzdálené tak, že přejdete do **nástroje** > **možnosti** > **různé platformy**  >   **Správce připojení** nebo vyhledávání "Connection Manager" v rámci **Snadné spuštění**.

Pokud chcete úplnou kontrolu nad nasazením, můžete přidat následující bloků kódu do souboru launch.vs.json. Nezapomeňte nahradit hodnoty zástupných symbolů skutečné hodnoty:

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

- Chcete-li ladit ARM zařízení v systému Linux, najdete v tomto blogovém příspěvku: [Ladění zařízení se systémem embedded ARM v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/).

## <a name="see-also"></a>Viz také:

[C++ vlastnosti ladění (Linux C++)](prop-pages/debugging-linux.md)
