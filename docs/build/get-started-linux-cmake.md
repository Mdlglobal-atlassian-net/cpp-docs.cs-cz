---
title: Vytváření projektů v jazyce C++ pro různé platformy v sadě Visual Studio
description: Jak nastavit, zkompilovat a ladit open source projekt CMake v sadě Visual Studio, který cílí na Linux i Windows.
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: aac536f488cf22adf5aa835c9fe5b884fc5d7298
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328748"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Kurz: vytváření projektů pro různé platformy C++ v aplikaci Visual Studio

Vývoj pro Visual Studio C a C++ už není jenom pro Windows. V tomto kurzu se dozvíte, jak používat Visual Studio pro vývoj pro různé platformy C++ v systémech Windows a Linux. Je založena na CMaki, takže nemusíte vytvářet ani generovat projekty sady Visual Studio. Když otevřete složku, která obsahuje soubor CMakeLists. txt, Visual Studio nakonfiguruje technologii IntelliSense a nastavení sestavení automaticky. Můžete rychle začít upravovat, sestavovat a ladit kód místně ve Windows. Pak přepněte svou konfiguraci tak, aby byla stejná pro Linux, vše z aplikace Visual Studio.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * naklonování open source projektu CMake z GitHubu
> * Otevřete projekt v aplikaci Visual Studio
> * sestavení a ladění cíle spustitelných souborů ve Windows
> * Přidání připojení k počítači se systémem Linux
> * sestavování a ladění stejného cíle v systému Linux

## <a name="prerequisites"></a>Požadavky

