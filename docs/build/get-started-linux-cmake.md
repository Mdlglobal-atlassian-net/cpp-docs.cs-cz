---
title: Vytváření projektů v jazyce C++ pro různé platformy v sadě Visual Studio
description: Jak nastavit, zkompilovat a ladit projekt C++ open source CMake v sadě Visual Studio, který se zaměřuje na Linux i Windows.
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: aac536f488cf22adf5aa835c9fe5b884fc5d7298
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328748"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Kurz: Vytvoření projektů napříč platformami jazyka C++ v sadě Visual Studio

Vývoj Visual Studio C a C++ už není jen pro Windows. Tento kurz ukazuje, jak používat Visual Studio pro vývoj napříč platformami C++ ve Windows a Linuxu. Je založen na CMake, takže není nutné vytvářet nebo generovat projekty sady Visual Studio. Když otevřete složku, která obsahuje soubor CMakeLists.txt, Visual Studio nakonfiguruje nastavení Technologie IntelliSense a sestavení automaticky. Můžete rychle začít upravovat, vytváření a ladění kódu místně v systému Windows. Potom přepněte konfiguraci, abyste to udělali stejně v Linuxu, vše z visual studia.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> * klonovat open-source projekt CMake z GitHubu
> * otevření projektu v sadě Visual Studio
> * sestavení a ladění spustitelného cíle v systému Windows
> * přidání připojení k počítači s Linuxem
> * sestavení a ladění stejného cíle na Linuxu

## <a name="prerequisites"></a>Požadavky

