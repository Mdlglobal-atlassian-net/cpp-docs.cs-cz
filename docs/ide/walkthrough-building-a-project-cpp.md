---
title: "Návod: Sestavení projektu (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 713a74cc889721259ca99f1622ef5e9919edf573
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-building-a-project-c"></a>Návod: Sestavení projektu (C++)
V tomto návodu je úmyslně zavést chyby syntaxe jazyka Visual C++ v kódu se dozvíte, jak vypadá chyba kompilace a jeho řešení. Při kompilaci projektu chybová zpráva označuje, co je problém a kde došlo k.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Tento návod předpokládá, že rozumíte základy jazyka C++.  
  
-   Také předpokládá, že jste dokončili dříve související návodů, které jsou uvedeny v [pomocí prostředí Visual Studio IDE pro vývoje v jazyce C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-fix-compilation-errors"></a>Oprava chyb kompilace  
  
1.  V testgames odstraňte středník na posledním řádku tak, aby vypadal takto:  
  
     `return 0`  
  
2.  Na řádku nabídek zvolte **sestavení**, **sestavit řešení**.  
  
3.  Zprávy v **seznam chyb** okno znamená, že v budově projektu došlo k chybě. Popis vypadá přibližně takto:  
  
     `error C2143: syntax error : missing ';' before '}'`  
  
     Chcete-li zobrazit informace o této chybě, zvýrazněte ho v **seznam chyb** okna a potom vyberte klávesy F1.  
  
4.  Přidejte středník zpět do konce řádku, který obsahuje chybu syntaxe:  
  
     `return 0;`  
  
5.  Na řádku nabídek zvolte **sestavení**, **sestavit řešení**.  
  
     Zprávy v **výstup** okno znamená úspěšně zkompilovány projektu.  
  
    ```Output  
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------  
    1>  TestGames.cpp  
    1>  Game.vcxproj -> C:\Users\<username>\Documents\Visual Studio <version>\Projects\Game\Debug\Game.exe  
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
    ```  
  
## <a name="next-steps"></a>Další kroky  
 **Předchozí:** [návod: práce s projekty a řešeními (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) &#124; **Další:**[návod: testování projektu (C++)](../ide/walkthrough-testing-a-project-cpp.md)  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Sestavení C/C++ programů](../build/building-c-cpp-programs.md)