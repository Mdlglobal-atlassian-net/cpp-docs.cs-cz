---
title: Vytváření projektů v jazyce C++ pro různé platformy v sadě Visual Studio
description: V tomto kurzu se dozvíte, jak nastavit, zkompilovat a ladit C++ open source projekt cmake v sadě Visual Studio, který cílí na Linux i Windows.
author: mikeblome
ms.topic: tutorial
ms.date: 03/05/2019
ms.openlocfilehash: cd01d5e389bda46fbb05d297ece8e68ef2265725
ms.sourcegitcommit: c53a3efcc5d51fc55fa57ac83cca796b33ae888f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71960726"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Kurz: vytváření C++ projektů pro různé platformy v aplikaci Visual Studio 

Visual Studio C a C++ vývoj už nejsou jenom pro Windows. V tomto kurzu se dozvíte, jak používat C++ Visual Studio pro vývoj pro různé platformy na základě cmake bez nutnosti vytvářet nebo generovat projekty sady Visual Studio. Když otevřete složku, která obsahuje soubor CMakeLists. txt, Visual Studio nakonfiguruje technologii IntelliSense a nastavení sestavení automaticky. Můžete rychle upravovat, sestavovat a ladit kód v místním systému Windows a pak přepnout konfiguraci tak, aby se na platformě Linux, vše ze sady Visual Studio, přepnulo.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * naklonování open source projektu CMake z GitHubu
> * Otevřete projekt v aplikaci Visual Studio 
> * sestavení a ladění cíle spustitelných souborů ve Windows
> * Přidání připojení k počítači se systémem Linux
> * sestavování a ladění stejného cíle v systému Linux

## <a name="prerequisites"></a>Požadavky

