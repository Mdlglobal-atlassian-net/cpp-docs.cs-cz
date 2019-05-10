---
title: Vytváření multiplatformních projektů v jazyce C++ v sadě Visual Studio
description: Tento kurz ukazuje, jak nastavit, kompilaci a ladit projekt CMake open-source jazyka C++ v sadě Visual Studio, který cílí na Linux i Windows.
author: mikeblome
ms.topic: tutorial
ms.date: 03/05/2019
ms.openlocfilehash: f184cc2ce3eaf3adcc936bd723019956b5b23dc9
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220855"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Kurz: Vytváření multiplatformních projektů v jazyce C++ v sadě Visual Studio 

Vývoj pro Visual Studio C a C++ není k dispozici už jenom pro Windows. Tento kurz ukazuje, jak pomocí sady Visual Studio pro jazyk C++ pro vývoj napříč platformami podle CMake, aniž byste museli vytvářet nebo generování projektů sady Visual Studio. Když otevřete složku, která obsahuje soubor CMakeLists.txt, Visual Studio nakonfiguruje nastavení technologie IntelliSense a sestavení automaticky. Můžete rychle se úpravy, sestavování a ladění kódu místně na Windows a pak přepnout konfiguraci stejný postup provést v Linuxu, z Visual Studia.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * naklonujte projekt open source CMake z Githubu
> * Otevřete projekt v sadě Visual Studio 
> * Vytvářejte a laďte cíl spustitelný soubor na Windows
> * Přidat připojení k počítači s Linuxem
> * Vytvářejte a laďte stejného cíle v Linuxu

## <a name="prerequisites"></a>Požadavky

