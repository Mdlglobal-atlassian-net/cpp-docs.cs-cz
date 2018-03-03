---
title: "Návod: Práce s projekty a řešeními (C++) | Microsoft Docs"
ms.custom: 
ms.date: 12/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a20c0ee933d49465a841b638a8260181d7175ac5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Návod: Práce s projekty a řešeními (C++)

Toto téma shrnuje postup, jak vytvořit projekt jazyka C++ v sadě Visual Studio, přidat kód a poté projekt sestavit a spustit. V tomto návodu používáme jako příklad projektu program, který sleduje, kolik hráčů hraje různé karetní hry.

V sadě Visual Studio je pracovní uspořádány do projektů a řešení. Řešení může obsahovat více než jeden projekt, například knihovnu DLL a spustitelný soubor, který na tuto knihovnu DLL odkazuje. Další informace najdete v tématu [řešení a projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Než začnete

Pro dokončení tohoto návodu, musíte Visual Studio 2017 verze 15.3 nebo novější. Pokud budete potřebovat kopii, zde je krátký průvodce: [podpory nainstalovat C++ v sadě Visual Studio](../build/vscpp-step-0-installation.md). Pokud jste ho ještě neudělali, postupujte podle další kroky po instalaci prostřednictvím kurzu "Hello, World", abyste měli jistotu, že je správně nainstalováno Visual C++ a všechny funguje.

Pomáhá pochopit základy jazyka C++ a vědět, co kompilátoru, linkeru a ladicí program se používají pro. Kurz také předpokládá, že jste obeznámeni s Windows a jak používat nabídky, dialogová okna,

## <a name="create-a-project"></a>Vytvoření projektu

Chcete-li vytvořit projekt, zvolte nejprve šablonu typu projektu. Pro každý typ projektu sady Visual Studio nastaví nastavení kompilátoru a – v závislosti na typu – generuje počáteční kód, který můžete později upravit.

### <a name="to-create-a-project"></a>Vytvoření projektu

1. Na řádku nabídek zvolte **soubor > Nový > projekt**.

1. V levém podokně **nový projekt** dialogové okno, rozbalte seznam **nainstalovaná** a vyberte **Visual C++**, pokud není již otevřený.

1. V seznamu nainstalovaných šablon v prostředním podokně, vyberte **konzolové aplikace pro Windows**.

1. Zadejte název projektu v **název** pole. V tomto příkladu zadejte **herní**.

   Můžete přijmout výchozí umístění v **umístění** rozevíracího seznamu, zadejte jiné umístění, nebo zvolte **Procházet** tlačítko, přejděte do adresáře, kam chcete uložit projektu.

   Když vytvoříte projekt, Visual Studio uloží projekt v řešení. Ve výchozím nastavení má řešení stejný název jako projekt. Můžete změnit název v **název řešení** pole, ale v tomto příkladu ponechat výchozí název.

1. Vyberte **OK** tlačítko pro vytvoření projektu.

   Visual Studio vytvoří nové řešení a soubory projektu a otevře se editor pro Game.cpp souboru se zdrojovým kódem, který vygeneroval.

## <a name="organize-projects-and-files"></a>Uspořádání projekty a soubory

Můžete použít **Průzkumníku řešení** k uspořádání a správě projektů, soubory a další prostředky ve vašem řešení.

Tato část návodu ukazuje, jak do projektu přidat třídu. Když přidáte třídu, Visual Studio přidá odpovídající .h a sada souborů. Zobrazí výsledky v **Průzkumníku řešení**.

### <a name="to-add-a-class-to-a-project"></a>Přidání třídy do projektu

1. Pokud **Průzkumníku řešení** okno se nezobrazí v sadě Visual Studio na řádku nabídek, zvolte **zobrazení > Průzkumníku řešení**.

1. V **Průzkumníku řešení**, vyberte **herní** projektu. Na řádku nabídek zvolte **Projekt > Přidat třídu**.

1. V **přidat třídu** dialogové okno, zadejte *Cardgame* v **název třídy** pole. Neupravujte výchozí názvy souborů a nastavení. Vyberte **OK** tlačítko.

   Visual Studio vytvoří nové soubory a přidá je do projektu. Zobrazí se jim v **Průzkumníku řešení** okno. Otevření souborů Cardgame.h a Cardgame.cpp v editoru.

1. Upravte soubor Cardgame.h a proveďte tyto změny:

   - Přidejte dva soukromé datové členy po otevírací závorce definice třídy.
      <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Upravte výchozí konstruktor, který aplikace Visual Studio vygenerovala. Po `public:` přístup specifikátor, najít řádek, který vypadá takto:

      `Cardgame();`

      Upravit tento konstruktor provést jeden parametr typu `int`s názvem *přehrávače*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Za výchozí destruktor, přidejte také vložené prohlášení o `static int` – členská funkce s názvem *GetParticipants* které nepřijímá žádné parametry a vrátí `totalParticipants` hodnotu.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   Po změnách by soubor Cardgame.h měl vypadat takto:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->
   ```cpp
   #pragma once
   class Cardgame
   {
       int players;
       static int totalParticipants;
   public:
       Cardgame(int players);
       ~Cardgame(void);
       static int GetParticipants() { return totalParticipants; }
   };
   ```

   Na řádku `#pragma once` určuje kompilátor zahrnout soubor hlaviček pouze jednou. Další informace najdete v tématu [po](../preprocessor/once.md). Informace o dalších klíčová slova jazyka C++ v tomto souboru záhlaví najdete v tématu [třída](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [statické](../cpp/storage-classes-cpp.md), a [veřejné](../cpp/public-cpp.md).

1. Vyberte **Cardgame.cpp** v horní části podokna úprav otevřete pro úpravy.

1. Odstraňte všechny položky v souboru a nahraďte je tímto kódem:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->
   ```cpp
   #include "stdafx.h"
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
   > Při zadávání kódu lze použít automatické dokončování. Například pokud zadáte tento kód na klávesnici, můžete zadat *pl* nebo *tot* a potom stiskněte klávesu Ctrl + mezerník. Automatické dokončování zadá `players` nebo `totalParticipants` za vás.

## <a name="add-test-code-to-your-main-function"></a>Přidání testovacího kódu do vaší main – funkce

Přidejte nějaký kód do aplikace, který kontroluje nové funkce.

### <a name="to-add-test-code-to-the-project"></a>Chcete-li přidat testovací kód do projektu

1. V okně editoru Game.cpp nahraďte existující kód toto:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->
   ```cpp
   // Game.cpp : Defines the entry point for the console application.
   //

   #include "stdafx.h"
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
Tento kód přidá funkci test, `PlayGames`, zdrojový kód a volání v `main`. 

## <a name="build-and-run-your-app-project"></a>Sestavení a spuštění projektu aplikace

V dalším kroku se projekt sestavil a spuštění aplikace.

### <a name="to-build-and-run-the-project"></a>Sestavení a spuštění projektu

1. Na řádku nabídek zvolte **sestavení > Sestavit řešení**.

   Zobrazí se výstup ze sestavení v **výstup** okno. Pokud bylo sestavení úspěšné, výstup by měl vypadat následovně:

   ```Output
   1>------ Build started: Project: Game, Configuration: Debug Win32 ------
   1>  stdafx.cpp
   1>  Game.cpp
   1>  Cardgame.cpp
   1>  Generating Code...
   1>  Game.vcxproj -> C:\Users\username\Source\Repos\Game\Debug\Game.exe
   ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
   ```

   **Výstup** v okně se zobrazí různé kroky, v závislosti na konfiguraci sestavení, ale pokud sestavení projektu úspěšné, by měla vypadat přibližně poslední řádek výstupu zobrazí.

   Pokud vaše sestavení nebylo úspěšné, porovnejte svůj kód do kódu, které se zobrazí v dřívějších krocích.

1. Chcete-li spustit projekt v řádku nabídek, zvolte **ladění > Spustit bez ladění**. Okno konzoly by se měla objevit a výstup by měl vypadat takto:

   ```Output
   4 players have started a new game.  There are now 4 players in total.
   8 players have started a new game.  There are now 12 players in total.
   1 players have started a new game.  There are now 13 players in total.
   5 players have started a new game.  There are now 18 players in total.
   ```
Stiskněte klávesu pro zavření v okně konzoly.

Blahopřejeme, úspěšně jste vytvořili projekt aplikace a řešení. Další informace o tom, jak vytvářet projekty kódu C++ v sadě Visual Studio dál návodu.

## <a name="next-steps"></a>Další kroky

**Předchozí:** [pomocí sady Visual Studio IDE pro vývoj C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
**Další krok:** [návod: sestavení projektu (C++)](../ide/walkthrough-building-a-project-cpp.md).

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)  
[Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)