- Nastavení sady Visual Studio pro vývoj pro C++ různé platformy
    - Nejprve musíte mít [nainstalovánu aplikaci Visual Studio](https://visualstudio.microsoft.com/vs/). Dále ověřte, že máte nainstalované  **C++ úlohy** pro vývoj **desktopových C++**  aplikací a pro Linux. Tato minimální instalace je jenom 3 GB, v závislosti na instalaci rychlosti stahování by nemělo trvat déle než 10 minut.
- Nastavení počítače se systémem Linux pro vývoj pro C++ různé platformy
    - Visual Studio nevyžaduje žádnou konkrétní distribuci systému Linux. Operační systém může běžet na fyzickém počítači, ve VIRTUÁLNÍm počítači, v cloudu nebo v subsystému Windows pro Linux (WSL). Pro tento kurz se ale vyžaduje grafické prostředí. Proto se WSL nedoporučuje, protože je určen hlavně pro operace příkazového řádku.
    - Nástroje, které Visual Studio vyžaduje na počítači se systémem Linux, C++ jsou: compilers, GDB, SSH, rsync a zip. V systémech založených na Debian můžete tyto závislosti nainstalovat následujícím způsobem.
    
    ```cmd
        sudo apt install -y openssh-server build-essential gdb rsync zip
    ```
    - Sada Visual Studio vyžaduje, aby měl počítač se systémem Linux novější verzi CMake s povoleným režimem serveru (minimálně 3,8). Společnost Microsoft vytvoří univerzální sestavování CMake, které můžete nainstalovat na všechny distribuce se systémem Linux. Toto sestavení doporučujeme použít k zajištění, že máte nejnovější funkce. Binární soubory CMake můžete získat z [větve Microsoftu úložiště cmake](https://github.com/Microsoft/CMake/releases) na GitHubu. Přejít na tuto stránku a stáhnout verzi, která odpovídá vaší systémové architektuře na počítači se systémem Linux, a označit ji jako spustitelný soubor:
    
    ```cmd
        wget <path to binary>
        chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```
    - Můžete zobrazit možnosti spuštění skriptu s `-–help`. Pro určení instalace v cestě **/usr/local** doporučujeme použít možnost `–prefix`, protože se jedná o výchozí umístění, ve kterém sada Visual Studio hledá cmake. Následující příklad ukazuje skript Linux-x86_64. Podle potřeby změňte, pokud používáte jinou cílovou platformu. 
    
    ```cmd
        sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```
- Git pro Windows nainstalovaný na počítači s Windows.
- Účet GitHubu.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Naklonování open source projektu CMake z GitHubu

V tomto kurzu se používá sada odrážek sady SDK na GitHubu, která poskytuje detekci kolizí a simulaci fyziky pro celou řadu různých aplikací. Obsahuje ukázkové spustitelné programy, které se zkompiluje a spouštějí bez nutnosti psát další kód. V tomto kurzu se nemění žádný zdrojový kód ani skripty sestavení. Začněte tím, že naklonujte úložiště bullet3 z GitHubu na počítači, na kterém máte nainstalovanou aplikaci Visual Studio. 

```cmd

git clone https://github.com/bulletphysics/bullet3.git

```

1. V hlavní nabídce sady Visual Studio vyberte **soubor > otevřete > cmake** a přejděte do souboru CMakeLists. txt v kořenovém adresáři úložiště bullet3, který jste právě stáhli.

    ![Nabídka sady Visual Studio pro soubor > Otevřít > CMake](media/cmake-open-cmake.png)

    Po otevření složky se vaše struktura složek zobrazí v **Průzkumník řešení**.

    ![Zobrazení složky Průzkumník řešení sady Visual Studio](media/cmake-bullet3-solution-explorer.png)

    Toto zobrazení vám ukáže přesně to, co je na disku, nikoli logické nebo filtrované zobrazení. Ve výchozím nastavení se skryté soubory nezobrazují. 

2. Kliknutím na tlačítko **Zobrazit všechny soubory** zobrazíte všechny soubory ve složce.

    ![Tlačítko pro zobrazení všech souborů v aplikaci Visual Studio Průzkumník řešení](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Přepnout na zobrazení cílů

Když otevřete složku, která používá CMake, sada Visual Studio automaticky vygeneruje mezipaměť CMake. Tato operace může chvíli trvat, v závislosti na velikosti projektu. 

1. V **okno výstup**vyberte **Zobrazit výstup z** a pak zvolte **cmake** , abyste mohli monitorovat stav procesu generování mezipaměti. Po dokončení operace se zobrazí zpráva "extrakce cílových informací byla dokončena".

    ![Okno výstup sady Visual Studio zobrazující výstup z CMake](media/cmake-bullet3-output-window.png)

    Po dokončení této operace se nakonfiguruje technologie IntelliSense, projekt se může sestavit a můžete ladit aplikaci. Visual Studio teď může poskytnout logické zobrazení řešení na základě cílů zadaných v souborech CMakeLists. 

2. Pomocí tlačítka **řešení a složky** v **Průzkumník řešení** přepněte na zobrazení cílů cmake.

    ![Tlačítko řešení a složky v Průzkumník řešení pro zobrazení cílů CMake](media/cmake-bullet3-show-targets.png)

    Toto zobrazení vypadá jako u sady odrážek:

    ![Zobrazení cílů Průzkumník řešení CMake](media/cmake-bullet3-targets-view.png)

    Zobrazení cílů nabízí intuitivnější zobrazení toho, co je v této zdrojové základně. Můžete vidět, že některé cíle jsou knihovny a jiné jsou spustitelné soubory. 

3. Rozbalením uzlu v zobrazení cílů CMake zobrazíte soubory se zdrojovým kódem, pokud se tyto soubory mohou nacházet na disku.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Přidání explicitní konfigurace Windows x64 – ladění

Visual Studio vytvoří výchozí konfiguraci pro **ladění x64** pro Windows. Konfigurace představují způsob, jakým aplikace Visual Studio rozumí, jaký cíl platformy se bude používat pro CMake. Výchozí konfigurace není reprezentovaná na disku. Když explicitně přidáte konfiguraci, Visual Studio vytvoří soubor s názvem CMakeSettings. JSON, který se naplní nastavením pro všechny zadané konfigurace. 

1. Přidejte novou konfiguraci kliknutím na rozevírací nabídku Konfigurace na panelu nástrojů a výběrem **možnosti spravovat konfigurace...**

    ![Rozevírací seznam pro správu konfigurace](media/cmake-bullet3-manage-configurations.png)

    Tím se otevře [Editor nastavení cmake](customize-cmake-settings.md). Výběrem zeleného znaménka plus na levé straně editoru přidejte novou konfiguraci. Zobrazí se dialogové okno **Přidat konfiguraci do CMakeSettings** .

    ![Přidat konfiguraci do dialogového okna CMakeSettings](media/cmake-bullet3-add-configuration-x64-debug.png)

    Toto dialogové okno obsahuje všechny konfigurace, které jsou součástí sady Visual Studio, a také všechny vlastní konfigurace, které můžete vytvořit. Pokud chcete pokračovat v používání konfigurace **pro ladění x64** , která by měla být první, kterou přidáte. Vyberte **x64 – ladění** a klikněte na **Vybrat**. Tím se vytvoří soubor CMakeSettings. JSON s konfigurací pro **x64 – ladění** a uloží se konfigurace na disk. Změnou parametru název přímo v CMakeSettings. JSON můžete použít libovolné názvy vašich konfigurací.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Nastavení zarážky, sestavení a spuštění ve Windows 

V tomto kroku budeme ladit ukázkový program, který demonstruje knihovnu fyzika s odrážkami.
  
1. V **Průzkumník řešení**vyberte AppBasicExampleGui a rozbalte ji. 
1. Otevřete soubor `BasicExample.cpp`. 
1. Nastavte zarážku, která bude dosaženo po kliknutí na běžící aplikaci. Událost Click je zpracována v metodě v rámci pomocné třídy. K rychlému získání:

    1. Vyberte `CommonRigidBodyBase`, že struktura `BasicExample` je odvozena od kolem řádku 30.
    1. Klikněte pravým tlačítkem a vyberte **Přejít k definici**. Nyní jste v hlavičce CommonRigidBodyBase. h. 
    1. V zobrazení prohlížeče výše byste měli vidět, že jste v `CommonRigidBodyBase`. Napravo můžete vybrat členy k prohlédnutí. Klikněte na rozevírací seznam a vyberte `mouseButtonCallback` pro přechod k definici této funkce v hlavičce.

        ![Panel nástrojů seznam členů sady Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Umístěte zarážku na první řádek v rámci této funkce. To se zobrazí po kliknutí na tlačítko myši v rámci okna aplikace při spuštění v ladicím programu sady Visual Studio.

1. Aplikaci spustíte tak, že vyberete rozevírací seznam spustit s ikonou přehrát, která uvádí "vybrat položku po spuštění" na panelu nástrojů. V rozevíracím seznamu vyberte AppBasicExampleGui. exe. Název spustitelného souboru se nyní zobrazí na spouštěcím tlačítku:

    ![Rozevírací seznam pro spuštění panelu nástrojů sady Visual Studio pro výběr položky po spuštění](media/cmake-bullet3-launch-button.png)

5.  Kliknutím na tlačítko spustit sestavíte aplikaci a potřebné závislosti a pak ji spustíte s připojeným ladicím programem sady Visual Studio. Po chvíli se spustí běžící aplikace:

    ![Ladění aplikace systému Windows v aplikaci Visual Studio](media/cmake-bullet3-launched.png)

6. Přesuňte myš do okna aplikace a potom kliknutím na tlačítko aktivujte zarážku. Tím se Visual Studio vrátí zpátky do popředí s editorem ukazujícím čáru, kde je provádění pozastaveno. Budete moci zkontrolovat proměnné aplikace, objekty, vlákna a paměť. Kód lze procházet interaktivně. Kliknutím na tlačítko **pokračovat** můžete aplikaci obnovit a ukončit normálně nebo ukončit provádění v rámci sady Visual Studio pomocí tlačítka zastavit.

##  <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Přidejte konfiguraci pro Linux a připojte se ke vzdálenému počítači.

1. Teď přidejte konfiguraci pro Linux. V zobrazení **Průzkumník řešení** klikněte pravým tlačítkem na soubor CMakeSettings. JSON a vyberte **Přidat konfiguraci**. Zobrazí se stejná dialogová okna Přidat konfiguraci do CMakeSettings jako předtím. Vyberte **Linux – ladění** tentokrát a pak uložte soubor CMakeSettings. JSON (CTRL + s). 
2. Teď v rozevíracím seznamu konfigurace vyberte **Linux-Debug** .

    ![Rozevírací seznam spuštění konfigurace s x64 – ladění a Linux – možnosti ladění](media/cmake-bullet3-linux-configuration-item.png)

    Pokud se k systému Linux připojujete poprvé, zobrazí se dialogové okno **připojit ke vzdálenému systému** .

    ![Dialogové okno připojení k vzdálenému systému Visual Studio](media/cmake-bullet3-connection-manager.png)

    Pokud jste už přidali vzdálené připojení, můžete toto okno otevřít tak, že přejdete na **nástroje > možnosti > > Správce připojení pro různé platformy**.
 
3. Zadejte [informace o připojení k počítači se systémem Linux] (Connect-to-Remote-Linux-computer.md] a klikněte na **připojit**. Visual Studio přidá tento počítač jako výchozí připojení pro **Linux-Debug**jako výchozí připojení k CMakeSettings. JSON. Bude také stahovat hlavičky ze vzdáleného počítače, takže získáte [technologii IntelliSense specifickou pro toto vzdálené připojení](https://docs.microsoft.com/en-us/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense). Sada Visual Studio nyní odešle soubory do vzdáleného počítače a vygeneruje mezipaměť CMake ve vzdáleném systému. Tyto kroky můžou nějakou dobu trvat v závislosti na rychlosti vaší sítě a výkonu vzdáleného počítače. Budete vědět, že je to hotové, když se v okně výstup CMake zobrazí zpráva "extrakce cílových informací byla dokončena".

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Nastavení zarážky, sestavení a spuštění v systému Linux

Vzhledem k tomu, že se jedná o desktopovou aplikaci, je nutné zadat další konfigurační informace pro konfiguraci ladění. 

1. V zobrazení cílů CMake klikněte pravým tlačítkem na AppBasicExampleGui a vyberte **nastavení ladění a spouštění** . otevře se soubor Launch. vs. JSON, který se nachází v podsložce skryté **. vs** . Tento soubor je místní pro vaše vývojové prostředí. Můžete ho přesunout do kořenového adresáře projektu, pokud ho chcete vrátit se změnami a uložit ho do svého týmu. V tomto souboru byla přidána konfigurace pro AppBasicExampleGui. Tato výchozí nastavení fungují ve většině případů, ale vzhledem k tomu, že se jedná o desktopovou aplikaci, je potřeba zadat nějaké další informace, abyste mohli program spustit způsobem tak, jak ho vidíte na našem počítači se systémem Linux. 
2. Musíte znát hodnotu proměnné prostředí `DISPLAY` na svém počítači se systémem Linux, spusťte tento příkaz a získejte ho.

    ```cmd
    echo $DISPLAY
    ```

    V konfiguraci pro AppBasicExampleGui je pole parametrů "pipeArgs". V rámci je řádek "$ {debuggerCommand}". Toto je příkaz, který spouští GDB na vzdáleném počítači. Visual Studio musí před spuštěním tohoto příkazu Exportovat zobrazení do tohoto kontextu. Například pokud hodnota zobrazení: 1, upravte tento řádek následujícím způsobem:

    ```cmd
    "export DISPLAY=:1;${debuggerCommand}",
    ```
3. Nyní Pokud chcete spustit a ladit naši aplikaci, zvolte v rozevíracím seznamu **Vybrat položku při spuštění** na panelu nástrojů a zvolte možnost AppBasicExampleGui. Nyní stiskněte toto tlačítko nebo stiskněte klávesu **F5**. Tím se sestaví aplikace a její závislosti na vzdáleném počítači se systémem Linux a potom se spustí pomocí připojeného ladicího programu sady Visual Studio. Na vzdáleném počítači se systémem Linux by se mělo zobrazit okno aplikace.

4. Přesuňte myš do okna aplikace, klikněte na tlačítko a zarážku se objeví. Spuštění programu se pozastaví, Visual Studio se vrátí zpátky na popředí a na zarážku. V aplikaci Visual Studio by se měla zobrazit také okno konzoly pro Linux. Toto okno poskytuje výstup ze vzdáleného počítače se systémem Linux a může také přijímat vstupy pro `stdin`. Podobně jako u libovolného okna sady Visual Studio může být ukotveno, kde je dáváte přednost, a jeho umístění bude v budoucích relacích trvalé.

    ![Okno konzoly Visual Studio Linux](media/cmake-bullet3-linux-console.png)

5. Pomocí sady Visual Studio můžete interaktivně kontrolovat proměnné aplikace, objekty, vlákna, paměť a krokovat kód. Tentokrát to ale uděláte na vzdáleném počítači se systémem Linux namísto místního prostředí systému Windows. Kliknutím na tlačítko **pokračovat** můžete aplikaci obnovit a ukončit normálně, nebo můžete stisknout tlačítko Zastavit stejně jako při místním spuštění.

6. Podívejte se na okno zásobník volání a zobrazte volání `x11OpenGLWindow`, protože aplikace Visual Studio spustila aplikaci na platformě Linux.

    ![Okno zásobníku volání zobrazující zásobník volání Linux](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Co jste se naučili 

V tomto kurzu jste viděli základ kódu, který je Klonovaný přímo z GitHubu, a sestavený, spuštěný a laděný ve Windows bez úprav. Toto bylo základem kódu, s menšími změnami konfigurace, bylo sestaveno, spuštěno a laděno na vzdáleném počítači se systémem Linux. 

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