* Nastavení visual studia pro vývoj c++ napříč platformami
  * Nejprve [nainstalujte Visual Studio](https://visualstudio.microsoft.com/vs/) a zvolte vývoj plochy s **vývojem C++** a **Linuxu s úlohami C++**. Tato minimální instalace je pouze 3 GB. V závislosti na rychlosti stahování by instalace neměla trvat déle než 10 minut.

* Nastavení počítače s Linuxem pro vývoj c++ napříč platformami
  * Visual Studio nevyžaduje žádnou konkrétní distribuci Linuxu. Operační ho může běžet na fyzickém počítači, ve virtuálním počítači nebo v cloudu. Můžete také použít podsystém Windows pro Linux (WSL). Pro účely tohoto kurzu je však vyžadováno grafické prostředí. Wsl se zde nedoporučuje, protože je určen především pro operace příkazového řádku.
  * Visual Studio vyžaduje tyto nástroje na počítači s Linuxem: Kompilátory Jazyka C++, gdb, ssh, rsync, ninja a zip. V systémech založených na Debianu můžete pomocí tohoto příkazu nainstalovat tyto závislosti:

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync ninja-build zip
    ```

  * Visual Studio vyžaduje nejnovější verzi CMake na počítači s Linuxem, který má zapnutý režim serveru (alespoň 3.8). Společnost Microsoft vytváří univerzální sestavení CMake, které můžete nainstalovat na libovolné distro Linuxu. Doporučujeme použít toto sestavení k zajištění, že máte nejnovější funkce. Můžete získat binární soubory CMake z [rozdvojené sady Microsoft úložiště CMake](https://github.com/Microsoft/CMake/releases) na GitHubu. Přejděte na tuto stránku a stáhněte si verzi, která odpovídá architektuře systému v počítači s Linuxem, a označte ji jako spustitelný soubor:

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * Můžete zobrazit možnosti pro spuštění `-–help`skriptu s . Doporučujeme použít `–prefix` možnost určit instalaci v **/usr** cestu, protože **/usr/bin** je výchozí umístění, kde Visual Studio hledá CMake. Následující příklad ukazuje skript Linux-x86_64. Pokud používáte jinou cílovou platformu, změňte ji podle potřeby.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Git pro windows nainstalovaný na vašem počítači se systémem Windows.
* Účet GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Klonování open-source projektu CMake z GitHubu

Tento kurz používá bullet fyziky SDK na GitHub. Poskytuje simulace detekce kolizí a fyziky pro mnoho aplikací. Sada SDK obsahuje ukázkové spustitelné programy, které kompilují a spouštějí bez nutnosti psát další kód. Tento kurz nemění žádný zdrojový kód nebo vytvářet skripty. Chcete-li spustit, *klonovat bullet3* úložiště z GitHub u počítače, kde máte nainstalovaný Visual Studio.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. V hlavní nabídce Visual Studia zvolte **Soubor > Otevřít > CMake**. Přejděte do souboru CMakeLists.txt v kořenovém adresáři souboru bullet3, který jste právě stáhli.

    ![Nabídka Visual Studia pro > souboru otevřít > CMake](media/cmake-open-cmake.png)

    Jakmile složku otevřete, struktura složek se zobrazí v **Průzkumníku řešení**.

    ![Zobrazení složky Průzkumníka řešení sady Visual Studio](media/cmake-bullet3-solution-explorer.png)

    Toto zobrazení zobrazuje přesně to, co je na disku, nikoli logické nebo filtrované zobrazení. Ve výchozím nastavení se nezobrazují skryté soubory.

1. Chcete-li zobrazit všechny soubory ve složce, zvolte tlačítko **Zobrazit všechny soubory.**

    ![Visual Studio Průzkumník řešení Zobrazit všechny soubory tlačítko tlačítko](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Přepnout do zobrazení cílů

Když otevřete složku, která používá CMake, Visual Studio automaticky vygeneruje mezipaměť CMake. Tato operace může trvat několik okamžiků, v závislosti na velikosti projektu.

1. V **okně Výstup**vyberte **Zobrazit výstup z** a pak zvolte **CMake** pro sledování stavu procesu generování mezipaměti. Po dokončení operace se zobrazí "Extrakce informací o cíli dokončena".

   ![Okno Visual Studio Output zobrazující výstup z CMake](media/cmake-bullet3-output-window.png)

   Po dokončení této operace je nakonfigurována technologie IntelliSense. Můžete vytvořit projekt a ladit aplikace. Visual Studio nyní zobrazuje logické zobrazení řešení na základě cílů zadaných v souborech CMakeLists.

1. Pomocí tlačítka **Řešení a složky** v **Průzkumníku řešení** přepněte do zobrazení cílů CMake.

   ![Tlačítko Řešení a složky v Průzkumníku řešení pro zobrazení cílů CMake](media/cmake-bullet3-show-targets.png)

   Zde je to, co toto zobrazení vypadá pro Bullet SDK:

   ![Zobrazení cílů aplikace CMake řešení](media/cmake-bullet3-targets-view.png)

   Zobrazení cílů poskytuje intuitivnější zobrazení toho, co je v této zdrojové základně. Můžete vidět, že některé cíle jsou knihovny a jiné jsou spustitelné soubory.

1. Rozbalte uzel v zobrazení CMake Targets View, abyste viděli jeho soubory zdrojového kódu, ať už jsou tyto soubory umístěny na disku.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Přidání explicitní konfigurace windows x64-debug

Visual Studio vytvoří výchozí konfiguraci **x64-Debug** pro Windows. Konfigurace jsou jak Visual Studio chápe, jaký cíl platformy se bude používat pro CMake. Výchozí konfigurace není na disku reprezentována. Pokud explicitně přidáte konfiguraci, visual studio vytvoří soubor s názvem *CMakeSettings.json*. Je naplněn nastavením pro všechny konfigurace, které zadáte.

1. Přidejte novou konfiguraci. Otevřete rozevírací panel **Konfigurace** na panelu nástrojů a vyberte **Spravovat konfigurace**.

   ![Rozevírací rozevírací pravidla Spravovat konfiguraci](media/cmake-bullet3-manage-configurations.png)

   Otevře se [Editor nastavení CMake.](customize-cmake-settings.md) Vyberte zelené znaménko plus na levé straně editoru a přidejte novou konfiguraci. Zobrazí se dialogové okno **Přidat konfiguraci do cMakeSettings.**

   ![Dialogové okno Přidat konfiguraci do cMakeSettings](media/cmake-bullet3-add-configuration-x64-debug.png)

   Toto dialogové okno zobrazuje všechny konfigurace, které jsou součástí sady Visual Studio, plus všechny vlastní konfigurace, které vytvoříte. Pokud chcete pokračovat v používání konfigurace **x64-Debug,** měl by to být první, který přidáte. Vyberte **x64-Ladění**a pak zvolte **tlačítko Vybrat.** Visual Studio vytvoří soubor CMakeSettings.json s konfigurací pro **x64-Debug**a uloží jej na disk. Můžete použít libovolné názvy, které se vám líbí pro vaše konfigurace změnou name parametr přímo v CMakeSettings.json.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Nastavení zarážky, sestavení a spuštění v systému Windows

V tomto kroku budeme ladit ukázkový program, který demonstruje bullet fyziky knihovny.
  
1. V **Průzkumníku řešení**vyberte AppBasicExampleGui a rozbalte ji.

1. Otevřete soubor `BasicExample.cpp`.

1. Nastavte zarážku, která se dostane do přístupů po klepnutí na tlačítko v běžící aplikaci. Událost click je zpracována metodou v rámci pomocné třídy. Chcete-li se tam rychle dostat:

   1. Vyberte, `CommonRigidBodyBase` že `BasicExample` struktura je odvozena od. Je to kolem linky 30.

   1. Klikněte pravým tlačítkem myši a zvolte **Přejít na definici**. Nyní jste v záhlaví CommonRigidBodyBase.h.

   1. V zobrazení prohlížeče nad zdrojem byste měli vidět, `CommonRigidBodyBase`že se najdete v aplikaci . Vpravo můžete vybrat členy, které chcete prozkoumat. Otevřete rozevírací `mouseButtonCallback` seznam a vyberte, chcete-li přejít na definici této funkce v záhlaví.

      ![Panel nástrojů seznamu členů sady Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Umístěte zarážku na první řádek v rámci této funkce. Získá přístup, když kliknete na tlačítko myši v okně aplikace, při spuštění v ladicím programu sady Visual Studio.

1. Chcete-li aplikaci spustit, vyberte rozbalovací panel spuštění na panelu nástrojů. Je to ten s ikonou zelené hry, která říká "Vyberte položku po spuštění". V rozevíracím souboru vyberte AppBasicExampleGui.exe. Název spustitelného souboru se nyní zobrazuje na spouštěcím tlačítku:

   ![Rozevírací seznam panelu nástrojů sady Visual Studio pro vybrat položku po spuštění](media/cmake-bullet3-launch-button.png)

1. Zvolte tlačítko spuštění k sestavení aplikace a nezbytné závislosti a spusťte ji s připojeným ladicím programem Visual Studio. Po několika okamžicích se zobrazí spuštěná aplikace:

   ![Visual Studio ladění aplikace systému Windows](media/cmake-bullet3-launched.png)

1. Přesuňte myš do okna aplikace a kliknutím na tlačítko aktivujte zarážku. Zarážka přináší Visual Studio zpět do popředí a editor zobrazí řádek, kde je pozastaveno provádění. Můžete zkontrolovat proměnné aplikace, objekty, vlákna a paměť nebo interaktivně procházet kód. Chcete-li aplikaci obnovit, zvolte **Pokračovat** a pak ji ukončit normálně. Nebo zastavit provádění v rámci sady Visual Studio pomocí tlačítka stop.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Přidání konfigurace Linuxu a připojení ke vzdálenému počítači

1. Přidejte konfiguraci Linuxu. Klepněte pravým tlačítkem myši na soubor CMakeSettings.json v zobrazení **Průzkumník řešení** a vyberte příkaz **Přidat konfiguraci**. Zobrazí se stejné dialogové okno Přidat konfiguraci do cMakeSettings jako dříve. Tentokrát vyberte **Linux-Debug** a pak uložte soubor CMakeSettings.json (ctrl + s).

1. V rozbalovací části konfigurace vyberte **Linux-Ladění.**

   ![Spuštění rozevíracího nabídky konfigurace s možnostmi X64-Debug a Linux-Debug](media/cmake-bullet3-linux-configuration-item.png)

   Pokud se připojujete k systému Linux poprvé, zobrazí se dialogové okno **Připojit ke vzdálenému systému.**

   ![Dialogové okno Připojení ke vzdálenému systému v sadě Visual Studio](media/cmake-bullet3-connection-manager.png)

   Pokud jste již přidali vzdálené připojení, můžete toto okno otevřít tak, že přejdete do **pole Nástroje > možnosti > aplikace Cross Platform > Connection Manager**.

1. Zadejte [informace o připojení k počítači s Linuxem](/cpp/linux/connect-to-your-remote-linux-computer) a zvolte **Připojit**. Visual Studio přidá tento počítač jako CMakeSettings.json jako výchozí připojení pro **Linux-Ladění**. To také stáhne záhlaví ze vzdáleného počítače, takže dostanete [IntelliSense specifické pro toto vzdálené připojení](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense). Dále Visual Studio odešle soubory do vzdáleného počítače a generuje mezipaměť CMake ve vzdáleném systému. Tyto kroky mohou nějakou dobu trvat v závislosti na rychlosti sítě a napájení vzdáleného počítače. Budete vědět, že je kompletní, když se ve výstupním okně CMake zobrazí zpráva "Extrakce cílových informací".

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Nastavení zarážky, sestavení a spuštění na Linuxu

Vzhledem k tomu, že se jedná o desktopovou aplikaci, je třeba zadat některé další informace o konfiguraci konfigurace ladění.

1. V zobrazení Cíle CMake klikněte pravým tlačítkem myši na Položku AppBasicExampleGui a zvolte **Nastavení ladění a spuštění** a otevřete soubor launch.vs.json, který je ve skryté podsložce **.vs.** Tento soubor je místní vývojové prostředí. Můžete jej přesunout do kořenového adresáře projektu, pokud chcete zkontrolovat a uložit se svým týmem. V tomto souboru byla přidána konfigurace pro AppBasicExampleGui. Tato výchozí nastavení fungují ve většině případů, ale ne zde. Vzhledem k tomu, že se jedná o desktopovou aplikaci, musíte poskytnout některé další informace pro spuštění programu, abyste jej mohli vidět na počítači s Linuxem.

1. Chcete-li najít hodnotu `DISPLAY` proměnné prostředí v počítači s Linuxem, spusťte tento příkaz:

   ```cmd
   echo $DISPLAY
   ```

   V konfiguraci pro AppBasicExampleGui je pole parametrů" pipeArgs". Obsahuje řádek: "${debuggerCommand}". Je to příkaz, který spouští gdb na vzdáleném počítači. Visual Studio musí exportovat zobrazení do tohoto kontextu před spuštěním tohoto příkazu. Pokud je `:1`například hodnota zobrazení , upravte tento řádek takto:

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. Spusťte a laděte aplikaci. Otevřete rozevírací seznam **Vybrat položku po spuštění** na panelu nástrojů a zvolte **AppBasicExampleGui**. Dále zvolte zelenou ikonu přehrávání na panelu nástrojů nebo stiskněte **klávesu F5**. Aplikace a její závislosti jsou postaveny na vzdáleném počítači s Linuxem a poté spuštěny s připojeným ladicím programem visual studio. Na vzdáleném počítači s Linuxem by se mělo zobrazit okno aplikace.

1. Přesuňte myš do okna aplikace a klepněte na tlačítko. Zarážka je přístupů. Spuštění programu pozastaví, Visual Studio se vrátí do popředí a zobrazí se zarážka. Měli byste také vidět Linux Console Window se zobrazí v sadě Visual Studio. Okno poskytuje výstup ze vzdáleného počítače S Linuxem `stdin`a může také přijímat vstup pro . Stejně jako každé okno sady Visual Studio můžete ukotvit, kde chcete vidět. Jeho pozice přetrvává v budoucích zasedáních.

   ![Okno konzoly Visual Studio Linux](media/cmake-bullet3-linux-console.png)

1. Můžete zkontrolovat proměnné aplikace, objekty, vlákna, paměť a krokovat kód interaktivně pomocí sady Visual Studio. Ale tentokrát to všechno děláte na vzdáleném počítači s Linuxem namísto místního prostředí Windows. Můžete zvolit **Pokračovat,** chcete-li, aby aplikace normálně pokračovala a ukončuje, nebo můžete zvolit tlačítko stop, stejně jako u místního spuštění.

1. Podívejte se na okno zásobníku `x11OpenGLWindow` volání a zobrazte volání od spuštění aplikace Visual Studio na Linuxu.

   ![Okno Zásobník volání zobrazující zásobník volání Linuxu](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Co jste se naučili

V tomto kurzu jste naklonovali základ kódu přímo z GitHubu. Vytvořili jste, běželi a ladili v systému Windows bez úprav. Potom jste použili stejný základ kódu s menšími změnami konfigurace k sestavení, spuštění a ladění na vzdáleném počítači s Linuxem.

## <a name="next-steps"></a>Další kroky

Další informace o konfiguraci a ladění projektů CMake v sadě Visual Studio:

> [!div class="nextstepaction"]
> [CMake projekty v sadě Visual Studio](cmake-projects-in-visual-studio.md)<br/><br/>
> [Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)<br/><br/>
> [Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Vlastní nastavení sestavení CMake](customize-cmake-settings.md)<br/><br/>
> [Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md)<br/><br/>
> [Nasazení, spuštění a ladění projektu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CMake předdefinovaný odkaz na konfiguraci](cmake-predefined-configuration-reference.md)
>
