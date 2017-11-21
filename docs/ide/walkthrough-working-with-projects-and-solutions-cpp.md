---
title: "Návod: Práce s projekty a řešeními (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6b30cd4885d5fdd65831c8044a088fcb87b52ae3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Návod: Práce s projekty a řešeními (C++)
Toto téma shrnuje postup, jak vytvořit projekt jazyka C++ v sadě Visual Studio, přidat kód a poté projekt sestavit a spustit. V tomto návodu používáme jako příklad projektu program, který sleduje, kolik hráčů hraje různé karetní hry.  
  
 V sadě Visual Studio je pracovní uspořádány do projektů a řešení. Řešení může obsahovat více než jeden projekt, například knihovnu DLL a spustitelný soubor, který na tuto knihovnu DLL odkazuje. Další informace najdete v tématu [řešení a projekty](/visualstudio/ide/solutions-and-projects-in-visual-studio).  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Předpokladem práce s tímto návodem je znalost základů jazyka C++.  
  
## <a name="creating-a-project"></a>Vytvoření projektu  
 Chcete-li vytvořit projekt, zvolte nejprve šablonu typu projektu. Pro každý typ projektu sady Visual Studio nastaví nastavení kompilátoru a – v závislosti na typu – generuje počáteční kód, který můžete později upravit.  
  
#### <a name="to-create-a-project"></a>Vytvoření projektu  
  
1.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
2.  V levém podokně **nový projekt** dialogové okno, rozbalte seznam **nainstalovaných šablonách** uzlu, rozbalte **Visual C++** uzel a potom vyberte **Win32**.  
  
3.  V seznamu nainstalovaných šablon v prostředním podokně, vyberte **Konzolová aplikace Win32**.  
  
4.  Zadejte název projektu v **název** pole. V tomto příkladu zadejte **herní**.  
  
     Můžete přijmout výchozí umístění v **umístění** rozevíracího seznamu, zadejte jiné umístění, nebo zvolte **Procházet** tlačítko, přejděte do adresáře, kam chcete uložit projektu.  
  
     Když vytvoříte projekt, Visual Studio uloží projekt v řešení. Ve výchozím nastavení má řešení stejný název jako projekt. Můžete změnit název v **název řešení** pole, ale v tomto příkladu ponechat výchozí název.  
  
     Vyberte **OK** tlačítko Spustit **Win32 – Průvodce aplikací**.  
  
5.  Na **přehled** stránky **Win32 – Průvodce aplikací**, vyberte **Další** tlačítko.  
  
6.  Na **nastavení aplikace** v části **typ aplikace**, vyberte **konzolové aplikace**. V části **další možnosti**, zrušte **předkompilované hlavičky** nastavení a pak vyberte **prázdný projekt** nastavení. Vyberte **Dokončit** tlačítko pro vytvoření projektu.  
  
     Nyní máte projekt, ten ale ještě neobsahuje zdrojové soubory.  
  
## <a name="organizing-projects-and-files-in-a-solution"></a>Uspořádání projektů a souborů do řešení  
 Můžete použít **Průzkumníku řešení** k uspořádání a správě projektů, soubory a další prostředky ve vašem řešení.  
  
 Tato část návodu ukazuje, jak do projektu přidat třídu. Když přidáte třídu, Visual Studio přidá odpovídající .h a sada souborů. Poté přidejte do projektu nový zdrojový soubor pro hlavní program, který třídu otestuje.  
  
#### <a name="to-add-a-class-to-a-project"></a>Přidání třídy do projektu  
  
1.  Pokud **Průzkumníku řešení** se nezobrazí, na řádku nabídek zvolte **zobrazení**, **Průzkumníku řešení**.  
  
2.  V **Průzkumníku řešení**, otevřete místní nabídku pro **soubory hlaviček** složku a potom zvolte **přidat**, **třída**.  
  
     V levém podokně **přidat třídu** dialogové okno, rozbalte seznam **Visual C++** uzel a vyberte možnost **C++**a potom v seznamu nainstalovaných šablon v prostředním podokně, vyberte  **Třídy C++**. Vyberte **přidat** tlačítko.  
  
3.  V **obecného Průvodce třídami C++**, zadejte **Cardgame** v **název třídy** pole. Neupravujte výchozí názvy souborů a nastavení. Vyberte **Dokončit** tlačítko.  
  