* Nastavení sady Visual Studio pro vývoj pro různé platformy C++
  * Nejdřív [nainstalujte Visual Studio](https://visualstudio.microsoft.com/vs/) a vyberte **vývoj desktopových aplikací s** využitím **úloh c++ a vývoj pro Linux**. Tato minimální instalace je jenom 3 GB. V závislosti na rychlosti stahování by instalace neměla trvat déle než 10 minut.

* Nastavení počítače se systémem Linux pro vývoj pro různé platformy C++
  * Visual Studio nevyžaduje žádnou konkrétní distribuci systému Linux. Operační systém může běžet na fyzickém počítači, na VIRTUÁLNÍm počítači nebo v cloudu. Můžete také použít podsystém Windows pro Linux (WSL). Pro tento kurz se ale vyžaduje grafické prostředí. WSL se tady nedoporučuje, protože je určený hlavně pro operace s příkazovým řádkem.
  * Visual Studio vyžaduje tyto nástroje na počítači se systémem Linux: kompilátory C++, GDB, SSH, rsync, expertem a zip. V systémech založených na Debian můžete pomocí tohoto příkazu nainstalovat tyto závislosti:

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync ninja-build zip
    ```

  * Sada Visual Studio vyžaduje na počítači se systémem Linux novější verzi CMake, která má povolený režim serveru (minimálně 3,8). Společnost Microsoft vytvoří univerzální sestavování CMake, které můžete nainstalovat na všechny distribuce se systémem Linux. Toto sestavení doporučujeme použít k zajištění, že máte nejnovější funkce. Binární soubory CMake můžete získat z [větve Microsoftu úložiště cmake](https://github.com/Microsoft/CMake/releases) na GitHubu. Přejít na tuto stránku a stáhnout verzi, která odpovídá architektuře systému na počítači se systémem Linux, a označit ji jako spustitelný soubor:

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * Možnosti spuštění skriptu můžete zobrazit pomocí `-–help`. Doporučujeme, abyste použili `–prefix` možnost zadat instalaci do **/usr** cesty, protože **/usr/bin** je výchozí umístění, kde aplikace Visual Studio hledá cmake. Následující příklad ukazuje skript pro Linux x86_64. Pokud používáte jinou cílovou platformu, změňte ji podle potřeby.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Git pro Windows nainstalovaný na počítači s Windows.
* Účet GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Naklonování open source projektu CMake z GitHubu

V tomto kurzu se používá sada odrážek sady SDK na GitHubu. Poskytuje detekci kolizí a simulaci fyziky pro mnoho aplikací. Sada SDK obsahuje ukázkové spustitelné programy, které se zkompiluje a spouštějí bez nutnosti psát další kód. V tomto kurzu se nemění žádný zdrojový kód ani skripty sestavení. Začněte tím, že naklonujte úložiště *bullet3* z GitHubu na počítači, na kterém máte nainstalovanou aplikaci Visual Studio.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. V hlavní nabídce sady Visual Studio vyberte **soubor > otevřít > cmake**. V kořenovém adresáři úložiště bullet3, který jste právě stáhli, přejděte do souboru CMakeLists. txt.

    ![Nabídka sady Visual Studio pro soubor > otevřít > CMake](media/cmake-open-cmake.png)

    Jakmile složku otevřete, bude struktura složek v **Průzkumník řešení**viditelná.

    ![Zobrazení složky Průzkumník řešení sady Visual Studio](media/cmake-bullet3-solution-explorer.png)

    Toto zobrazení vám ukáže přesně to, co je na disku, nikoli logické nebo filtrované zobrazení. Ve výchozím nastavení se skryté soubory nezobrazují.

1. Kliknutím na tlačítko **Zobrazit všechny soubory** zobrazíte všechny soubory ve složce.

    ![Tlačítko pro zobrazení všech souborů v aplikaci Visual Studio Průzkumník řešení](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Přepnout na zobrazení cílů

Když otevřete složku, která používá CMake, sada Visual Studio automaticky vygeneruje mezipaměť CMake. Tato operace může chvíli trvat, v závislosti na velikosti projektu.

1. V **okno výstup**vyberte **Zobrazit výstup z** a pak zvolte **cmake** , abyste mohli monitorovat stav procesu generování mezipaměti. Po dokončení operace se zobrazí zpráva "extrakce cílových informací byla dokončena".

   ![Okno výstup sady Visual Studio zobrazující výstup z CMake](media/cmake-bullet3-output-window.png)

   Po dokončení této operace je nakonfigurována technologie IntelliSense. Můžete sestavit projekt a ladit aplikaci. Visual Studio nyní zobrazuje logické zobrazení řešení na základě cílů zadaných v souborech CMakeLists.

1. Pomocí tlačítka **řešení a složky** v **Průzkumník řešení** přepněte na zobrazení cílů cmake.

   ![Tlačítko řešení a složky v Průzkumník řešení pro zobrazení cílů CMake](media/cmake-bullet3-show-targets.png)

   Toto zobrazení vypadá jako u sady odrážek:

   ![Zobrazení cílů Průzkumník řešení CMake](media/cmake-bullet3-targets-view.png)

   Zobrazení cílů nabízí intuitivnější zobrazení toho, co je v této zdrojové základně. Můžete vidět, že některé cíle jsou knihovny a jiné jsou spustitelné soubory.

1. Rozbalením uzlu v zobrazení cílů CMake zobrazíte soubory se zdrojovým kódem, pokud se tyto soubory mohou nacházet na disku.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Přidání explicitní konfigurace Windows x64 – ladění

Visual Studio vytvoří výchozí konfiguraci pro **ladění x64** pro Windows. Konfigurace představují způsob, jakým aplikace Visual Studio rozumí, jaký cíl platformy se bude používat pro CMake. Výchozí konfigurace není reprezentovaná na disku. Když explicitně přidáte konfiguraci, Visual Studio vytvoří soubor s názvem *CMakeSettings. JSON*. Naplní se nastavením pro všechny zadané konfigurace.

1. Přidejte novou konfiguraci. Otevřete rozevírací seznam **Konfigurace** na panelu nástrojů a vyberte **spravovat konfigurace**.

   ![Rozevírací seznam pro správu konfigurace](media/cmake-bullet3-manage-configurations.png)

   Otevře se [Editor nastavení cmake](customize-cmake-settings.md) . Výběrem zeleného znaménka plus na levé straně editoru přidejte novou konfiguraci. Zobrazí se dialogové okno **Přidat konfiguraci do CMakeSettings** .

   ![Přidat konfiguraci do dialogového okna CMakeSettings](media/cmake-bullet3-add-configuration-x64-debug.png)

   Toto dialogové okno obsahuje všechny konfigurace, které jsou součástí sady Visual Studio, včetně všech vlastních konfigurací, které vytvoříte. Pokud chcete pokračovat v používání konfigurace **pro ladění x64** , která by měla být první, kterou přidáte. Vyberte **x64 – ladění**a pak klikněte na tlačítko **Vybrat** . Visual Studio vytvoří soubor CMakeSettings. JSON s konfigurací pro **x64 – ladění**a uloží ho na disk. Změnou parametru název přímo v CMakeSettings. JSON můžete použít libovolné názvy vašich konfigurací.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Nastavení zarážky, sestavení a spuštění ve Windows

V tomto kroku budeme ladit ukázkový program, který demonstruje knihovnu fyzika s odrážkami.
  
1. V **Průzkumník řešení**vyberte AppBasicExampleGui a rozbalte ji.

1. Otevřete soubor `BasicExample.cpp`.

1. Nastavte zarážku, která se získá po kliknutí na běžící aplikaci. Událost Click je zpracována v metodě v rámci pomocné třídy. K rychlému získání:

   1. Vyberte `CommonRigidBodyBase` , z něhož `BasicExample` je struktura odvozena. Je okolo řádku 30.

   1. Klikněte pravým tlačítkem a vyberte **Přejít k definici**. Teď jste v hlavičce CommonRigidBodyBase. h.

   1. V zobrazení prohlížeče nad vaším zdrojem byste měli vidět, že jste v `CommonRigidBodyBase`. Napravo můžete vybrat členy k prohlédnutí. Otevřete rozevírací nabídku a vyberte možnost `mouseButtonCallback` přejít k definici této funkce v hlavičce.

      ![Panel nástrojů seznam členů sady Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Umístěte zarážku na první řádek v rámci této funkce. Když kliknete na tlačítko myši v rámci aplikace, bude dosaženo při spuštění v ladicím programu sady Visual Studio.

1. Chcete-li spustit aplikaci, vyberte na panelu nástrojů možnost spustit v rozevíracím seznamu. Je to ikona se zelenou Play, která uvádí "vybrat položku po spuštění". V rozevíracím seznamu vyberte AppBasicExampleGui. exe. Název spustitelného souboru se nyní zobrazí na spouštěcím tlačítku:

   ![Rozevírací seznam pro spuštění panelu nástrojů sady Visual Studio pro výběr položky po spuštění](media/cmake-bullet3-launch-button.png)

1. Klikněte na tlačítko Spustit a sestavte aplikaci a nezbytné závislosti a potom ji spusťte pomocí připojeného ladicího programu sady Visual Studio. Po chvíli se spustí běžící aplikace:

   ![Ladění aplikace systému Windows v aplikaci Visual Studio](media/cmake-bullet3-launched.png)

1. Přesuňte myš do okna aplikace a potom kliknutím na tlačítko aktivujte zarážku. Zarážka přináší Visual Studio zpátky do popředí a Editor zobrazuje řádek, kde je provádění pozastaveno. Můžete kontrolovat proměnné aplikace, objekty, vlákna a paměť nebo krokovat kód prostřednictvím kódu interaktivně. Zvolte **pokračovat** , aby se aplikace obnovila, a pak ji obvyklým způsobem ukončete. Nebo zastavit provádění v rámci sady Visual Studio pomocí tlačítka zastavit.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Přidejte konfiguraci pro Linux a připojte se ke vzdálenému počítači.

1. Přidejte konfiguraci pro Linux. V zobrazení **Průzkumník řešení** klikněte pravým tlačítkem na soubor CMakeSettings. JSON a vyberte **Přidat konfiguraci**. Zobrazí se stejná dialogová okna Přidat konfiguraci do CMakeSettings jako předtím. Vyberte **Linux – ladění** tentokrát a pak uložte soubor CMakeSettings. JSON (CTRL + s).

1. V rozevíracím seznamu konfigurace vyberte **Linux-Debug** .

   ![Rozevírací seznam spuštění konfigurace s x64 – ladění a Linux – možnosti ladění](media/cmake-bullet3-linux-configuration-item.png)

   Pokud se připojujete k systému Linux poprvé, zobrazí se dialogové okno **připojit ke vzdálenému systému** .

   ![Dialogové okno připojení k vzdálenému systému Visual Studio](media/cmake-bullet3-connection-manager.png)

   Pokud jste už přidali vzdálené připojení, můžete toto okno otevřít tak, že přejdete na **nástroje > možnosti > > Správce připojení pro různé platformy**.

1. Zadejte [informace o připojení k počítači se systémem Linux](/cpp/linux/connect-to-your-remote-linux-computer) a klikněte na tlačítko **připojit**. Visual Studio přidá tento počítač jako výchozí připojení pro **Linux-Debug**jako výchozí připojení k CMakeSettings. JSON. Vyžádá si také hlavičky ze vzdáleného počítače, takže získáte [technologii IntelliSense specifickou pro toto vzdálené připojení](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense). V dalším kroku aplikace Visual Studio odešle soubory do vzdáleného počítače a vygeneruje mezipaměť CMake ve vzdáleném systému. Tyto kroky můžou nějakou dobu trvat, v závislosti na rychlosti vaší sítě a výkonu vzdáleného počítače. Budete vědět, že je to hotové, když se v okně výstup CMake zobrazí zpráva "extrakce cílových informací byla dokončena".

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Nastavení zarážky, sestavení a spuštění v systému Linux

Vzhledem k tomu, že se jedná o desktopovou aplikaci, je nutné zadat další konfigurační informace pro konfiguraci ladění.

1. V zobrazení cílů CMake klikněte pravým tlačítkem na AppBasicExampleGui a vyberte **nastavení ladění a spouštění** . otevře se soubor Launch. vs. JSON, který se nachází v podsložce skryté **. vs** . Tento soubor je místní pro vaše vývojové prostředí. Můžete ho přesunout do kořenového adresáře projektu, pokud ho chcete vrátit se změnami a uložit ho do svého týmu. V tomto souboru byla přidána konfigurace pro AppBasicExampleGui. Tato výchozí nastavení fungují ve většině případů, ale ne tady. Vzhledem k tomu, že se jedná o desktopovou aplikaci, musíte zadat nějaké další informace, abyste mohli spustit program, abyste ho viděli na počítači se systémem Linux.

1. Pokud chcete zjistit hodnotu proměnné `DISPLAY` prostředí na svém počítači se systémem Linux, spusťte tento příkaz:

   ```cmd
   echo $DISPLAY
   ```

   V konfiguraci pro AppBasicExampleGui je k dispozici pole parametrů "pipeArgs". Obsahuje řádek: $ {debuggerCommand}. Je to příkaz, který spouští GDB na vzdáleném počítači. Visual Studio musí před spuštěním tohoto příkazu Exportovat zobrazení do tohoto kontextu. Například pokud je `:1`hodnota zobrazení, upravte tento řádek následujícím způsobem:

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. Spusťte a ladit aplikaci. Otevřete rozevírací seznam **Vybrat položku po spuštění** na panelu nástrojů a zvolte možnost **AppBasicExampleGui**. Dále zvolte zelenou ikonu přehrávání na panelu nástrojů nebo stiskněte klávesu **F5**. Aplikace a její závislosti jsou postavené na vzdáleném počítači se systémem Linux a pak byly spuštěny pomocí připojeného ladicího programu sady Visual Studio. Na vzdáleném počítači se systémem Linux by se mělo zobrazit okno aplikace.

1. Přesuňte myš do okna aplikace a klikněte na tlačítko. Zarážka je dosaženo. Spuštění programu je pozastaveno, Visual Studio se vrátí zpět do popředí a zobrazí se zarážka. V aplikaci Visual Studio by se měla zobrazit také okno konzoly pro Linux. Okno poskytuje výstup ze vzdáleného počítače se systémem Linux a může také přijmout vstup pro `stdin`. Stejně jako jakékoli okno aplikace Visual Studio, můžete ho ukotvit tam, kde ho chcete zobrazit. Jeho pozice je trvalá v budoucích relacích.

   ![Okno konzoly Visual Studio Linux](media/cmake-bullet3-linux-console.png)

1. Pomocí sady Visual Studio můžete interaktivně kontrolovat proměnné aplikace, objekty, vlákna, paměť a krokovat kód. V tuto chvíli ale provádíte vše na vzdáleném počítači se systémem Linux namísto místního prostředí systému Windows. Můžete zvolit **pokračovat** , aby se aplikace normálně obnovila a ukončila, nebo můžete zvolit tlačítko Zastavit, stejně jako při místním spuštění.

1. Podívejte se na okno zásobník volání a zobrazte volání, `x11OpenGLWindow` protože aplikace Visual Studio spustila aplikaci na platformě Linux.

   ![Okno zásobníku volání zobrazující zásobník volání Linux](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Co jste se naučili

V tomto kurzu jste naklonováni základ kódu přímo z GitHubu. Sestavili jste, spustili a rozladíte ho ve Windows bez úprav. Pak jste použili stejný základ kódu s menšími změnami konfigurace pro sestavení, spuštění a ladění na vzdáleném počítači se systémem Linux.

## <a name="next-steps"></a>Další kroky

Další informace o konfiguraci a ladění projektů CMake v sadě Visual Studio:

> [!div class="nextstepaction"]
> [Projekty CMake v sadě Visual Studio](cmake-projects-in-visual-studio.md)<br/><br/>
> [Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)<br/><br/>
> [Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Vlastní nastavení sestavení CMake](customize-cmake-settings.md)<br/><br/>
> [Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md)<br/><br/>
> [Nasazení, spuštění a ladění projektu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [Odkaz na předdefinovaný konfigurační odkaz CMake](cmake-predefined-configuration-reference.md)
>
