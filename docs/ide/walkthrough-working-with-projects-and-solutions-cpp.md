---
title: 'Průvodce: Práce s projekty a řešenímiC++()'
ms.date: 05/14/2019
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 6d9ee71e2608c2ed4935e7a5a3c54af45921e5d2
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108399"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Průvodce: Práce s projekty a řešenímiC++()

Toto téma shrnuje postup, jak vytvořit projekt jazyka C++ v sadě Visual Studio, přidat kód a poté projekt sestavit a spustit. V tomto návodu používáme jako příklad projektu program, který sleduje, kolik hráčů hraje různé karetní hry.

V aplikaci Visual Studio je práce organizována v projektech a řešeních. Řešení může mít více než jeden projekt, například knihovnu DLL a spustitelný soubor, který odkazuje na tuto knihovnu DLL. Další informace najdete v tématu [řešení a projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Než začnete

K dokončení tohoto návodu budete potřebovat Visual Studio 2017 nebo novější. Pokud potřebujete kopii, tady je Stručná příručka: [Nainstalujte C++ podporu v aplikaci Visual Studio](../build/vscpp-step-0-installation.md). Pokud jste to ještě neudělali, postupujte po instalaci prostřednictvím kurzu "Hello, World", abyste se ujistili, C++ že jsou komponenty správně nainstalované a vše funguje.

Pomáhá porozumět základům C++ jazyka a znát, k čemu se kompilátor, linker a ladicí program používají. Tento kurz také předpokládá, že jste obeznámeni se systémem Windows a jak používat nabídky, dialogy,

## <a name="create-a-project"></a>Vytvoření projektu

Chcete-li vytvořit projekt, zvolte nejprve šablonu typu projektu. Pro každý typ projektu sada Visual Studio nastaví nastavení kompilátoru a – v závislosti na typu – vygeneruje počáteční kód, který můžete později změnit. Následující postup se liší v závislosti na verzi sady Visual Studio, kterou používáte. Ujistěte se, že selektor verzí v levém horním rohu této stránky je nastavený na správnou verzi.

::: moniker range="vs-2019"

### <a name="to-create-a-project-in-visual-studio-2019"></a>Vytvoření projektu v aplikaci Visual Studio 2019

1. V hlavní nabídce vyberte **soubor** > **Nový** > **projekt** a otevřete tak dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Console**.

1. Z filtrovaného seznamu typů projektů zvolte Konzolová **aplikace** a pak zvolte **Další**. Na další stránce zadejte jako název projektu *hru* .

   Výchozí umístění můžete přijmout v rozevíracím seznamu **umístění** , zadejte jiné umístění nebo klikněte na tlačítko **Procházet** a přejděte do adresáře, kam chcete projekt uložit.

   Když vytvoříte projekt, Visual Studio vloží projekt do řešení. Ve výchozím nastavení má řešení stejný název jako projekt. Název můžete změnit v poli **název řešení** , ale v tomto příkladu ponecháme výchozí název.

1. Kliknutím na tlačítko **vytvořit** vytvořte projekt.

   Visual Studio vytvoří nové soubory řešení a projektu a otevře Editor pro soubor zdrojového kódu Game. cpp, který vygeneroval.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017"></a>Vytvoření projektu v aplikaci Visual Studio 2017

1. Na panelu nabídek vyberte **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte položku **nainstalované** a vyberte možnost **vizuál C++** , pokud již není otevřená.

1. V seznamu nainstalovaných šablon v prostředním podokně vyberte **Konzolová aplikace systému Windows**.

1. Do pole **název** zadejte název projektu. V tomto příkladu zadejte *Game*.

   Výchozí umístění můžete přijmout v rozevíracím seznamu **umístění** , zadejte jiné umístění nebo klikněte na tlačítko **Procházet** a přejděte do adresáře, kam chcete projekt uložit.

   Když vytvoříte projekt, Visual Studio vloží projekt do řešení. Ve výchozím nastavení má řešení stejný název jako projekt. Název můžete změnit v poli **název řešení** , ale v tomto příkladu ponecháme výchozí název.

1. Kliknutím na tlačítko **OK** vytvořte projekt.

   Visual Studio vytvoří nové soubory řešení a projektu a otevře Editor pro soubor zdrojového kódu Game. cpp, který vygeneroval.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-project-in-visual-studio-2015"></a>Vytvoření projektu v aplikaci Visual Studio 2015

1. Na panelu nabídek vyberte **soubor** > **Nový** > **projekt**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte položku **nainstalované** a vyberte možnost **vizuál C++** , pokud již není otevřená.

1. V seznamu nainstalovaných šablon v prostředním podokně vyberte **Konzolová aplikace Win32**.

1. Do pole **název** zadejte název projektu. V tomto příkladu zadejte *Game*.

   Výchozí umístění můžete přijmout v rozevíracím seznamu **umístění** , zadejte jiné umístění nebo klikněte na tlačítko **Procházet** a přejděte do adresáře, kam chcete projekt uložit.

   Když vytvoříte projekt, Visual Studio vloží projekt do řešení. Ve výchozím nastavení má řešení stejný název jako projekt. Název můžete změnit v poli **název řešení** , ale v tomto příkladu ponecháme výchozí název.

1. Kliknutím na tlačítko **OK** vytvořte projekt.

   Visual Studio vytvoří nové soubory řešení a projektu a otevře Editor pro soubor zdrojového kódu Game. cpp, který vygeneroval.

::: moniker-end

## <a name="organize-projects-and-files"></a>Uspořádání projektů a souborů

**Průzkumník řešení** můžete použít k organizování a správě projektů, souborů a dalších prostředků ve vašem řešení.

Tato část návodu ukazuje, jak přidat třídu do projektu. Když přidáte třídu, Visual Studio přidá odpovídající soubory. h a. cpp. Výsledky můžete zobrazit v **Průzkumník řešení**.

### <a name="to-add-a-class-to-a-project"></a>Přidání třídy do projektu

1. Pokud se okno **Průzkumník řešení** v aplikaci Visual Studio nezobrazí, v řádku nabídek vyberte možnost **Zobrazit** > **Průzkumník řešení**.

1. V **Průzkumník řešení**vyberte projekt **hry** . Na panelu nabídek vyberte **projekt** > **Přidat třídu**.

1. V dialogovém okně **Přidat třídu** zadejte do pole **název třídy** *Cardgame* . Neupravujte výchozí názvy souborů a nastavení. Zvolte **OK** tlačítko.

   Visual Studio vytvoří nové soubory a přidá je do projektu. Můžete je zobrazit v okně **Průzkumník řešení** . Soubory Cardgame. h a Cardgame. cpp jsou otevřeny v editoru.

1. Upravte soubor Cardgame. h a proveďte tyto změny:

   - Přidejte dva soukromé datové členy po otevírací závorce definice třídy.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Upravte výchozí konstruktor, který aplikace Visual Studio vygenerovala. Po specifikátoru `public:` přístupu Najděte řádek, který vypadá takto:

      `Cardgame();`

      Upravte konstruktor tak, aby převzal jeden parametr `int`typu snázvem Players.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Po výchozím destruktoru přidejte vloženou deklaraci `static int` členské funkce s názvem getúčastníci, která nepřijímá žádné `totalParticipants` parametry a vrací hodnotu.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   Soubor Cardgame. h by měl po změně vypadat podobně jako v následujícím příkladu:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->

    ```cpp
    #pragma once
    class Cardgame
    {
        int players;
        static int totalParticipants;
    public:
        Cardgame(int players);
        ~Cardgame();
        static int GetParticipants() { return totalParticipants; }
    };
    ```

   Řádek `#pragma once` instruuje kompilátor, aby soubor hlaviček zahrnul pouze jednou. Další informace najdete v tématu [jednou](../preprocessor/once.md). Informace C++ o dalších klíčových slovech v hlavičkovém souboru výše naleznete v tématu [Class](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [static](../cpp/storage-classes-cpp.md)a [Public](../cpp/public-cpp.md).

1. Vyberte kartu **Cardgame. cpp** v horní části podokna úprav a otevřete ji pro úpravy.

1. Odstraňte všechny položky v souboru a nahraďte je kódem:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->

    ```cpp
    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    int Cardgame::totalParticipants = 0;

    Cardgame::Cardgame(int players)
        : players(players)
    {
        totalParticipants += players;
        cout << players << " players have started a new game.  There are now "
             << totalParticipants << " players in total." << endl;
    }

    Cardgame::~Cardgame()
    {
    }
    ```

   > [!NOTE]
   > Při zadávání kódu lze použít automatické dokončování. Pokud například zadáte tento kód na klávesnici, můžete zadat *pl* nebo *celkem* a pak stisknout klávesovou zkratku **CTRL**+**MEZERNÍK**. Automatické doplňování se `players` zadá `totalParticipants` nebo za vás.

## <a name="add-test-code-to-your-main-function"></a>Přidání testovacího kódu do funkce main

Přidejte do aplikace nějaký kód, který testuje nové funkce.

### <a name="to-add-test-code-to-the-project"></a>Přidání testovacího kódu do projektu

1. V okně editoru **hry. cpp** nahraďte existující kód:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->

    ```cpp
    // Game.cpp : Defines the entry point for the console application.
    //

    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    void PlayGames()
    {
        Cardgame bridge(4);
        Cardgame blackjack(8);
        Cardgame solitaire(1);
        Cardgame poker(5);
    }

    int main()
    {
        PlayGames();
        return 0;
    }
    ```

   Kód přidá funkci testu, `PlayGames`ke zdrojovému kódu a zavolá ji v. `main`

## <a name="build-and-run-your-app-project"></a>Sestavení a spuštění projektu aplikace

V dalším kroku Sestavte projekt a spusťte aplikaci.

### <a name="to-build-and-run-the-project"></a>Sestavení a spuštění projektu

1. Na řádku nabídek klikněte na **sestavit** > sestavení**řešení**.

   Výstup sestavení se zobrazí v okně **výstup** . Pokud je sestavení úspěšné, výstup by měl vypadat přibližně takto:

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   Okno **výstup** může v závislosti na konfiguraci sestavení zobrazit různé kroky, ale pokud je sestavení projektu úspěšné, poslední řádek by měl vypadat jako zobrazený výstup.

   Pokud vaše sestavení nebylo úspěšné, porovnejte kód s kódem, který je uveden v předchozích krocích.

1. Chcete-li spustit projekt, na panelu nabídek vyberte možnost **ladit** > **Spustit bez ladění**. Mělo by se zobrazit okno konzoly a výstup by měl vypadat přibližně takto:

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   Stisknutím klávesy zavřete okno konzoly.

Gratulujeme, úspěšně jste vytvořili projekt aplikace a řešení. V tomto návodu se dozvíte víc o tom, C++ jak vytvářet projekty kódu v aplikaci Visual Studio.

## <a name="next-steps"></a>Další postup

**Předchozí** [Použití prostředí IDE sady Visual Studio pro vývoj aplikací klasické pracovní plochy v jazyce C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**Generace** [Návod: Sestavení projektu (C++)](../ide/walkthrough-building-a-project-cpp.md)

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>