4.  Soubor Cardgame.h se otevře v editoru. Proveďte následující změny:  
  
    -   Přidejte dva soukromé datové členy po otevírací závorce definice třídy.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)]  
  
    -   Upravte výchozí konstruktor, který aplikace Visual Studio vygenerovala. Po `public:` přístup specifikátor, najít řádek, který vypadá takto:  
  
         `Cardgame(void);`  
  
         Upravit ji tak, aby jeden parametr typu `int`s názvem **přehrávače**.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]  
  
    -   Za výchozí destruktor, přidejte také vložené prohlášení o int statické členské funkce s názvem **GetParticipants** které nepřijímá žádné parametry a vrátí **totalParticipants** hodnotu.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]  
  
5.  Po změnách by soubor Cardgame.h měl vypadat takto:  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]  
  
     Na řádku `#pragma once` říká kompilátoru zahrnout soubor pouze jednou. Další informace najdete v tématu [po](../preprocessor/once.md).  
  
     Informace o dalších klíčová slova jazyka C++ v tomto souboru záhlaví najdete v tématu [třída](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [statické](../cpp/storage-classes-cpp.md), a [veřejné](../cpp/public-cpp.md).  
  
6.  Vyberte **Cardgame.cpp** v podokně úpravy otevřete pro úpravy.  
  
7.  Odstraňte všechny položky v souboru a nahraďte je tímto kódem:  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]  
  
    > [!NOTE]
    >  Při zadávání kódu lze použít automatické dokončování. Například pokud byly zadáte tento kód, můžete zadat **pl** nebo **tot** a potom stiskněte klávesu Ctrl + mezerník, tak, aby automatické dokončování dokončení zadávání `players` nebo `totalParticipants` za vás.  
  
     Informace o `#include`, najdete v části [#include – direktiva (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).  
  
## <a name="adding-a-source-file"></a>Přidání zdrojového souboru  
 Nyní přidáte zdrojový soubor hlavního programu, který testuje třídu.  
  
#### <a name="to-add-a-new-source-file"></a>Přidání nového zdrojového souboru  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro **zdrojové soubory** složku a potom zvolte **přidat**, **novou položku**.  
  
     V **přidat novou položku** dialogové okno, v levém podokně rozbalte **nainstalovaná** uzlu, rozbalte **Visual C++** uzel a potom vyberte **kód**. V prostředním podokně vyberte **soubor C++ ()**.  
  
2.  Zadejte **testgames** v **název** pole a potom vyberte **přidat** tlačítko.  
  
3.  V okně úprav TestGames.cpp zadejte následující kód:  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]  
  
## <a name="building-and-running-a-project"></a>Vytvoření a spuštění projektu  
 Nyní sestavte projekt a spusťte aplikaci.  
  
#### <a name="to-build-and-run-the-project"></a>Sestavení a spuštění projektu  
  
1.  Na řádku nabídek zvolte **sestavení**, **sestavit řešení**.  
  
    > [!NOTE]
    >  Pokud používáte edici Express, která nezobrazí **sestavení** nabídky v řádku nabídek zvolte **nástroje**, **nastavení**, **Expert nastavení**povolit.  
  
     Zobrazí se výstup ze sestavení v **výstup** okno. Pokud bylo sestavení úspěšné, výstup by měl vypadat následovně:  
  
    ```Output  
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------  
    1>  TestGames.cpp  
    1>  Cardgame.cpp  
    1>  Generating Code...  
    1>  Game.vcxproj -> c:\users\username\documents\visual studio\Projects\Game\Debug\Game.exe  
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
  
    ```  
  
     **Výstup** v okně se zobrazí různé kroky, v závislosti na edici a je konfigurace sestavení, ale pokud sestavení projektu úspěšné, by měla vypadat přibližně poslední řádek výstupu zobrazí.  
  
     Pokud sestavení selhalo, porovnejte kód s kódem, který byl uveden v předchozích krocích.  
  
2.  Chcete-li spustit projekt v řádku nabídek, zvolte **ladění**, **spustit bez ladění**. Výstup by měl vypadat takto:  
  
    ```Output  
    4 players have started a new game.  There are now 4 players in total.  
    8 players have started a new game.  There are now 12 players in total.  
    1 players have started a new game.  There are now 13 players in total.  
    5 players have started a new game.  There are now 18 players in total.  
    ```  
  
## <a name="next-steps"></a>Další kroky  
 **Předchozí:** [pomocí sady Visual Studio IDE pro vývoj C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). **Další krok:**[návod: sestavení projektu (C++)](../ide/walkthrough-building-a-project-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Sestavení C/C++ programů](../build/building-c-cpp-programs.md)