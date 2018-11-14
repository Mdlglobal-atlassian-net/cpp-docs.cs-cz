---
title: Nasazení, spuštění a ladění projektu C++ Linux v sadě Visual Studio
description: Popisuje, jak kompilovat, spouštění a ladění kódu na vzdálené cílové z uvnitř projektu Linux C++ v sadě Visual Studio.
ms.date: 09/12/2018
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
ms.openlocfilehash: 413f0b089b3b1398093073bcd6f49358143121c8
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328393"
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Nasazení, spuštění a ladění projektu Linux

Po vytvoření projektu Linux C++ v sadě Visual Studio a jste se připojili pomocí projektu [Správce připojení systému Linux](../linux/connect-to-your-remote-linux-computer.md), můžete spustit a ladit projekt. Kompilace, spuštění a ladění kódu na vzdálené cílové.

Existuje několik způsobů, jak pracovat s a ladění projektu Linux.

- Ladění pomocí tradiční funkce aplikace Visual Studio, jako je například zarážky, oknech kukátka a ukazatele myši nad proměnnou. Použití těchto metod, může ladit běžným způsobem pro ostatní typy projektů.

- Zobrazit výstup z cílový počítač ve speciální okno konzoly systému Linux. Můžete také použít konzolu k odeslání vstupní k cílovému počítači.

## <a name="debug-your-linux-project"></a>Ladění projektu Linux

1. Vyberte režim ladění v **ladění** stránku vlastností.

   GDB slouží k ladění aplikace běžící na Linuxu.  Ale to můžete spustit ve dvou různých režimech, které můžete vybrat z **režim ladění** možnost v projektu **ladění** stránky vlastností:

   ![Možnosti GDB](media/settings_debugger.png)

   - V **gdbserver** režimu GDB spouštíte místně, která se připojuje k gdbserver běží na vzdáleném systému.  Všimněte si, že se jedná o jediný režim, který podporuje v okně konzoly systému Linux.

   - V **gdb** režimu jednotky ladicího programu sady Visual Studio GDB ve vzdáleném systému, který je kompatibilní více, pokud v místní verzi GDB není kompatibilní s verzí nainstalované v cílovém počítači. |

   > [!NOTE]
   > Pokud se nemůžete k dosažení zarážky v ladění režimu gdbserver, zkuste režimu gdb použije. musí být nejprve gdb [nainstalované](../linux/download-install-and-setup-the-linux-development-workload.md) na vzdálené cílové.

1. Vyberte vzdálený cíl pomocí standardní **ladění** nástrojů v sadě Visual Studio.

   Při vzdálené cílové je k dispozici, zobrazí se, že je uvedená podle názvu nebo IP adresu.

   ![Vzdálené cílové](media/remote_target.png)

   Pokud jste se ještě nepřipojili na vzdálené cílové, zobrazí se pokyn k použití [Správce připojení systému Linux](../linux/connect-to-your-remote-linux-computer.md) pro připojení k vzdálené cílové.

   ![Vzdálené architektury](media/architecture.png)

1. Spustí sadu zarážku kliknutím v levém hřbetu kódu, které znáte.

   Červená tečka se zobrazí na řádku kódu, kde nastavit zarážku.

1. Stisknutím klávesy **F5** (nebo **ladit > Spustit ladění**) pro spuštění ladění.

   Při spuštění ladění bude uložena zkompilovaná aplikace na vzdálené cílové před spuštěním. Chyby při kompilaci se zobrazí v **seznam chyb** okna.

   Pokud nejsou žádné chyby, aplikace se spustí a ladicí program se pozastaví na zarážce.

   ![Na zarážku](media/hit_breakpoint.png)

   Teď můžete pracovat s aplikací v stisknutím klávesy příkazu, jako je aktuální stav, zobrazit proměnné a procházejte kódem po krocích **F10** nebo **F11**.

1. Pokud chcete použít konzolu pro Linux pro interakci s vaší aplikací, vyberte **ladit > Konzola Linuxu**.

   ![Konzola Linuxu nabídky](media/consolemenu.png)

   Tato konzola zobrazit žádný výstup konzoly z cílového počítače a také trvat vstupní a odeslat do cílového počítače.

   ![Okno konzoly systému Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options"></a>Nakonfigurovat další možnosti ladění

- Argumenty příkazového řádku může být předán spustitelného souboru pomocí **argumenty programu** položky v projektu **ladění** stránku vlastností.

   ![Argumenty programu](media/settings_programarguments.png)

- Možnosti ladicího programu pro konkrétní mohou být předány GDB pomocí **další příkazy ladicího programu** položka.  Můžete například chtít ignorovat SIGILL signály (Neplatná instrukce).  Můžete použít **zpracování** příkaz, který můžete toho dosáhnout.  přidáním následujícího **další příkazy ladicího programu** položka, jak je uvedeno výše:

   `handle SIGILL nostop noprint`

## <a name="next-steps"></a>Další kroky

- Chcete-li ladit ARM zařízení v systému Linux, najdete v tomto blogovém příspěvku: [ladění vestavěného zařízení ARM v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/).

- Chcete-li ladit pomocí **připojit k procesu** příkazu, najdete v tomto blogovém příspěvku: [úlohy pro C++ Linux vylepšení systém projektu, okna konzoly systému Linux, rsync a připojit k procesu](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).

## <a name="see-also"></a>Viz také:

[C++ vlastnosti ladění (Linux C++)](../linux/prop-pages/debugging-linux.md)
