---
title: 'Návod: Práce s projekty a řešeními (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: ae2830d58bb992a4ff065aa0e53085a490eb90d7
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400954"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Návod: Práce s projekty a řešeními (C++)

Toto téma shrnuje postup, jak vytvořit projekt jazyka C++ v sadě Visual Studio, přidat kód a poté projekt sestavit a spustit. V tomto návodu používáme jako příklad projektu program, který sleduje, kolik hráčů hraje různé karetní hry.

V sadě Visual Studio je práce organizována do projektů a řešení. Řešení může obsahovat více než jeden projekt, například knihovny DLL i spustitelný soubor, který odkazuje na tuto knihovnu DLL. Další informace najdete v tématu [řešení a projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Než začnete

K dokončení tohoto návodu, třeba Visual Studio 2017 nebo novější. Pokud potřebujete kopii, zde je krátké průvodce: [Instalace podpory jazyka C++ v sadě Visual Studio](../build/vscpp-step-0-installation.md). Pokud jste to ještě neudělali, postupujte podle dalších kroků po instalaci prostřednictvím kurzu "Hello, World" a ujistěte se, C++ součásti jsou správně nainstalované, a to všechno funguje.

To pomáhá porozumět základům jazyka C++ a vědět, co kompilátoru, linkeru a ladicí program se používají pro. Kurz předpokládá také, že jste obeznámeni s Windows a použití nabídek, dialogová okna,

## <a name="create-a-project"></a>Vytvoření projektu

Chcete-li vytvořit projekt, zvolte nejprve šablonu typu projektu. Pro každý typ projektu aplikace Visual Studio nastaví nastavení kompilátoru a – podle toho, jaké – vygeneruje počáteční kód, který můžete později změnit. Následující postup se liší v závislosti na tom, kterou verzi sady Visual Studio, kterou používáte. Ujistěte se, že volič verze v levé horní části této stránky je nastaven na správnou verzi.

::: moniker range="vs-2019"

### <a name="to-create-a-project-in-visual-studio-2019"></a>Vytvoření projektu v aplikaci Visual Studio 2019

1. V hlavní nabídce zvolte **souboru** > **nový** > **projektu** otevřít **vytvořte nový projekt** dialogového okna pole.

1. V horní části dialogového okna, nastavte **jazyk** k **C++** , nastavte **platformy** k **Windows**a nastavte **typprojektu** k **konzoly**. 

1. Filtrované seznamu typů projektů zvolte **konzolovou aplikaci** klikněte na tlačítko **Další**. Na další stránce zadejte *hru* jako název projektu.

   Můžete přijmout výchozí umístění v **umístění** rozevíracího seznamu zadat jiné umístění nebo zvolte **Procházet** tlačítko vyhledat adresář, kam chcete projekt uložit.

   Při vytváření projektu sady Visual Studio vloží projektu v řešení. Ve výchozím nastavení má řešení stejný název jako projekt. Můžete změnit název v **název řešení** pole, ale v tomto příkladu Ponecháme výchozí název.

1. Zvolte **vytvořit** tlačítko pro vytvoření projektu.

   Visual Studio vytvoří nová řešení a soubory projektu a otevře se editor pro Game.cpp souboru se zdrojovým kódem, který je generován.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017"></a>Vytvoření projektu v sadě Visual Studio 2017

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**.

1. V levém podokně **nový projekt** dialogového okna rozbalte **nainstalováno** a vyberte **Visual C++** , pokud není již otevřen.

1. V seznamu nainstalovaných šablon v prostředním podokně vyberte **Konzolová aplikace Windows**.

1. Zadejte název projektu v **název** pole. V tomto příkladu zadejte *hru*.

   Můžete přijmout výchozí umístění v **umístění** rozevíracího seznamu zadat jiné umístění nebo zvolte **Procházet** tlačítko vyhledat adresář, kam chcete projekt uložit.

   Při vytváření projektu sady Visual Studio vloží projektu v řešení. Ve výchozím nastavení má řešení stejný název jako projekt. Můžete změnit název v **název řešení** pole, ale v tomto příkladu Ponecháme výchozí název.

1. Zvolte **OK** tlačítko pro vytvoření projektu.

   Visual Studio vytvoří nová řešení a soubory projektu a otevře se editor pro Game.cpp souboru se zdrojovým kódem, který je generován.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-project-in-visual-studio-2015"></a>Vytvoření projektu v sadě Visual Studio 2015

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**.

1. V levém podokně **nový projekt** dialogového okna rozbalte **nainstalováno** a vyberte **Visual C++** , pokud není již otevřen.

1. V seznamu nainstalovaných šablon v prostředním podokně vyberte **Konzolová aplikace Win32**.

1. Zadejte název projektu v **název** pole. V tomto příkladu zadejte *hru*.

   Můžete přijmout výchozí umístění v **umístění** rozevíracího seznamu zadat jiné umístění nebo zvolte **Procházet** tlačítko vyhledat adresář, kam chcete projekt uložit.

   Při vytváření projektu sady Visual Studio vloží projektu v řešení. Ve výchozím nastavení má řešení stejný název jako projekt. Můžete změnit název v **název řešení** pole, ale v tomto příkladu Ponecháme výchozí název.

1. Zvolte **OK** tlačítko pro vytvoření projektu.

   Visual Studio vytvoří nová řešení a soubory projektu a otevře se editor pro Game.cpp souboru se zdrojovým kódem, který je generován.

::: moniker-end

## <a name="organize-projects-and-files"></a>Uspořádání projektů a souborů

Můžete použít **Průzkumníka řešení** k uspořádání a správě projektů, souborů a dalších prostředků ve vašem řešení.

Tato část návodu ukazuje, jak přidat třídu do projektu. Při přidání třídy přidá aplikace Visual Studio odpovídající soubory .h a .cpp. Zobrazí se výsledky v **Průzkumníka řešení**.

### <a name="to-add-a-class-to-a-project"></a>Přidání třídy do projektu

1. Pokud **Průzkumníka řešení** okno se nezobrazí v sadě Visual Studio na řádku nabídek, zvolte **zobrazení** > **Průzkumníka řešení**.

1. V **Průzkumníka řešení**, vyberte **hru** projektu. V panelu nabídky zvolte **projektu** > **přidat třídu**.

1. V **přidat třídu** dialogové okno, zadejte *Cardgame* v **název třídy** pole. Neupravujte výchozí názvy souborů a nastavení. Zvolte **OK** tlačítko.

   Visual Studio vytvoří nové soubory a přidá je do projektu. Zobrazí se jim v **Průzkumníka řešení** okna. V editoru jsou otevřeny Cardgame.h a Cardgame.cpp soubory.

1. Upravte soubor Cardgame.h a tyto změny:

   - Přidejte dva soukromé datové členy po otevírací závorce definice třídy.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Upravte výchozí konstruktor, který aplikace Visual Studio vygenerovala. Po `public:` specifikátor přístupu, najděte řádek, který bude vypadat takto:

      `Cardgame();`

      Upravte konstruktor pro přijímat jeden parametr typu `int`s názvem *hráči*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Za výchozí destruktor přidejte vloženou deklaraci `static int` členskou funkci s názvem *GetParticipants* , která nepřijímá žádné parametry a vrátí `totalParticipants` hodnotu.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   Soubor Cardgame.h měl vypadat kód uvedený níže, po změnách by:

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

   Na řádku `#pragma once` instruuje kompilátor, aby zahrnutím souboru hlaviček jen jednou. Další informace najdete v tématu [po](../preprocessor/once.md). Informace o dalších klíčových slovech C++ z výše uvedené hlavičky souboru najdete v tématu [třídy](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [statické](../cpp/storage-classes-cpp.md), a [veřejné](../cpp/public-cpp.md).

1. Zvolte **Cardgame.cpp** kartě v horní části editovacím podokně otevřete pro úpravy.

1. Odstraňte všechny položky v souboru a nahraďte kód:

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
   > Při zadávání kódu lze použít automatické dokončování. Například pokud zadáte tento kód na klávesnici, můžete zadat *pl* nebo *tot* a potom stiskněte klávesu **Ctrl**+**MEZERNÍK**. Automatické dokončování zadá `players` nebo `totalParticipants` za vás.

## <a name="add-test-code-to-your-main-function"></a>Přidat testovací kód do hlavní funkce

Přidání kódu do vaší aplikace, který kontroluje nových funkcí.

### <a name="to-add-test-code-to-the-project"></a>Chcete-li přidat testovací kód do projektu

1. V **Game.cpp** okno editoru nahraďte existující kód:

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

   Kód přidá testovací funkci, `PlayGames`, zdrojový kód a volání v `main`.

## <a name="build-and-run-your-app-project"></a>Sestavení a spuštění projektu aplikace

V dalším kroku se projekt sestavil a spuštění aplikace.

### <a name="to-build-and-run-the-project"></a>Sestavení a spuštění projektu

1. V panelu nabídky zvolte **sestavení** > **sestavit řešení**.

   Výstup sestavení se zobrazí v **výstup** okna. Pokud bylo sestavení úspěšné, výstup by měl vypadat:

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   **Výstup** okno může zobrazovat odlišné kroky, v závislosti na konfiguraci sestavení, ale pokud byl projekt sestaven úspěšně, poslední řádek odpovídá uvedenému výstupu.

   Pokud sestavení nebylo úspěšné, porovnejte svůj kód do kódu, který se zobrazí v předchozích krocích.

1. Chcete-li spustit projekt, na panelu nabídek, zvolte **ladění** > **spustit bez ladění**. By měl zobrazit okno konzoly a výstup by měl vypadat:

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   Stisknutím jakékoli klávesy zavřete okno konzoly.

Blahopřejeme, úspěšně jste vytvořili řešení a projekt aplikace. Další informace o tom, jak vytvářet projekty kódu C++ v sadě Visual Studio dál návodu.

## <a name="next-steps"></a>Další kroky

**Předchozí:** [Použití prostředí IDE sady Visual Studio pro vývoj aplikací klasické pracovní plochy v jazyce C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**Další:** [Návod: Sestavení projektu (C++)](../ide/walkthrough-building-a-project-cpp.md)

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](../build/projects-and-build-systems-cpp.md)<br/>