- Instalace sady Visual Studio pro vývoj v jazyce C++ pro různé platformy
    - Nejdřív je potřeba mít [nainstalovanou sadu Visual Studio](https://visualstudio.microsoft.com/vs/). Dále ověřte, že máte **vývoj desktopových aplikací pomocí C++** a **vývoj pro Linux v C++ úlohy** nainstalované. Tato minimální instalace je jenom 3 GB, v závislosti na vámi stahovaných rychlost instalaci neměla by mít více než 10 minut.
- Nastavit počítač s Linuxem pro vývoj v jazyce C++ pro různé platformy
    - Visual Studio nevyžaduje žádné konkrétní distribuci systému Linux. Operační systém, mohou běžet na fyzický počítač, virtuální počítač, cloudu nebo subsystému Windows pro Linux (WSL). Pro účely tohoto kurzu je grafické prostředí však vyžaduje; proto WSL se nedoporučuje, protože je určený primárně pro operace příkazového řádku.
    - Nástroje, které sada Visual Studio vyžaduje na počítači s Linuxem jsou: Kompilátory C++, GDB, ssh a zip. Na základě systémy Debian můžete nainstalovat tyto závislosti následujícím způsobem.
    
    ```cmd
        sudo apt install -y openssh-server build-essential gdb zip
    ```
    - Visual Studio vyžaduje počítač s Linuxem nejnovější verzi CMake, s povoleným režimem serveru (nejméně 3.8). Microsoft vytváří univerzální sestavení CMake, který můžete nainstalovat na libovolný distribuce Linuxu. Doporučujeme používat toto sestavení, abyste měli jistotu, že máte nejnovější funkce. Můžete získat binární soubory CMake z [Microsoft forku úložiště CMake](https://github.com/Microsoft/CMake/releases) na Githubu. Přejděte na příslušnou stránku a stáhněte si verzi, která odpovídá architektuře systému na počítač s Linuxem a označte ji jako spustitelný soubor:
    
    ```cmd
        wget <path to binary>
        chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```
    - Zobrazí se možnosti pro spuštění skriptu pomocí `-–help`. Doporučujeme použít `–prefix` možnost zadat v instalaci **/usr/local** cestu vzhledem k tomu, který je výchozím umístěním, kde sady Visual Studio vyhledá CMake. Následující příklad ukazuje Linux x86_64 skriptu. Změňte podle potřeby, pokud používáte jinou cílovou platformu. 
    
    ```cmd
        sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```
- Git pro windows nainstalované v počítači Windows.
- Účet GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>naklonujte projekt open source CMake z Githubu

Tento kurz používá SDK fyzika odrážek v Githubu, který poskytuje detekce kolizí a fyzika simulace pro širokou škálu různých aplikací. Obsahuje ukázkové spustitelné programy, které zkompilovat a spustit bez nutnosti psát další kód. V tomto kurzu nelze upravovat zdrojový kód nebo skripty pro sestavení. Pokud chcete začít, naklonujte bullet3 úložiště z Githubu na počítači ve kterém máte nainstalovanou sadu Visual Studio. 

```cmd

git clone https://github.com/bulletphysics/bullet3.git

```

1. V hlavní nabídce sady Visual Studio zvolte **soubor > Otevřít > CMake** a přejděte na soubor CMakeLists.txt v kořenovém adresáři úložiště bullet3, který jste si právě stáhli.

    ![Visual Studio nabídku pro soubor > Otevřít > CMake](media/cmake-open-cmake.png)

    Jakmile otevřete složku, vaše struktura složky se nebude zobrazovat v **Průzkumníka řešení**.

    ![Zobrazení složky v Průzkumníku řešení sady Visual Studio](media/cmake-bullet3-solution-explorer.png)

    Toto zobrazení uvádí, co přesně je na disku, nejsou logické nebo filtrované zobrazení. Ve výchozím nastavení nezobrazuje skryté soubory. 

2. Stisknutím klávesy **zobrazit všechny soubory** tlačítko, abyste viděli všechny soubory ve složce.

    ![Visual Studio řešení Explorer tlačítko Zobrazit všechny soubory](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Přepnout na zobrazení cílů

Když otevřete složku, která používá CMake Visual Studio automaticky vytvoří mezipaměť CMake. Tato operace může chvíli trvat, v závislosti na velikosti projektu. 

1. V **okno výstup**vyberte **zobrazit výstup z:** a klikněte na tlačítko **CMake** monitorování stavu procesu generování mezipaměti. Po dokončení operace se říká "Extrakce cílových informací Hotovo".

    ![Visual Studio výstupní okno výstup z CMake](media/cmake-bullet3-output-window.png)

    Po dokončení této operace IntelliSense je nakonfigurovaný, můžete vytvořit projekt a můžete ladit aplikace. Visual Studio teď můžete zadat logické zobrazení řešení založené na cílech podle souborů CMakeLists. 

2. Použití **řešení a složky** tlačítko **Průzkumníka řešení** přepnout na zobrazení cílů CMake.

    ![Tlačítko řešení a složky v Průzkumníku řešení zobrazíte CMake, zaměřuje zobrazení](media/cmake-bullet3-show-targets.png)

    Tady je co zobrazení vypadá podobně jako pro sadu SDK odrážku:

    ![Zobrazení cílů CMake Průzkumníka řešení](media/cmake-bullet3-targets-view.png)

    Zobrazení cílů poskytuje mnohem intuitivnější zobrazení co je v tomto základ zdroje. Zobrazí se některé cíle jsou knihovny a další jsou spustitelné soubory. 

3. Rozbalte uzel v zobrazení cílů CMake zobrazíte její soubory zdrojového kódu, bez ohledu na tyto soubory mohou být umístěny na disku.

## <a name="set-a-breakpoint-build-and-run"></a>Nastavit zarážku, sestavení a spuštění

V tomto kroku budeme budete ladit ukázkový program, který ukazuje knihovny fyzika odrážky.
  
1. V **Průzkumníka řešení**AppBasicExampleGui vyberte a rozbalte ho. 
1. Otevřete soubor `BasicExample.cpp`. 
1. Nastavte zarážku, která dosáhne po kliknutí na ve spuštěné aplikaci. Událost click probíhá v metodě v rámci třídy pomocné rutiny. Pokud chcete rychle získat existuje:

    1. Vyberte `CommonRigidBodyBase` , který struktury `BasicExample` je odvozen z kolem řádku 30.
    1. Klikněte pravým tlačítkem a zvolte **přejít k definici**. Nyní jsou v hlavičce CommonRigidBodyBase.h. 
    1. V prohlížeči výše, váš zdroj byste měli vidět, že jste v `CommonRigidBodyBase`. Na pravé straně můžete vybrat členy k prozkoumání. Klikněte na rozevírací seznam a vyberte `mouseButtonCallback` přejít k definici této funkce v záhlaví.

        ![Panel nástrojů seznam členů Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Umístíte zarážky na prvním řádku v rámci této funkce. To se dostanou po kliknutí na tlačítko myši v okně aplikace při spuštění v ladicím programu sady Visual Studio.

1. Ke spuštění aplikace, vyberte rozevírací seznam s na ikonu přehrávání s textem "Vybrat položku při spuštění" na panelu nástrojů na trh. V rozevíracím seznamu vyberte AppBasicExampleGui.exe. Název spustitelného souboru se nyní zobrazí na tlačítku spuštění:

    ![Panel nástrojů Visual Studio spusťte rozevíracího seznamu vyberte položku při spuštění](media/cmake-bullet3-launch-button.png)

5.  Stisknutím tlačítka spuštění sestavit aplikaci potřebné závislosti a pak ji spustit v ladicím programu sady Visual Studio připojené. Spuštěné aplikace se zobrazí po chvíli se:

    ![Visual Studio, ladění aplikace Windows](media/cmake-bullet3-launched.png)

6. Najeďte myší do okna aplikace a pak klikněte na tlačítko aktivovat zarážku. Visual Studio otevře zpět na popředí v editoru zobrazují řádku, kde je spuštění pozastaveno. Budete moci kontrolovat aplikace proměnné, objekty, vlákna a paměti. Můžete krokovat kód interaktivně. Můžete kliknout na **pokračovat** které umožní aplikaci pokračovat a ukončit normálně nebo ukončí provádění v rámci sady Visual Studio pomocí tlačítka Zastavit.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Přidat explicitní x64 ladění konfigurace Windows

Zatím jste použili výchozí **x64 ladění** konfigurace pro Windows. Konfigurace se, jak Visual Studio rozumí jakou platformu cíl se bude používat pro CMake. Výchozí konfigurace není zastoupen na disku. Když explicitně přidat konfiguraci, Visual Studio vytvoří soubor s názvem souboru CMakeSettings.json, který je vyplněný s nastavením pro všechny konfigurace, kterou zadáte. 

1. Přidat novou konfiguraci kliknutím na konfiguraci rozevíracího seznamu na panelu nástrojů a vyberete **spravovat konfigurace...**

    ![Správa konfigurace rozevíracího seznamu](media/cmake-bullet3-manage-configurations.png)

    **Přidat konfiguraci cmakesettings na pozici** zobrazí se dialogové okno.

    ![Přidání konfigurace do dialogového okna cmakesettings na pozici](media/cmake-bullet3-add-configuration-x64-debug.png)

    Toto dialogové okno zobrazuje všechny konfigurace, které jsou součástí sady Visual Studio, stejně jako všechny vlastní konfigurace, které vytvoříte. Pokud chcete dál používat výchozí **x64 ladění** konfigurace, které by měly být první z nich můžete přidat. Přidáním této konfigurace bude možné přepínat mezi Windows a Linuxem konfigurace. Vyberte **x64 ladění** a klikněte na tlačítko **vyberte**. Tím se vytvoří soubor CMakeSettings.json s konfigurací pro **x64 ladění** a přepínače sady Visual Studio na místo výchozího s použitím této konfigurace. Zobrazí se rozevírací konfigurace už říká "(výchozí)" jako součást názvu. Můžete použít libovolné názvy pro vaše konfigurace tak, že změníte název parametru přímo v souboru CMakeSettings.json.

##  <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Přidat konfiguraci systému Linux a připojení ke vzdálenému počítači

1. Nyní přidejte konfiguraci systému Linux. Klikněte pravým tlačítkem na souboru CMakeSettings.json **Průzkumníka řešení** zobrazit a vybrat **Přidat konfiguraci**. Zobrazí se stejnou konfigurací přidat do dialogového okna cmakesettings na pozici jako před. Vyberte **Linux ladění** tentokrát potom uložte souboru CMakeSettings.json. 
2. Teď vyberte **Linux ladění** v rozevíracího seznamu konfigurace.

    ![Spuštění konfigurace rozevírací seznam s X64 ladění a možnosti ladění systému Linux](media/cmake-bullet3-linux-configuration-item.png)

    Pokud to je poprvé, kdy se připojujete k systému Linux **připojit ke vzdálenému systému** zobrazí se dialogové okno.

    ![Visual Studio Connect do dialogového okna vzdáleného systému](media/cmake-bullet3-connection-manager.png)

    Pokud jste už přidali vzdáleného připojení toto okno můžete otevřít tak, že přejdete do **nástroje > Možnosti > pro různé platformy > Správce připojení**.
 
3. Zadání informací o připojení pro počítač s Linuxem a klikněte na tlačítko **připojit**. Visual Studio přidá jako výchozí pro tento počítač jde o CMakeSettings.json **Linux ladění**. To se také stáhne hlavičky ze vzdáleného počítače tak, aby získáte IntelliSense specifické pro daný počítač můžete ji použít. Teď Visual Studio odeslat soubory na vzdálený počítač, pak je generováním mezipaměti CMake existuje a po dokončení sady Visual Studio se nakonfiguruje pro stejný zdroj základní pomocí tohoto vzdáleného počítače s Linuxem. Tyto kroky může chvíli trvat v závislosti na rychlosti sítě a výkon vzdáleného počítače. Budete vědět, že to je dokončeno, když se zobrazí zpráva "Extrakce cílových informací Hotovo" ve výstupním okně CMake.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Nastavit zarážku, sestavovat a provozovat v Linuxu

Protože je to aplikace klasické pracovní plochy, budete muset zadat nějaké další informace o konfiguraci pro konfiguraci ladění. 

1. V zobrazení cílů CMake, klikněte pravým tlačítkem na AppBasicExampleGui a zvolte **nastavení ladění a spouštění** k otevření souboru launch.vs.json, který je v skrytého **.vs** podsložky. Tento soubor je místní pro vaše vývojové prostředí. Můžete jej přesunout do kořenové složce projektu Pokud chcete zkontrolovat a uložte si ho se svým týmem. V tomto souboru se přidala pro AppBasicExampleGui konfigurace. Tato výchozí nastavení fungovat ve většině případů, ale protože to je desktopová aplikace, budete muset zadat další informace ke spuštění programu tak je najdete na naší počítač s Linuxem. 
2. Je potřeba vědět hodnotu proměnné prostředí `DISPLAY` na počítač s Linuxem, spusťte tento příkaz se dá stáhnout.

    ```cmd
    echo $DISPLAY
    ```

    V konfiguraci AppBasicExampleGui je pole parametrů "pipeArgs". V rámci něj je řádek "${debuggerCommand}". Toto je příkaz, který spustí gdb na vzdáleném počítači. Visual Studio je potřeba exportovat zobrazení v tomto kontextu, před spuštěním tohoto příkazu. Například pokud hodnota zobrazení: 1, změňte tento řádek následujícím způsobem:

    ```cmd
    "export DISPLAY=:1;${debuggerCommand}",
    ```
3. Teď Pokud chcete spustit a ladit aplikaci, zvolte **vybrat položku při spuštění** rozevíracího seznamu na panelu nástrojů a zvolte AppBasicExampleGui. Nyní stiskněte tlačítko nebo stiskněte tlačítko **F5**. Tím se aplikace sestaví a závislých na vzdáleném počítači s Linuxem pak spustit v ladicím programu sady Visual Studio připojené. Na vzdáleném počítači Linux měli byste vidět okna aplikace se zobrazí.

4. Najeďte myší do okna aplikace klikněte na tlačítko a bude dosaženo zarážkou. Pozastaví spuštění programu, Visual Studio se vrátí zpět na popředí a bude na vaší zarážce. Také byste měli vidět okno konzoly systému Linux se zobrazí v sadě Visual Studio. Toto okno poskytuje výstup ze vzdáleného počítače s Linuxem a můžete také přijmout vstup pro `stdin`. Stejně jako jakékoli okno Visual Studio ho lze ukotvit Pokud budete chtít podívat, jak to a jeho pozice se nastavit jako trvalý v budoucích relacích.

    ![Konzola Linuxu okně aplikace Visual Studio](media/cmake-bullet3-linux-console.png)

5. Procházejte kód interaktivně pomocí sady Visual Studio si můžete prohlédnout aplikace proměnné, objekty, vlákna, paměti a kroku. Ale tentokrát děláte to vše na vzdáleném počítači s Linuxem namísto vašeho místního prostředí Windows. Můžete kliknout na **pokračovat** které umožní aplikaci pokračovat a za normálních okolností ukončí nebo stisknete tlačítko stop, stejně jako u místního spuštění.

6. Podívejte se na okno zásobníku volání a zobrazit volání `x11OpenGLWindow` od sady Visual Studio spustí aplikaci v Linuxu.

    ![Zobrazení zásobníku volání Linux okno zásobníku volání](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Co jste se naučili 

V tomto kurzu jste viděli základní klonovaný přímo z Githubu a sestavení, spuštění a ladění na Windows bez možnosti úprav kódu. To přišel kódovou základnu o změny menší konfigurace, byla založená, spuštění a ladění na vzdáleném počítači s Linuxem. 

## <a name="next-steps"></a>Další kroky

Další informace o konfiguraci a ladění projektů CMake v sadě Visual Studio:

> [!div class="nextstepaction"]
> [Projekty CMake v sadě Visual Studio](cmake-projects-in-visual-studio.md)<br/><br/>
> [Konfigurace projektu Linux CMake](../linux/cmake-linux-project.md)<br/><br/>
> [Připojení ke vzdálenému počítači s Linuxem](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Vlastní nastavení sestavení CMake](customize-cmake-settings.md)<br/><br/>
> [Konfigurace ladicích relací CMake](configure-cmake-debugging-sessions.md)<br/><br/>
> [Nasazení, spuštění a ladění projektu Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [Referenční dokumentace ke konfiguraci CMake předdefinované](cmake-predefined-configuration-reference.md)
> 
