---
title: Nasazení, spustit a spusťte ladění svého projektu Linux | Microsoft Docs
ms.custom: ''
ms.date: 11/06/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-linux
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: ebd8783bdcf3c188e04c1d6808d5a727a2bc7cdd
ms.sourcegitcommit: cff1a8a49f0cd50f315a250c5dd27e15c173845f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2018
---
# <a name="deploy-run-and-debug-your-linux-project"></a>Nasazení, spustit a spusťte ladění svého projektu Linux

Po vytvoření projektu Linux a jste se připojili k projektu pomocí [Správce připojení systému Linux](../linux/connect-to-your-remote-linux-computer.md), můžete spustit a ladění projektu. Kompilovat, spouštění a ladění kódu na vzdálené cíli.

Existuje několik způsobů, jak pracovat s a ladění projektu Linux.

* Ladění pomocí tradičních funkcích nástroje Visual Studio, například zarážky, sledovat windows a ukazatele myši na proměnnou. Těmito metodami může ladění jako za normálních okolností byste pro jiné typy projektů.
* Zobrazit výstup z cílový počítač ve speciální okna konzoly Linux. Můžete také použít konzolu k odeslání vstupní k cílovému počítači.

## <a name="debug-your-linux-project"></a>Spusťte ladění svého projektu Linux

1. Vyberte režim ladění v **ladění** stránku vlastností.

    GDB slouží k ladění aplikací spuštěných v systému Linux.  Nicméně to spustit ve dvou různých režimech, které je možné vybrat z **režim ladění** možnost v projektu **ladění** stránky vlastností:

    ![Možnosti GDB](media/settings_debugger.png)

    - V **gdbserver** režimu GDB běží místně, který se připojuje k gdbserver spuštěná ve vzdáleném systému.  Všimněte si, že se jedná pouze režimu, který podporuje v okně konzoly Linux.

    - V **gdb** režimu ladicího programu sady Visual Studio jednotky GDB ve vzdáleném systému, což je více kompatibilní, pokud v místní verzi GDB není kompatibilní s verzí nainstalované v cílovém počítači. |

    > [!NOTE] 
    > Pokud není možné zadat zarážky v režimu ladění gdbserver, zkuste gdb režimu. musí být nejprve gdb [nainstalován](../linux/download-install-and-setup-the-linux-development-workload.md) na vzdálené cíli.

2. Vyberte vzdálený cíl přes standardní **ladění** panelu nástrojů v sadě Visual Studio.

    Když vzdálený cíl je k dispozici, zobrazí se, že ho uvedené podle názvu nebo IP adresu.

    ![Vzdálený cíl](media/remote_target.png)

    Pokud jste se ještě nepřipojili k vzdáleného cíli, zobrazí se instrukce používat [Správce připojení systému Linux](../linux/connect-to-your-remote-linux-computer.md) pro připojení k vzdálené cíl.

    ![Vzdálené architektura](media/architecture.png)

3. Sada vědět zarážek klikněte v levém oddělovací mezery u některých kódu, které spustí.

    Červené tečky, zobrazí se na řádek kódu, kde nastavit bod přerušení.

4. Stiskněte klávesu **F5** (nebo **ladění > Spustit ladění**) spustit ladění.

    Při spuštění ladění aplikace je před spuštěním kompilovány na vzdálený cíl. Všechny chyby kompilace se objeví v **seznam chyb** okno.

    Pokud nejsou žádné chyby, spustí aplikaci a ladicí program se pozastaví u zarážky.

    ![Stiskněte tlačítko zarážky](media/hit_breakpoint.png)  

    Nyní můžete pracovat s aplikací v stisknutím příkaz klíče, jako je aktuální stav, zobrazit proměnné a krok prostřednictvím kódu **F10** nebo **F11**.

4. Pokud chcete použít konzolu Linux k interakci s vaší aplikací, vyberte **ladění > konzole Linux**.

  ![Nabídce konzoly Linux](media/consolemenu.png)

  Tato konzola zobrazit žádný výstup konzoly z cílového počítače a také provést vstupní a odeslat do cílového počítače.

  ![Okno konzoly Linux](media/consolewindow.png)

## <a name="configure-other-debugging-options"></a>Konfigurace dalších možností ladění

* Argumenty příkazového řádku se dá předat do spustitelného souboru pomocí **Program argumenty** položku v projektu **ladění** stránku vlastností.
  
  ![Program argumenty](media/settings_programarguments.png)

* Ladicí program konkrétní možnosti se dá předat do GDB pomocí **další příkazy ladicí program** položka.  Například můžete chtít ignorovat sigill – signály (Neplatná instrukce).  Můžete použít **zpracování** příkaz dosáhnout.  přidáním následujícího **další příkazy ladicí program** položku jako v příkladu nahoře:

  ```handle SIGILL nostop noprint```

## <a name="next-steps"></a>Další kroky

* Chcete-li ladit ARM zařízení v systému Linux, najdete v části tohoto příspěvku blogu: [ladění vložené zařízení ARM v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/).

* K ladění pomocí **připojit k procesu** příkazů najdete v tématu tohoto příspěvku blogu: [Linux C++ zatížení vylepšení systému projektu okna konzoly Linux, rsync a připojit k procesu](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).

## <a name="see-also"></a>Viz také
[C++ – ladění vlastnosti (Linux C++)](../linux/prop-pages/debugging-linux.md).
