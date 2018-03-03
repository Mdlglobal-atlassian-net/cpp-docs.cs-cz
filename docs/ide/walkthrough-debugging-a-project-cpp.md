---
title: "Návod: Ladění projektu (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c9789a7deafacf09ad615f416a446da4eba8150
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-debugging-a-project-c"></a>Návod: Ladění projektu (C++)
V tomto návodu změníte program pro vyřešení problému, který jste zjistili při testování projektu.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Tento návod předpokládá, že rozumíte základy jazyka C++.  
  
-   Také předpokládá, že jste dokončili dříve související návodů, které jsou uvedeny v [pomocí prostředí Visual Studio IDE pro vývoje v jazyce C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-fix-a-program-that-has-a-bug"></a>Oprava programu, který obsahuje chybu  
  
1.  Chcete-li zjistit, co se stane, když je objekt `Cardgame` zničen, zobrazte destruktor třídy `Cardgame`.  
  
     Na řádku nabídek zvolte **zobrazení**, **zobrazení tříd**.  
  
     V **zobrazení tříd** okno, rozbalte **herní** strom projektu a vyberte **Cardgame** třídy, které chcete zobrazit členy třídy a metody.  
  
     Otevřete místní nabídku pro **~Cardgame(void)** destruktor a potom zvolte **přejít k definici**.  
  
2.  Pro snížení proměnné `totalParticipants` při ukončení aplikace Cardgame přidejte následující kód mezi otevírací a uzavírací závorky destruktoru `Cardgame::~Cardgame`:  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]  
  
3.  Soubor Cardgame.cpp by měl by vypadat takto:  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]  
  
4.  Na řádku nabídek zvolte **sestavení**, **sestavit řešení**.  
  
5.  Po dokončení sestavení spustit v režimu ladění výběrem **ladění**, **spustit ladění** v řádku nabídek nebo výběrem klávesy F5. Program se pozastaví u první zarážky.  
  
6.  Krok prostřednictvím programu na řádku nabídek zvolte **ladění**, **Krokovat s přeskočením**, nebo zvolte F10 klíč.  
  
     Po každém provedení konstruktoru třídy Cardgame se hodnota proměnné `totalParticipants` zvýší. Když se funkce `PlayGames` dokončí, a jelikož se každá instance třídy Cardgame dostane mimo rozsah a je odstraněna (a je zavolán destruktor), proměnná `totalParticipants` se sníží. Těsně před `return` je spustit příkaz, `totalParticipants` rovná 0.  
  
7.  Krokování programu, dokud bude pokračovat, nebo ji spustit výběrem nechat **ladění**, **spustit** v řádku nabídek nebo výběrem klávesy F5.  
  
## <a name="next-steps"></a>Další kroky  
 **Předchozí:** [návod: testování projektu (C++)](../ide/walkthrough-testing-a-project-cpp.md) &#124; **Další:**[návod: nasazení programu (C++)](../ide/walkthrough-deploying-your-program-cpp.md)  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)