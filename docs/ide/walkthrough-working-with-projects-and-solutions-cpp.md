---
title: 'Návod: Práce s projekty a řešeními (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 36c64a74310c72df38021aebd8abb3ee430da3f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375895"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Návod: Práce s projekty a řešeními (C++)

Toto téma shrnuje postup, jak vytvořit projekt jazyka C++ v sadě Visual Studio, přidat kód a poté projekt sestavit a spustit. V tomto návodu používáme jako příklad projektu program, který sleduje, kolik hráčů hraje různé karetní hry.

V sadě Visual Studio je práce organizována v projektech a řešeních. Řešení může mít více než jeden projekt – například DLL a spustitelný soubor, který odkazuje na tuto dll. Další informace naleznete v tématu [Řešení a projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Než začnete

K dokončení tohoto návodu potřebujete Visual Studio 2017 nebo novější. Pokud potřebujete kopii, tady je stručný průvodce: [Instalace podpory jazyka C++ v sadě Visual Studio](../build/vscpp-step-0-installation.md). Pokud jste to ještě neudělali, postupujte podle následujících kroků po instalaci prostřednictvím kurzu "Hello, World", abyste se ujistili, že součásti Jazyka C++ jsou nainstalovány správně a vše funguje.

Pomáhá, pokud rozumíte základy jazyka C++ a víte, co kompilátor, propojovací program a ladicí program se používají. Kurz také předpokládá, že jste obeznámeni s Windows a jak používat nabídky, dialogy,

## <a name="create-a-project"></a>Vytvoření projektu

Chcete-li vytvořit projekt, zvolte nejprve šablonu typu projektu. Pro každý typ projektu Visual Studio nastaví nastavení kompilátoru a – v závislosti na typu – generuje počáteční kód, který můžete později upravit. Následující kroky se liší v závislosti na verzi sady Visual Studio, kterou používáte. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

### <a name="to-create-a-project-in-visual-studio-2019"></a>Vytvoření projektu v Sadě Visual Studio 2019

1. V hlavní nabídce zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno Vytvořit **nový projekt.**

1. V horní části dialogového okna nastavte **jazyk** na **C++**, nastavte **platformu** na **Systém Windows**a **typ projektu** na **Console**.

1. Z filtrovaného seznamu typů projektů zvolte **Konzolová aplikace** a pak zvolte **Další**. Na další stránce zadejte *hru* jako název projektu.

   Můžete přijmout výchozí umístění v rozevíracím seznamu **Umístění,** zadat jiné umístění nebo zvolit tlačítko **Procházet** a procházet do adresáře, do kterého chcete projekt uložit.

   Při vytváření projektu Visual Studio umístí projekt do řešení. Ve výchozím nastavení má řešení stejný název jako projekt. Název můžete změnit v poli **Název řešení,** ale v tomto příkladu zachovat výchozí název.

1. Chcete-li vytvořit projekt, zvolte tlačítko **Vytvořit.**

   Visual Studio vytvoří nové řešení a soubory projektu a otevře editor pro soubor zdrojového kódu Game.cpp, který vygeneroval.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017"></a>Vytvoření projektu v sadě Visual Studio 2017

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte **Možnost Nainstalováno** a vyberte **Visual C++**, pokud ještě není otevřený.

1. V seznamu nainstalovaných šablon v prostředním podokně vyberte **možnost Konzola Windows Aplikace**.

1. Do pole **Název** zadejte název projektu. V tomto příkladu zadejte *hru*.

   Můžete přijmout výchozí umístění v rozevíracím seznamu **Umístění,** zadat jiné umístění nebo zvolit tlačítko **Procházet** a procházet do adresáře, do kterého chcete projekt uložit.

   Při vytváření projektu Visual Studio umístí projekt do řešení. Ve výchozím nastavení má řešení stejný název jako projekt. Název můžete změnit v poli **Název řešení,** ale v tomto příkladu zachovat výchozí název.

1. Pro vytvoření projektu zvolte tlačítko **OK.**

   Visual Studio vytvoří nové řešení a soubory projektu a otevře editor pro soubor zdrojového kódu Game.cpp, který vygeneroval.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-project-in-visual-studio-2015"></a>Vytvoření projektu v sadě Visual Studio 2015

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

1. V levém podokně dialogového okna **Nový projekt** rozbalte **Možnost Nainstalováno** a vyberte **Visual C++**, pokud ještě není otevřený.

1. V seznamu nainstalovaných šablon v prostředním podokně vyberte možnost **Win32 Console Application**.

1. Do pole **Název** zadejte název projektu. V tomto příkladu zadejte *hru*.

   Můžete přijmout výchozí umístění v rozevíracím seznamu **Umístění,** zadat jiné umístění nebo zvolit tlačítko **Procházet** a procházet do adresáře, do kterého chcete projekt uložit.

   Při vytváření projektu Visual Studio umístí projekt do řešení. Ve výchozím nastavení má řešení stejný název jako projekt. Název můžete změnit v poli **Název řešení,** ale v tomto příkladu zachovat výchozí název.

1. Pro vytvoření projektu zvolte tlačítko **OK.**

   Visual Studio vytvoří nové řešení a soubory projektu a otevře editor pro soubor zdrojového kódu Game.cpp, který vygeneroval.

::: moniker-end

## <a name="organize-projects-and-files"></a>Uspořádání projektů a souborů

**Průzkumník řešení** můžete použít k uspořádání a správě projektů, souborů a dalších prostředků v řešení.

Tato část návodu ukazuje, jak přidat třídu do projektu. Když přidáte třídu, Visual Studio přidá odpovídající soubory H a CPP. Výsledky se zobrazí v **Průzkumníku řešení**.

### <a name="to-add-a-class-to-a-project"></a>Přidání třídy do projektu

1. Pokud se okno **Průzkumník řešení** v sadě Visual Studio nezobrazuje, na řádku nabídek zvolte **Zobrazit** > **Průzkumníka řešení**.

1. V **Průzkumníku řešení**vyberte **herní** projekt. Na řádku nabídek zvolte **Project** > **Add Class**.

1. V dialogovém okně **Přidat třídu** zadejte *Cardgame* do pole **Název třídy.** Neupravujte výchozí názvy souborů a nastavení. Zvolte tlačítko **OK.**

   Visual Studio vytvoří nové soubory a přidá je do projektu. Můžete je vidět v okně **Průzkumník řešení.** Soubory Cardgame.h a Cardgame.cpp jsou otevřeny v editoru.

1. Upravte soubor Cardgame.h a proveďte tyto změny:

   - Přidejte dva soukromé datové členy po otevírací závorce definice třídy.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Upravte výchozí konstruktor, který aplikace Visual Studio vygenerovala. Po `public:` specifikátoru přístupu vyhledejte řádek, který vypadá takto:

      `Cardgame();`

      Upravte konstruktor tak, aby `int`přeji jeden parametr typu , pojmenované *přehrávače*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Za výchozí destruktor přidejte včleněnou deklaraci pro členskou `static int` funkci s názvem *GetParticipants,* která nepřijímá žádné parametry a vrací hodnotu. `totalParticipants`

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   Soubor Cardgame.h by se měl po změně podobat níže uvedenému kódu:

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

   Řádek `#pragma once` říká kompilátoru zahrnout soubor záhlaví pouze jednou. Další informace naleznete v tématu [once](../preprocessor/once.md). Informace o dalších klíčových slovech jazyka C++ ve výše uvedeném souboru záhlaví naleznete v [tématu třída](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [static](../cpp/storage-classes-cpp.md)a [public](../cpp/public-cpp.md).

1. Zvolte kartu **Cardgame.cpp** v horní části podokna úprav a otevřete ji pro úpravy.

1. Odstraňte vše v souboru a nahraďte jej kódem:

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
   > Při zadávání kódu lze použít automatické dokončování. Pokud například zadáte tento kód na klávesnici, můžete zadat *pl* nebo *tot* a pak stisknout **klávesu Ctrl**+**Mezerník**. Automatické dokončování vstoupí `players` nebo `totalParticipants` pro vás.

## <a name="add-test-code-to-your-main-function"></a>Přidání testovacího kódu do hlavní funkce

Přidejte do aplikace nějaký kód, který testuje nové funkce.

### <a name="to-add-test-code-to-the-project"></a>Přidání testovacího kódu do projektu

1. V okně editoru **Game.cpp** nahraďte existující kód:

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

   Kód přidá testovací funkci `PlayGames`, do zdrojového kódu `main`a zavolá ji v aplikaci .

## <a name="build-and-run-your-app-project"></a>Sestavení a spuštění projektu aplikace

Dále vytvořte projekt a spusťte aplikaci.

### <a name="to-build-and-run-the-project"></a>Sestavení a spuštění projektu

1. Na řádku nabídek zvolte **Build** > **Build Build Solution**.

   Výstup ze sestavení se zobrazí v okně **Výstup.** Pokud je sestavení úspěšné, výstup by se měl podobat:

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   **Okno Výstup** může zobrazit různé kroky v závislosti na konfiguraci sestavení, ale pokud sestavení projektu proběhne úspěšně, poslední řádek by se měl podobat zobrazený výstup.

   Pokud vaše sestavení nebylo úspěšné, porovnejte kód s kódem, který je zobrazen v předchozích krocích.

1. Chcete-li projekt spustit, zvolte na řádku nabídek možnost **Ladění** > **startu bez ladění**. Mělo by se zobrazit okno konzoly a výstup by se měl podobat:

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   Stisknutím klávesy zavřete okno konzoly.

Gratulujeme, úspěšně jste vytvořili projekt a řešení aplikace. Pokračujte v návodu, abyste se dozvěděli další informace o tom, jak vytvořit projekty kódu jazyka C++ v sadě Visual Studio.

## <a name="next-steps"></a>Další kroky

**Předchozí:** [Použití ide sady Visual Studio pro vývoj plochy v jazyce C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**Další:** [Návod: Vytvoření projektu (C++)](../ide/walkthrough-building-a-project-cpp.md)

## <a name="see-also"></a>Viz také

[Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>
