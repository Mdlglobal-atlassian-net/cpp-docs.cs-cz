---
title: 'Návod: Testování projektu (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a9455fa9bf3c9f903f5018a1263978913aa35b2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33333561"
---
# <a name="walkthrough-testing-a-project-c"></a>Návod: Testování projektu (C++)
Když spustíte program v režimu ladění, můžete pozastavit program, který chcete zkontrolovat stav proměnné a objekty zarážky.  
  
 V tomto návodu sledovat hodnotu proměnné, jak program se spustí a zjistit, proč je hodnota neodpovídá vašim očekáváním.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Tento návod předpokládá, že rozumíte základy jazyka C++.  
  
-   Také předpokládá, že jste dokončili dříve související návodů, které jsou uvedeny v [pomocí prostředí Visual Studio IDE pro vývoje v jazyce C++ plochy](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-run-a-program-in-debug-mode"></a>Spuštění programu v režimu ladění  
  
1.  Testgames otevřete pro úpravy.  
  
2.  Vyberte tento řádek kódu:  
  
     `Cardgame.solitaire(1);`  
  
3.  Chcete-li nastavit zarážky daného řádku v řádku nabídek zvolte **ladění**, **Přepnout zarážku**, nebo zvolte F9 klíč. Červené kolečko se zobrazí vlevo řádku; Označuje, že je nastavit zarážky. Pokud chcete odebrat bod přerušení, můžete příkaz nabídky nebo F9 klíč znovu.  
  
     Pokud používáte myši, můžete také nastavit nebo odebrat zarážku kliknutím na levém okraji.  
  
4.  Na řádku nabídek zvolte **ladění**, **spustit ladění**, nebo zvolte klávesy F5.  
  
     Když program dosáhne řádku, který má zarážkou, provádění zastaví dočasně, aplikace je v režimu pozastavení. Žlutý šipku nalevo od řádek kódu naznačuje, že je na další řádek má být proveden.  
  
5.  K prozkoumání hodnotu `Cardgame::totalParticipants` proměnnou, přesuňte ukazatel myši `Cardgame` a poté ho přesuňte přes rozšíření řízení na levé straně okna popisku. Název proměnné `totalParticipants` a jeho hodnota 12 jsou zobrazeny.  
  
     Otevřete místní nabídku pro `Cardgame::totalParticipants` proměnné a pak zvolte **Přidat kukátko** zobrazíte tuto proměnnou v **kukátko 1** okno. Můžete také vybrat proměnnou a přetáhněte ji do **kukátko 1** okno.  
  
6.  Chcete-li krok na další řádek kódu na řádku nabídek zvolte **ladění**, **Krokovat s přeskočením**, nebo zvolte F10 klíč.  
  
     Hodnota `Cardgame::totalParticipants` v **kukátko 1** okno se nyní zobrazí jako 13.  
  
7.  Otevřete místní nabídku pro `return 0;` příkaz a potom zvolte **spustit ke kurzoru**. Žlutý šipku nalevo od kód odkazuje na další příkaz má být proveden.  
  
8.  `Cardgame::totalParticipants` Číslo by měl snížit při Cardgame ukončí. V tomto okamžiku `Cardgame::totalParticipants` musí rovnat 0, protože byly odstraněny všechny instance Cardgame, ale **kukátko 1** okno znamená, že `Cardgame::totalparticipants` rovná 18. To znamená, že je chyba v kód, který lze zjistit a opravit provedením další návod, [návod: ladění projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md).  
  
9. Chcete-li zastavit programu, v panelu nabídek, zvolte **ladění**, **Zastavte ladění**, nebo zvolte stiskněte kombinaci kláves Shift + F5.  
  
## <a name="next-steps"></a>Další kroky  
 **Předchozí:** [návod: sestavení projektu (C++)](../ide/walkthrough-building-a-project-cpp.md) &#124; **Další:**[návod: ladění projektu (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)