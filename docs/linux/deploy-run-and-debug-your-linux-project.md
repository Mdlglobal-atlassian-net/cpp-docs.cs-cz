---
title: Nasazení, spuštění a ladění projektu C++ Linux v sadě Visual Studio
description: Popisuje, jak kompilovat, spouštění a ladění kódu na vzdálené cílové z uvnitř projektu Linux C++ v sadě Visual Studio.
ms.date: 06/07/2019
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: 707915a502aafefee47af7e84b534e06ba678b3d
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821630"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Nasazení, spuštění a ladění projektu Linux

::: moniker range="vs-2015"

Podpora Linuxu je k dispozici v sadě Visual Studio 2017 nebo novější.

::: moniker-end

Po vytvoření projektu Linux C++ v sadě Visual Studio a jste se připojili pomocí projektu [Správce připojení systému Linux](connect-to-your-remote-linux-computer.md), můžete spustit a ladit projekt. Kompilace, spuštění a ladění kódu na vzdálené cílové.

::: moniker range="vs-2019"

**Visual Studio 2019 verze 16.1** je možné cílit na různých systémech Linux pro účely ladění a sestavení. Určete počítač sestavení na **Obecné** stránku vlastností a ladění počítačů na **ladění** stránku vlastností.

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

## <a name="configure-other-debugging-options"></a>Nakonfigurovat další možnosti ladění

- Argumenty příkazového řádku může být předán spustitelného souboru pomocí **argumenty programu** položky v projektu **ladění** stránku vlastností.

   ![Argumenty programu](media/settings_programarguments.png)

- Možnosti ladicího programu pro konkrétní mohou být předány GDB pomocí **další příkazy ladicího programu** položka.  Můžete například chtít ignorovat SIGILL signály (Neplatná instrukce).  Můžete použít **zpracování** příkaz, který můžete toho dosáhnout.  přidáním následujícího **další příkazy ladicího programu** položka, jak je uvedeno výše:

   `handle SIGILL nostop noprint`

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

## <a name="next-steps"></a>Další kroky

- Chcete-li ladit ARM zařízení v systému Linux, najdete v tomto blogovém příspěvku: [Ladění zařízení se systémem embedded ARM v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/).

## <a name="see-also"></a>Viz také:

[C++ vlastnosti ladění (Linux C++)](prop-pages/debugging-linux.md)
